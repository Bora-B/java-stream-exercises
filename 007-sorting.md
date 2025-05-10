>Listedeki tüm sayıları büyüklüğe göre sırala ve ilk 3'ü atlayıp sonraki 4'ünü yazdır.
```java
package org.example;

import java.util.*;

public class Application {
    public static void main(String[] args) {
        List<Integer> list = List.of(1, 2, 3, 4, 5, 6, 7, 8, 1, 1, 2, 3, 4, 4, -1, -1, -2, -100);

        list.stream().sorted().skip(3).limit(4).forEach(System.out::println);
    }
}
```
> Kişileri yaşlarına göre küçükten büyüğe sırala
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

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

public class Application {
    public static void main(String[] args) {
        List<Person> people = List.of(
            new Person("Ali", 16),
            new Person("Ayşe", 22),
            new Person("Veli", 18),
            new Person("Zeynep", 14),
            new Person("Mehmet", 20)
        );

        List<Person> sortedByAge = people.stream()
            .sorted(Comparator.comparing(Person::getAge))
            .collect(Collectors.toList());

        System.out.println(sortedByAge);
    }
}
```
> Kişileri isme göre alfabetik sırala
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

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

public class Application {
    public static void main(String[] args) {
        List<Person> people = List.of(
            new Person("Ali", 16),
            new Person("Ayşe", 22),
            new Person("Veli", 18),
            new Person("Zeynep", 14),
            new Person("Mehmet", 20)
        );

        List<Person> sortedByName = people.stream()
            .sorted(Comparator.comparing(Person::getName))
            .collect(Collectors.toList());

        System.out.println(sortedByName);
    }
}
```
> Kişileri önce yaşa göre küçükten büyüğe, yaşlar aynıysa isme göre alfabetik sırala
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

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

public class Application {
    public static void main(String[] args) {
        List<Person> people = List.of(
            new Person("Ali", 16),
            new Person("Ayşe", 22),
            new Person("Veli", 18),
            new Person("Zeynep", 14),
            new Person("Mehmet", 20)
        );

        List<Person> sortedComplex = people.stream()
            .sorted(Comparator.comparing(Person::getAge)
                    .thenComparing(Person::getName))
            .collect(Collectors.toList());

        System.out.println(sortedComplex);
    }
}
```
>Tersine sıralama: yaşa göre büyükten küçüğe
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

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

public class Application {
    public static void main(String[] args) {
        List<Person> people = List.of(
            new Person("Ali", 16),
            new Person("Ayşe", 22),
            new Person("Veli", 18),
            new Person("Zeynep", 14),
            new Person("Mehmet", 20)
        );

        List<Person> sortedDesc = people.stream()
            .sorted(Comparator.comparing(Person::getAge).reversed())
            .collect(Collectors.toList());

        System.out.println(sortedDesc);
    }
}
```