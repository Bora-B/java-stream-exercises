> Bir listedeki tüm sayıların pozitif olup olmadığını allMatch ile kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var nums = List.of(1, 2, 3, 4, 5);

        boolean allPositive = nums.stream().allMatch(n -> n > 0);
        System.out.println(allPositive);
    }
}
```
> Bir listedeki tüm sayıların pozitif olup olmadığını noneMatch ile kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var nums = List.of(1, 2, 3, 4, 5);

        boolean allPositive = nums.stream().noneMatch(n -> n <= 0);
        System.out.println(allPositive);
    }
}
```
>Bir listedeki tüm sayıların pozitif olup olmadığını anyMatch ile kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var nums = List.of(1, 2, 3, 4, 5);

        boolean allPositive = !nums.stream().anyMatch(n -> n <= 0);
        System.out.println(allPositive);
    }
}
```
>Bir listede en az 1 tane java yazısı bulunup bulunmadığını kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var words = List.of("spring", "java", "kotlin");

        boolean containsJava = words.stream().anyMatch(s -> s.equals("java"));

        System.out.println(containsJava); // true
    }
}
```
>Bir listedeki hiçbir String'in boş olup olmadığını kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var texts = List.of("hello", "world", "");

        boolean noneEmpty = texts.stream().noneMatch(String::isEmpty);

        System.out.println(noneEmpty);
    }
}
```
>Bir listedeki sayılar arasında 10'dan büyük en az bir sayı olup olmadığını kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var nums = List.of(3, 7, 11, 2);

        boolean hasGreaterThanTen = nums.stream().anyMatch(n -> n > 10);

        System.out.println(hasGreaterThanTen);
    }
}
```
>Hiçbir sayı çift değil mi diye kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var nums = List.of(1, 3, 5, 7);

        boolean noneEven = nums.stream().noneMatch(n -> n % 2 == 0);

        System.out.println(noneEven);
    }
}
```
>Tüm Person isimleri büyük harfle mi başlıyor diye kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var people = List.of(
                new Person("Ahmet", 25),
                new Person("mehmet", 30)
        );

        boolean allCapitalized = people.stream()
                .allMatch(p -> Character.isUpperCase(p.name.charAt(0)));

        System.out.println(allCapitalized);
    }
}

class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
>Fiyatı 1000'den yüksek en az bir ürün var mı diye kontrol et.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var products = List.of(
                new Product("Laptop", 1500),
                new Product("Mouse", 200)
        );

        boolean expensiveExists = products.stream()
                .anyMatch(p -> p.price > 1000);

        System.out.println(expensiveExists);
    }
}

class Product {
    String name;
    double price;

    Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
}
```