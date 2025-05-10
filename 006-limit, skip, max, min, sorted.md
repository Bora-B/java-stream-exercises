>Listedeki en küçük 5 sayıyı artarak sırayla yazdır.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        List<Integer> list = List.of(23, 4, 99, 15, 7, 18, 1, 60, 42);

        list.stream().sorted().limit(5).forEach(System.out::println);
    }
}
```
>Bir `List<Integer>` içinden en büyük 3 sayıyı bul ve yazdır.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        List<Integer> numbers = List.of(5, 12, 3, 19, 8, 25);

        numbers.stream().sorted(Comparator.reverseOrder()).limit(3).forEach(System.out::println);
    }
}
```
>Listedeki en büyük sayıyı bul ve yazdır (reduce KULLANMADAN).
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        List<Integer> list = List.of(1, 2, 3, 4, 5, 6, 7, 8, 1, 1, 2, 3, 4, 4, -1, -1, -2, -100);

        int max = list.stream()
                .max(Integer::compareTo)
                .orElseThrow();

        System.out.println(max);
    }
}
```
>Listedeki sayıların medyanını (ortanca) bul.  
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        List<Integer> list = List.of(1, 2, 3, 4, 5, 6, 7, 8, 1, 1, 2, 3, 4, 4, -1, -1, -2, -100);
        
        List<Integer> sorted = list.stream()
                .sorted()
                .toList();

        double median;
        int size = sorted.size();

        if (size % 2 == 1)
            median = sorted.get(size / 2);
        else
            median = (sorted.get(size / 2 - 1) + sorted.get(size / 2)) / 2.0;

        System.out.println(median);
    }
}
```
>Listedeki tüm sayılar içinde en büyük çift sayı kaçtır?
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        List<Integer> list = List.of(1, 2, 3, 4, 5, 6, 7, 8, 1, 1, 2, 3, 4, 4, -1, -1, -2, -100);

        int maxEven = list.stream()
                .filter(n -> n % 2 == 0)
                .max(Integer::compareTo)
                .orElseThrow();

        System.out.println(maxEven);
    }
}
```