# Java Class 6: Scanner, Getters, Setters, `final`, Access Modifiers, and Encapsulation

## 1. Scanner

**Definition:** `Scanner` is a Java class used to read input, such as text and numbers, from the user. It is part of the `java.util` package.

### Example: Read User Input

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = input.nextLine();

        System.out.print("Enter your age: ");
        int age = input.nextInt();

        System.out.println("Hello, " + name + ". You are " + age + " years old.");

        input.close();
    }
}
```

**Example output:**
```text
Enter your name: Rahul
Enter your age: 20
Hello, Rahul. You are 20 years old.
```

**Explanation:**
- `import java.util.Scanner;` makes the `Scanner` class available.
- `new Scanner(System.in)` creates a scanner that reads keyboard input.
- `nextLine()` reads a line of text.
- `nextInt()` reads an integer.
- `close()` closes the scanner when it is no longer needed.

### Common Scanner Methods

| Method | Reads |
|---|---|
| `nextLine()` | A full line of text |
| `next()` | One word |
| `nextInt()` | An integer |
| `nextDouble()` | A decimal number |
| `nextBoolean()` | `true` or `false` |

> **Note:** After reading a number with `nextInt()` or `nextDouble()`, a leftover newline may affect a following `nextLine()`. Call `nextLine()` once to consume it.

```java
int age = input.nextInt();
input.nextLine(); // Consume the leftover newline
String name = input.nextLine();
```

## 2. Access Modifiers

**Definition:** Access modifiers control where classes, variables, constructors, and methods can be accessed.

### Main Access Modifiers

| Modifier | Access |
|---|---|
| `public` | Accessible from anywhere |
| `private` | Accessible only inside the same class |
| `protected` | Accessible in the same package and in subclasses |
| No modifier (package-private) | Accessible within the same package |

### Example

```java
class Person {
    public String name = "Rahul";
    private int age = 20;

    public void displayName() {
        System.out.println(name);
    }

    private void displayAge() {
        System.out.println(age);
    }
}
```

**Explanation:**
- `name` is `public`, so it can be accessed from other classes.
- `age` is `private`, so it can only be accessed inside `Person`.
- `displayAge()` is private and cannot be called directly from outside `Person`.

## 3. Getters and Setters

**Definition:** A getter returns the value of a private variable. A setter changes its value.

### Example

```java
class Person {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String newName) {
        name = newName;
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person();

        person.setName("Rahul");
        System.out.println(person.getName());
    }
}
```

**Output:**
```text
Rahul
```

**Explanation:**
- `private String name` prevents direct access from outside the class.
- `getName()` returns the value of `name`.
- `setName()` updates the value of `name`.
- `person.setName("Rahul")` calls the setter.
- `person.getName()` calls the getter.

### Setter with Validation

A setter can check a value before storing it.

```java
class Person {
    private int age;

    public int getAge() {
        return age;
    }

    public void setAge(int newAge) {
        if (newAge >= 0) {
            age = newAge;
        } else {
            System.out.println("Age cannot be negative.");
        }
    }
}
```

**Explanation:**
- The setter only stores `newAge` if it is zero or greater.
- This helps protect an object's data from invalid values.

## 4. Encapsulation

**Definition:** Encapsulation means keeping data and the methods that work with it together in a class, while controlling access to that data.

A common way to use encapsulation is to:
1. Make instance variables `private`.
2. Provide `public` getters and setters.
3. Validate values inside setters when needed.

### Example: Encapsulated Student Class

```java
class Student {
    private String name;
    private int marks;

    public Student(String name, int marks) {
        this.name = name;
        setMarks(marks);
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getMarks() {
        return marks;
    }

    public void setMarks(int marks) {
        if (marks >= 0 && marks <= 100) {
            this.marks = marks;
        } else {
            System.out.println("Marks must be between 0 and 100.");
        }
    }

    public void display() {
        System.out.println("Name: " + name);
        System.out.println("Marks: " + marks);
    }
}

public class Main {
    public static void main(String[] args) {
        Student student = new Student("Priya", 92);

        student.display();
        student.setMarks(105);
    }
}
```

**Output:**
```text
Name: Priya
Marks: 92
Marks must be between 0 and 100.
```

**Explanation:**
- `name` and `marks` are private, so they cannot be changed directly from `Main`.
- The constructor initializes the student's data.
- `setMarks()` checks that marks are within the valid range.
- `this.marks` refers to the object's instance variable.

## 5. The `this` Keyword

**Definition:** `this` refers to the current object. It is often used when a parameter has the same name as an instance variable.

```java
class Student {
    private String name;

    public void setName(String name) {
        this.name = name;
    }
}
```

**Explanation:**
- `name` on the right is the method parameter.
- `this.name` on the left is the object's instance variable.
- `this.name = name;` stores the parameter value in the object.

## 6. The `final` Keyword

**Definition:** `final` prevents something from being changed or extended, depending on where it is used.

### Final Variable

A `final` variable can be assigned only once.

```java
class Main {
    public static void main(String[] args) {
        final double PI = 3.14159;

        System.out.println(PI);
    }
}
```

**Explanation:**
- `PI` is assigned a value once.
- Trying to assign another value to `PI` causes a compile-time error.
- Constant names are commonly written in uppercase.

### Final Method

A `final` method cannot be overridden by a subclass.

```java
class Animal {
    final void breathe() {
        System.out.println("Breathing...");
    }
}
```

### Final Class

A `final` class cannot be extended.

```java
final class Utility {
}
```

## 7. Complete Example: Scanner and Encapsulation

This example reads values from the user and stores them using setters.

```java
import java.util.Scanner;

class Student {
    private String name;
    private int marks;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getMarks() {
        return marks;
    }

    public void setMarks(int marks) {
        if (marks >= 0 && marks <= 100) {
            this.marks = marks;
        } else {
            System.out.println("Marks must be between 0 and 100.");
        }
    }

    public void displayResult() {
        System.out.println("Student: " + name);
        System.out.println("Marks: " + marks);

        if (marks >= 40) {
            System.out.println("Result: Pass");
        } else {
            System.out.println("Result: Fail");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        Student student = new Student();

        System.out.print("Enter student name: ");
        student.setName(input.nextLine());

        System.out.print("Enter marks: ");
        student.setMarks(input.nextInt());

        student.displayResult();

        input.close();
    }
}
```

**Example output:**
```text
Enter student name: Priya
Enter marks: 92
Student: Priya
Marks: 92
Result: Pass
```

**Explanation:**
1. `Scanner` reads the student's name and marks.
2. The `Student` class keeps its variables private.
3. Setters provide controlled access to the variables.
4. `setMarks()` checks that the marks are valid.
5. `displayResult()` displays the details and result.

## 8. Student Practice Tasks

1. Create a `Book` class with private `title` and `price` variables.
2. Add getters and setters for the book's title and price.
3. Make the price setter reject negative values.
4. Use `Scanner` to read a book's title and price from the user.
5. Create a `BankAccount` class with a private balance and a setter that rejects negative balances.
6. Create a `final` variable for a tax rate and display it.
7. Create a class with a `final` method and try to override it in a subclass.

## Class Summary

In this class, you learned:
- `Scanner` reads input from the user.
- Access modifiers control where class members can be used.
- Getters return private values, and setters update them.
- Encapsulation protects data by controlling how it is accessed and changed.
- `this` refers to the current object.
- `final` can prevent a variable from being reassigned, a method from being overridden, or a class from being extended.
```
