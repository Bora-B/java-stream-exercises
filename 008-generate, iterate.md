> Stream.generate ile rastgele 10 sayı üret ve yazdır. Her sayı 0.0 ile 1.0 arasında olsun
```java
package org.example;

import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        Stream.generate(Math::random)
              .limit(10)
              .forEach(System.out::println);
    }
}
```
> Stream.iterate kullanarak ilk 10 çift sayıyı üret ve yazdır.
```java
package org.example;

import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        Stream.iterate(0, n -> n + 2)
              .limit(10)
              .forEach(System.out::println);
    }
}
```
> Stream.iterate kullanarak 1’den başlayıp karesini alan ve 1000’i geçene kadar süren sayıları yazdır.
```java
package org.example;

import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        Stream.iterate(1, n -> n * n)
              .takeWhile(n -> n <= 1000)
              .forEach(System.out::println);
    }
}
```
> Stream.generate kullanarak sürekli aynı metni ("hello") üreten bir stream oluştur ve ilk 5’ini yazdır.
```java
package org.example;

import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        Stream.generate(() -> "hello")
              .limit(5)
              .forEach(System.out::println);
    }
}
```
> Stream.iterate ile bir Fibonacci dizisi oluştur. İlk 10 elemanı yazdır.
```java
package org.example;

import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        Stream.iterate(new long[]{0, 1}, arr -> new long[]{arr[1], arr[0] + arr[1]})
              .limit(10)
              .map(arr -> arr[0])
              .forEach(System.out::println);
    }
}
```
> Stream.generate ile UUID üret ve ilk 3 tanesini yazdır.
```java
package org.example;

import java.util.UUID;
import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        Stream.generate(UUID::randomUUID)
              .limit(3)
              .forEach(System.out::println);
    }
}
```