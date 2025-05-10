>Bir `Stream<Integer>` içindeki sayıların çarpımını hesaplayıp ekrana yazdır, Stream boş ise 1 elde edilsin.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var list = List.of(1, 2, 3, 4, 5);

        var sum = list.stream().reduce(1, (i1, i2) -> i1 * i2);
        System.out.println(sum);
    }
}
```
>Bir `Stream<Integer>` içindeki sayıların karelerinin toplamını hesaplayıp ekrana yazdır.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var list = List.of(1, 2, 3, 4, 5);

        var sum = list.stream().filter(i -> i % 2 == 1).map(i -> i * i).reduce(Integer::sum);
        System.out.println(sum);
    }
}
```

>Bir `Stream<String>` içindeki String'leri birleştirip ekrana yazdır.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var list = List.of("elma", "armut", "muz", "kivi", "kiraz", "vişne", "şeftali");

        var str = list.stream().reduce(String::concat);
        str.ifPresent(System.out::println);
    }
}
```

>Bir `Stream<String>` içindeki String'lerden ilk harfi büyük olanları filtreleyip aralarına , koyarak birleştirip ekrana yazdır.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var list = List.of("java", "spring", "stream", "sTreAm", "REFLECTION", "JAVA", "reflection", "method reference", "functional programming", "C", "maven", "int");

        var str = list.stream().filter(s -> Character.isUpperCase(s.charAt(0))).reduce((s1, s2) -> s1 + ", " + s2);
        str.ifPresent(System.out::println);
    }
}
```
>Bir `List<String>` içindeki String'lerden lexicographic karşılaştırmaya göre en büyüğünü reduce ile bul.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var list = List.of("java", "spring", "stream", "sTreAm", "REFLECTION", "JAVA", "reflection", "method reference", "functional programming", "C", "maven", "int");

        var str = list.stream().reduce((s1, s2) -> s1.compareTo(s2) > 0 ? s1 : s2);
        str.ifPresent(System.out::println);
    }
}
```
