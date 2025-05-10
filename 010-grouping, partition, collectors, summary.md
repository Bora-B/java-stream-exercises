>Bir `List<String>` içindeki kelimeleri uzunluklarına göre grupla.

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

>Bir `List<String>` içindeki kelimelerin ilk harfine göre gruplayıp her grubu say.

```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

public class Application {
    public static void main(String[] args) {
        var words = List.of("apple", "ant", "banana", "ball", "boat");

        Map<Character, Long> countByFirstLetter = words.stream()
                .collect(Collectors.groupingBy(word -> word.charAt(0), Collectors.counting()));

        System.out.println(countByFirstLetter);
    }
}
```
>Listedeki sayıların kaç tanesi tek, kaç tanesi çift bunu bir Map olarak gruplandır.
```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

public class Application {
    public static void main(String[] args) {
        var numbers = List.of(23, 4, 99, 15, 7, 18, 1, 60, 42);

        Map<String, Long> grouped = numbers.stream()
                .collect(Collectors.groupingBy(
                        n -> n % 2 == 0 ? "even" : "odd",
                        Collectors.counting()
                ));

        System.out.println(grouped);
    }
}
```

>Her kategori altında, o kategoriye ait ürün isimlerini bir `List<String>` olarak grupla.

```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

class Product {
    String name;
    String category;

    Product(String name, String category) {
        this.name = name;
        this.category = category;
    }

    public String getName() { return name; }
    public String getCategory() { return category; }
}

public class Application {
    public static void main(String[] args) {
        var products = List.of(
            new Product("Laptop", "Electronics"),
            new Product("TV", "Electronics"),
            new Product("Banana", "Food"),
            new Product("Apple", "Food"),
            new Product("Shirt", "Clothing")
        );

        Map<String, List<String>> grouped = products.stream()
            .collect(Collectors.groupingBy(
                Product::getCategory,
                Collectors.mapping(Product::getName, Collectors.toList())
            ));

        System.out.println(grouped);
    }
}
```

>Her departmanın toplam maaşını gösteren bir `Map<String, Integer>` üret.

```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

class Employee {
    String department;
    int salary;

    Employee(String department, int salary) {
        this.department = department;
        this.salary = salary;
    }

    public String getDepartment() { return department; }
    public int getSalary() { return salary; }
}

public class Application {
    public static void main(String[] args) {
        var employees = List.of(
            new Employee("IT", 6000),
            new Employee("HR", 4000),
            new Employee("Finance", 5000),
            new Employee("IT", 7000),
            new Employee("HR", 3000)
        );

        Map<String, Integer> totalSalaries = employees.stream()
            .collect(Collectors.groupingBy(
                Employee::getDepartment,
                Collectors.summingInt(Employee::getSalary)
            ));

        System.out.println(totalSalaries);
    }
}
```

>`partitioningBy` kullanarak kişileri 18 yaşından küçük olanlar ve büyük olanlar şeklinde iki gruba ayır.

```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public int getAge() { return age; }
    public String getName() { return name; }
}

public class Application {
    public static void main(String[] args) {
        var people = List.of(
            new Person("Ali", 16),
            new Person("Ayşe", 22),
            new Person("Veli", 18),
            new Person("Zeynep", 14),
            new Person("Mehmet", 20)
        );

        Map<Boolean, List<Person>> partitioned = people.stream()
            .collect(Collectors.partitioningBy(person -> person.getAge() < 18));

        System.out.println(partitioned);
    }
}
```

>Her kategoriye ait ürün isimlerini virgül ile ayırarak tek satırda göster.  
>(Örn: Electronics = Laptop, TV)

```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

class Product {
    String name;
    String category;

    Product(String name, String category) {
        this.name = name;
        this.category = category;
    }

    public String getName() { return name; }
    public String getCategory() { return category; }
}

public class Application {
    public static void main(String[] args) {
        var products = List.of(
            new Product("Laptop", "Electronics"),
            new Product("TV", "Electronics"),
            new Product("Shirt", "Clothing"),
            new Product("Banana", "Food"),
            new Product("Apple", "Food")
        );

        Map<String, String> joined = products.stream()
            .collect(Collectors.groupingBy(
                Product::getCategory,
                Collectors.mapping(Product::getName, Collectors.joining(", "))
            ));

        System.out.println(joined);
    }
}
```

> Derslere göre öğrencileri grupla  
> Elimizde `List<Student>` var. Her öğrenci birden fazla ders alıyor.  
> Her ders için o dersi alan öğrencilerin adlarını bul ve yazdır.  
> Beklenen çıktı (Map):  
> `{ Math = [Ali, Veli], Physics = [Ali, Ayşe], Chemistry = [Veli], Biology = [Ayşe] }`

```java
package org.example;

import java.util.*;
import java.util.stream.Collectors;

public class Application {
    public static void main(String[] args) {
        var students = List.of(
            new Student("Ali", List.of("Math", "Physics")),
            new Student("Veli", List.of("Math", "Chemistry")),
            new Student("Ayşe", List.of("Biology", "Physics"))
        );

        Map<String, List<String>> courseToStudents = students.stream()
            .flatMap(student -> student.courses.stream()
                .map(course -> Map.entry(course, student.name)))
            .collect(Collectors.groupingBy(
                Map.Entry::getKey,
                Collectors.mapping(Map.Entry::getValue, Collectors.toList())
            ));

        System.out.println(courseToStudents);
    }
}

class Student {
    String name;
    List<String> courses;

    Student(String name, List<String> courses) {
        this.name = name;
        this.courses = courses;
    }
}
```

> Her öğrencinin ders adlarının uzunluklarının toplamını hesapla.  
> Örn: "Ali" toplam 11 harflik ders alıyor (`Math` + `Physics`)

```java
package org.example;

import java.util.*;
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
        var students = List.of(
            new Student("Ali", List.of("Math", "Physics")),
            new Student("Veli", List.of("Math", "Chemistry")),
            new Student("Ayşe", List.of("Biology", "Physics"))
        );

        Map<String, Integer> studentCourseLengthSum = students.stream()
            .collect(Collectors.toMap(
                student -> student.name,
                student -> student.courses.stream()
                    .mapToInt(String::length)
                    .sum()
            ));

        System.out.println(studentCourseLengthSum);
    }
}
```