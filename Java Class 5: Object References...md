# Java Class 5: Object References, `null`, Method Overloading, and `static`
## 1. Object References
**Definition:** An object reference is a variable that refers to an object. When you create an object with `new`, the reference lets you access that object’s variables and methods.
### Example
```javaclass Student {    String name;}
public class Main {    public static void main(String[] args) {        Student s1 = new Student();        s1.name = "Rahul";
        System.out.println(s1.name);    }}```
**Output:**```textRahul```
**Explanation:**- `new Student()` creates a `Student` object.- `s1` is a reference variable that refers to that object.- `s1.name` accesses the `name` variable in the object.
A reference variable does not contain the object itself. It provides a way to access the object.
## 2. Class-Type Variables
A variable whose type is a class is called a **class-type variable**. It can refer to an object created from that class.
```javaStudent s1 = new Student();```
Here, `Student` is the class type, and `s1` is a class-type reference variable.
### Two References to the Same Object
You can assign one object reference to another. Both variables will then refer to the same object.
```javaclass Student {    String name;}
public class Main {    public static void main(String[] args) {        Student s1 = new Student();        s1.name = "Rahul";
        Student s2 = s1;        s2.name = "Priya";
        System.out.println(s1.name);        System.out.println(s2.name);    }}```
**Output:**```textPriyaPriya```
**Explanation:**- `Student s2 = s1;` copies the reference, not the object.- Both `s1` and `s2` refer to the same `Student` object.- Changing the object through `s2` is also visible through `s1`.
## 3. The `null` Value
**Definition:** `null` means that a reference variable does not refer to any object.
```javaStudent s1 = null;```
You can check whether a reference is `null` before using it.
```javaclass Student {    String name;}
public class Main {    public static void main(String[] args) {        Student s1 = null;
        if (s1 == null) {            System.out.println("No student object exists.");        }    }}```
**Output:**```textNo student object exists.```
Trying to use a `null` reference to access a variable or call a method causes a **`NullPointerException`**.
```javaStudent s1 = null;System.out.println(s1.name); // Causes a NullPointerException```
**Remember:** Check that a reference is not `null` before using it.
## 4. Method Overloading
**Definition:** Method overloading means creating multiple methods with the same name but different parameter lists.
Overloaded methods must differ in their **number, types, or order of parameters**. Changing only the return type is not enough.
### Example
```javaclass Calculator {    int add(int a, int b) {        return a + b;    }
    int add(int a, int b, int c) {        return a + b + c;    }
    double add(double a, double b) {        return a + b;    }}
public class Main {    public static void main(String[] args) {        Calculator calculator = new Calculator();
        System.out.println(calculator.add(10, 20));        System.out.println(calculator.add(10, 20, 30));        System.out.println(calculator.add(2.5, 3.5));    }}```
**Output:**```text30606.0```
**Explanation:**- The first `add()` method accepts two `int` values.- The second accepts three `int` values.- The third accepts two `double` values.- Java chooses which method to call based on the arguments.
## 5. The `static` Keyword
**Definition:** The `static` keyword makes a variable or method belong to the class itself rather than to each individual object.
### Static Variable
A **static variable** is shared by all objects of its class.
```javaclass Student {    String name;    static String school = "Green Valley School";}
public class Main {    public static void main(String[] args) {        Student s1 = new Student();        s1.name = "Rahul";
        Student s2 = new Student();        s2.name = "Priya";
        System.out.println(s1.name + " studies at " + Student.school);        System.out.println(s2.name + " studies at " + Student.school);    }}```
**Output:**```textRahul studies at Green Valley SchoolPriya studies at Green Valley School```
**Explanation:**- `name` is an instance variable, so each object has its own value.- `school` is static, so it is shared by all `Student` objects.- A static variable is commonly accessed using the class name, such as `Student.school`.
### Static Method
A **static method** belongs to the class and can be called without creating an object.
```javaclass Calculator {    static int square(int number) {        return number * number;    }}
public class Main {    public static void main(String[] args) {        System.out.println(Calculator.square(5));    }}```
**Output:**```text25```
**Explanation:**- `square()` is declared with `static`.- It is called using the class name: `Calculator.square(5)`.- A static method cannot directly use instance variables or call instance methods because those belong to objects.
## 6. Instance Members vs. Static Members
| Instance member | Static member ||---|---|| Belongs to an individual object. | Belongs to the class. || Each object has its own instance variable values. | A static variable is shared by the class’s objects. || Usually accessed through an object. | Commonly accessed through the class name. || Can use both instance and static members. | Cannot directly access instance members without an object. |
## 7. Complete Example
This example combines object references, `null`, method overloading, and static members.
```javaclass Student {    String name;    static int studentCount = 0;
    Student(String studentName) {        name = studentName;        studentCount++;    }
    void display() {        System.out.println("Student: " + name);    }
    void display(String message) {        System.out.println(message + " " + name);    }
    static void displayStudentCount() {        System.out.println("Students created: " + studentCount);    }}
public class Main {    public static void main(String[] args) {        Student s1 = new Student("Rahul");        Student s2 = s1;
        s2.display();        s1.display("Welcome,");
        Student s3 = null;
        if (s3 == null) {            System.out.println("s3 does not refer to a student object.");        }
        Student.displayStudentCount();    }}```
**Output:**```textStudent: RahulWelcome, Rahuls3 does not refer to a student object.Students created: 1```
**Explanation:**1. `s1` refers to a `Student` object.2. `s2 = s1` makes `s2` refer to the same object as `s1`.3. The two `display()` methods are overloaded because they have different parameter lists.4. `s3` is `null`, so it does not refer to an object.5. `studentCount` is static and shared by the `Student` class.
## 8. Student Practice Tasks
1. Create a `Book` class and make two reference variables point to the same `Book` object.2. Set a class-type variable to `null` and check it before calling a method.3. Create overloaded `multiply()` methods for two integers and three integers.4. Add a static variable to a `Car` class to count how many cars are created.5. Create a static method that displays a message without requiring an object.
## Class Summary
In this class, you learned:- An **object reference** provides access to an object.- Class-type variables can refer to objects, and multiple references can point to the same object.- **`null`** means a reference does not refer to an object.- **Method overloading** uses the same method name with different parameter lists.- **Static variables and methods** belong to the class rather than to individual objects.
