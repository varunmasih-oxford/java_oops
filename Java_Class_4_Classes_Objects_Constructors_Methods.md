# Java Class 4: Classes, Objects, Constructors, and Methods

## 1. Class

**Definition:** A class is a blueprint for creating objects. It defines the variables and methods that objects can use.

### Example

```java
class Student {
    String name;
    int age;
}
```

**Explanation:**
- `class Student` creates a class named `Student`.
- `name` is a variable that can store a student's name.
- `age` is a variable that can store a student's age.
- These variables are called **instance variables** because each object can have its own values.

This class describes a student, but it does not create a student object by itself.

## 2. Object

**Definition:** An object is an instance of a class. You can create objects using the `new` keyword.

### Example: Create a Student Object

```java
class Student {
    String name;
    int age;
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();

        s1.name = "Rahul";
        s1.age = 20;

        System.out.println(s1.name);
        System.out.println(s1.age);
    }
}
```

**Output:**
```text
Rahul
20
```

**Explanation:**
- `Student s1` declares a reference variable named `s1`.
- `new Student()` creates a new `Student` object.
- `s1.name = "Rahul"` stores the name in that object.
- `s1.age = 20` stores the age in that object.
- `System.out.println()` displays the values.

## 3. Multiple Objects

Objects created from the same class can store different values.

### Example

```java
class Student {
    String name;
    int marks;
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.name = "Rahul";
        s1.marks = 85;

        Student s2 = new Student();
        s2.name = "Priya";
        s2.marks = 92;

        System.out.println(s1.name + " scored " + s1.marks);
        System.out.println(s2.name + " scored " + s2.marks);
    }
}
```

**Output:**
```text
Rahul scored 85
Priya scored 92
```

**Explanation:**
- `s1` and `s2` refer to two separate objects.
- Both objects use the `Student` class.
- Each object has its own `name` and `marks` values.

## 4. Methods

**Definition:** A method is a block of code that performs a task. A method can be called whenever that task is needed.

### Example: Display Student Details

```java
class Student {
    String name = "Rahul";
    int age = 20;

    void display() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();

        s1.display();
    }
}
```

**Output:**
```text
Name: Rahul
Age: 20
```

**Explanation:**
- `void` means the method does not return a value.
- `display()` is the method name.
- The code inside `{ }` runs when the method is called.
- `s1.display()` calls the method through the object.

### Method with Parameters

**Definition:** Parameters allow you to pass information into a method.

```java
class Calculator {
    void add(int a, int b) {
        System.out.println("Sum: " + (a + b));
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator c1 = new Calculator();

        c1.add(10, 20);
        c1.add(5, 7);
    }
}
```

**Output:**
```text
Sum: 30
Sum: 12
```

**Explanation:**
- `int a` and `int b` are parameters.
- `c1.add(10, 20)` passes `10` and `20` to the method.
- The same method can be reused with different values.

## 5. Constructors

**Definition:** A constructor is a special part of a class that runs when an object is created. It is commonly used to initialize an object's values.

**Constructor rules:**
- Its name must match the class name.
- It has no return type, not even `void`.
- It runs when an object is created with `new`.

### Example: Constructor

```java
class Student {
    String name;
    int age;

    Student() {
        name = "Rahul";
        age = 20;
    }

    void display() {
        System.out.println(name + ", " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();

        s1.display();
    }
}
```

**Output:**
```text
Rahul, 20
```

**Explanation:**
- `Student()` is the constructor because it has the same name as the class.
- `new Student()` calls the constructor.
- The constructor assigns initial values to `name` and `age`.
- `s1.display()` displays those values.

## 6. Constructor with Parameters

A constructor can accept parameters so each object can start with different values.

### Example

```java
class Student {
    String name;
    int age;

    Student(String studentName, int studentAge) {
        name = studentName;
        age = studentAge;
    }

    void display() {
        System.out.println(name + " is " + age + " years old.");
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Rahul", 20);
        Student s2 = new Student("Priya", 21);

        s1.display();
        s2.display();
    }
}
```

**Output:**
```text
Rahul is 20 years old.
Priya is 21 years old.
```

**Explanation:**
- `Student(String studentName, int studentAge)` is a parameterized constructor.
- `new Student("Rahul", 20)` passes values to the constructor.
- The constructor stores those values in the object's variables.
- Each object can be initialized with different information.

## 7. Constructor vs Method

| Constructor | Method |
|---|---|
| Initializes an object when it is created. | Performs a task. |
| Name must match the class name. | Can have any valid method name. |
| Has no return type. | Has a return type, such as `void`, `int`, or `String`. |
| Called automatically during object creation. | Usually called explicitly. |

## 8. Complete Example: Student Class

This example combines instance variables, a parameterized constructor, and a method.

```java
class Student {
    String name;
    int marks;

    Student(String studentName, int studentMarks) {
        name = studentName;
        marks = studentMarks;
    }

    void displayResult() {
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
        Student s1 = new Student("Rahul", 85);
        Student s2 = new Student("Priya", 32);

        s1.displayResult();
        System.out.println();
        s2.displayResult();
    }
}
```

**Output:**
```text
Student: Rahul
Marks: 85
Result: Pass

Student: Priya
Marks: 32
Result: Fail
```

**Explanation:**
1. The `Student` class defines `name`, `marks`, a constructor, and a method.
2. The constructor assigns values when each object is created.
3. `s1` and `s2` are two different student objects.
4. `displayResult()` displays the student's details and checks the result.

## 9. Student Practice Tasks

1. Create an `Employee` class with `name` and `salary` variables.
2. Create two `Employee` objects with different values and display their details.
3. Create a `Book` class with `title` and `price` variables.
4. Add a method named `display()` to display book details.
5. Create a constructor that sets a book's title and price.
6. Create a `Calculator` class with a method that multiplies two numbers.
7. Create a `Student` class with a parameterized constructor and a method that displays whether the student passed or failed.

## Class Summary

In this class, you learned:
- A **class** is a blueprint for creating objects.
- An **object** is an instance of a class.
- A **constructor** initializes an object when it is created.
- A **method** performs a task and can be reused.
- Parameters allow constructors and methods to receive values.
