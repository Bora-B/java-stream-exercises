> Liste içindeki listeleri düzleştirme

```java
package org.example;

import java.util.List;

public class Application {
    public static void main(String[] args) {
        List<List<String>> data = List.of(
            List.of("a", "b"),
            List.of("c", "d"),
            List.of("e")
        );

        data.stream()
            .flatMap(List::stream)
            .forEach(System.out::println);
    }
}
```

> Cümleleri kelimelere ayırma

```java
package org.example;

import java.util.List;
import java.util.Arrays;

public class Application {
    public static void main(String[] args) {
        List<String> sentences = List.of(
            "Java is fun",
            "Stream API is powerful"
        );

        sentences.stream()
            .flatMap(sentence -> Arrays.stream(sentence.split(" ")))
            .forEach(System.out::println);
    }
}
```

> List<String[]> var, her String[] harf dizisini temsil ediyor. Tüm harfleri düzleştirip alfabetik sırayla yazdır.

```java
package org.example;

import java.util.List;
import java.util.Arrays;

public class Application {
    public static void main(String[] args) {
        List<String[]> data = List.of(
            new String[]{"c", "a"},
            new String[]{"b", "e"},
            new String[]{"d"}
        );

        data.stream()
            .flatMap(Arrays::stream)
            .sorted()
            .forEach(System.out::println);
    }
}
```
> Her öğrencinin birden fazla dersi var. Tüm dersleri düzleştir, tekrar etmeyecek şekilde listele.
```java
package org.example;

import java.util.List;
import java.util.stream.Collectors;

class Student {
    String name;
    List<String> courses;

    Student(String name, List<String> courses) {
        this.name = name;
        this.courses = courses;
    }
}

public class Application {
    public static void main(String[] args) {
        List<Student> students = List.of(
            new Student("Ali", List.of("Math", "Physics")),
            new Student("Veli", List.of("Math", "Chemistry")),
            new Student("Ayşe", List.of("Biology", "Physics"))
        );

        List<String> allCourses = students.stream()
            .flatMap(student -> student.courses.stream())
            .distinct()
            .collect(Collectors.toList());

        System.out.println(allCourses);
    }
}
```