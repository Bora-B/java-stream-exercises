> Bir `List<String>` içindeki kelimeleri uzunluklarına göre grupla.

```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

public class Application {
    public static void main(String[] args) {
        List<String> words = List.of("apple", "banana", "cherry", "melon", "watermelon", "peach", "orange", "strawberry");

        Map<Integer, List<String>> groupedByLength = words.stream()
                .collect(Collectors.groupingBy(String::length));

        System.out.println(groupedByLength);
    }
}
```

> Bir `List<String>` içindeki kelimelerin ilk harfine göre gruplayıp her grubu say.

```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

public class Application {
    public static void main(String[] args) {
        List<String> words = List.of("apple", "ant", "banana", "ball", "boat");

        Map<Character, Long> countByFirstLetter = words.stream()
                .collect(Collectors.groupingBy(word -> word.charAt(0), Collectors.counting()));

        System.out.println(countByFirstLetter);
    }
}
```

> 6. Listedeki tüm sayıların kaç tanesi tek, kaç tanesi çift, bunu bir Map olarak gruplandır:  
> // Örnek çıktı: {even=4, odd=5}

```java
Map<String, Long> grouped = list.stream()
        .collect(Collectors.groupingBy(
                n -> n % 2 == 0 ? "even" : "odd",
                Collectors.counting()
        ));

System.out.println(grouped);
// Örnek çıktı: {odd=5, even=4}
```