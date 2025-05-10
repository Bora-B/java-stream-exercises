>Bir Collection'dan stream oluştur.

```java
package org.example;

import java.util.*;
import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        List<Integer> list = List.of(1, 2, 3, 4, 5);
        Stream<Integer> streamInteger = list.stream();

        Set<String> set = Set.of("java", "maven", "gradle", "kotlin", "stream", "android");
        Stream<String> streamString = set.stream();
    }
}
```

>Bir Array'den stream oluştur.

```java
package org.example;

import java.util.stream.DoubleStream;
import java.util.stream.IntStream;
import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        int[] intArr = {1, 2, 3, 4, 5, 6};
        double[] doubleArr = {1., 2., 3., 4., 5., 6.};
        String[] stringArr = {"a", "bb", "ccc", "dddd", "eeeee", "ffffff", "gggggggg"};

        IntStream intStream = IntStream.of(intArr);
        IntStream intStream2 = IntStream.of(10, 11, 12, 13, 14, 15);
        DoubleStream doubleStream = DoubleStream.of(3., 5.3, 12.2, 7., -120);
        DoubleStream doubleStream2 = DoubleStream.of(doubleArr);

        Stream<Integer> integerStream = Stream.of(10, 11, 12, 13, 14, 15);
        Stream<String> stringStream = Stream.of(stringArr);
    }
}
```

>Bir stream'in elemanlarını ekrana yaz.
```java
package org.example;

import java.util.stream.DoubleStream;
import java.util.stream.IntStream;
import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        int[] intArr = {1, 2, 3, 4, 5, 6};
        double[] doubleArr = {1., 2., 3., 4., 5., 6.};
        String[] stringArr = {"a", "bb", "ccc", "dddd", "eeeee", "ffffff", "gggggggg"};

        IntStream.of(intArr).forEach(System.out::println);

        DoubleStream.of(3., 5.3, 12.2, 7., -120).forEach(System.out::println);
        
        Stream.of(stringArr).forEach(System.out::println);
    }
}
```

>Bir stream'in elemanlarını tekrar etmeyecek şekilde ekrana yaz.
```java
package org.example;

import java.util.stream.DoubleStream;
import java.util.stream.IntStream;
import java.util.stream.Stream;

public class Application {
    public static void main(String[] args) {
        int[] intArr = {1, 2, 2, 3, 3, 4, 5, 6};
        double[] doubleArr = {1., 2., 3., 4., 5., 6., 1., 1., 2., 2.};
        String[] stringArr = {"a", "a", "bb", "bb", "ccc", "dddd", "eeeee", "ffffff", "gggggggg"};

        IntStream.of(intArr).distinct().forEach(System.out::println);

        DoubleStream.of(3., 5.3, 12.2, 7., -120).distinct().forEach(System.out::println);
        
        Stream.of(stringArr).distinct().forEach(System.out::println);
    }
}
```