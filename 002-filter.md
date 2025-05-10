>Soru: Bir `List<String>` içindeki String'lerden uzunluğu 5'ten büyük olanları yazdır.

```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var list = List.of("java", "spring", "stream", "reflection", "method reference", "functional programming", "C", "maven", "int");

        list.stream().filter(s -> s.length() > 5).forEach(System.out::println);
    }
}
```

>Soru: Bir `List<Integer>` içindeki sadece çift sayıları filtreleyip yazdır.

```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var list = List.of(1, 2, 3, 4, 5);
        
        list.stream().filter(s -> s % 2 == 0).forEach(System.out::println);
    }
}
```

>Soru: Bir `List<String>` içindeki String'lerden uzunluğu 5'ten büyük olanların sayısını yazdır.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        var list = List.of("java", "spring", "stream", "reflection", "method reference", "functional programming", "C", "maven", "int");

        long count = list.stream().filter(s -> s.length() > 5).count();
        System.out.println(count);
    }
}
```
