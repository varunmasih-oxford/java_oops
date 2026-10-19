# Java Class 7: Packages, Imports, Java Libraries, and Arrays
## 1. Packages
**Definition:** A package groups related classes and helps organize Java programs. It also helps prevent naming conflicts between classes.
A package declaration, if used, must appear at the top of the Java file before imports and class definitions.
### Example: Declare a Package
```javapackage school;
public class Student {    public void display() {        System.out.println("I am a student.");    }}```
**Explanation:**- `package school;` places the `Student` class in the `school` package.- The source file should be stored in a folder named `school`.- The file name must be `Student.java` because `Student` is public.
### Using a Class from Another Package
Suppose the `Student` class is in the `school` package. A class in a different package can use its full name:
```javapublic class Main {    public static void main(String[] args) {        school.Student student = new school.Student();        student.display();    }}```
**Output:**```textI am a student.```
## 2. Imports
**Definition:** An `import` statement lets you use a class from another package without writing its full package name every time.
### Example: Import One Class
```javaimport school.Student;
public class Main {    public static void main(String[] args) {        Student student = new Student();        student.display();    }}```
**Explanation:**- `import school.Student;` imports the `Student` class.- The program can then use `Student` instead of `school.Student`.
### Import All Classes in a Package
```javaimport java.util.*;
public class Main {    public static void main(String[] args) {        Scanner input = new Scanner(System.in);        System.out.println("Enter your name:");
        String name = input.nextLine();        System.out.println("Hello, " + name);
        input.close();    }}```
**Explanation:**- `import java.util.*;` makes the classes in `java.util` available by their simple names.- The `*` imports classes in that package, but not classes in its subpackages.- Many Java programs import only the classes they need, such as `import java.util.Scanner;`.
## 3. Java Library Packages
Java includes many built-in packages containing useful classes and interfaces.
| Package | Common uses and examples ||---|---|| `java.lang` | Core Java classes such as `String`, `Math`, and `System` || `java.util` | Utility classes such as `Scanner`, `ArrayList`, and `Arrays` || `java.io` | Input and output, such as file handling || `java.time` | Dates and times, such as `LocalDate` || `java.net` | Networking classes |
The `java.lang` package is imported automatically, so you do not need to write `import java.lang.*;`.
### Example: Using `Math`
```javapublic class Main {    public static void main(String[] args) {        System.out.println(Math.max(12, 25));        System.out.println(Math.sqrt(81));    }}```
**Output:**```text259.0```
## 4. Arrays
**Definition:** An array stores a fixed number of values of the same type. Each value is stored at an index, beginning with index `0`.
### Declare and Create an Array
```javaint[] marks = new int[3];
marks[0] = 85;marks[1] = 92;marks[2] = 78;```
You can also declare and initialize an array in one statement:
```javaint[] marks = {85, 92, 78};```
### Example: Read and Display Array Values
```javapublic class Main {    public static void main(String[] args) {        int[] marks = {85, 92, 78};
        System.out.println("First mark: " + marks[0]);        System.out.println("Number of marks: " + marks.length);
        for (int i = 0; i < marks.length; i++) {            System.out.println(marks[i]);        }    }}```
**Output:**```textFirst mark: 85Number of marks: 3859278```
**Explanation:**- `marks[0]` accesses the first value.- `marks.length` gives the number of elements in the array.- The loop visits each valid index, from `0` through `marks.length - 1`.- Using an invalid index causes an `ArrayIndexOutOfBoundsException`.
### Enhanced `for` Loop
An enhanced `for` loop visits each array element without using an index.
```javapublic class Main {    public static void main(String[] args) {        String[] names = {"Ava", "Noah", "Mia"};
        for (String name : names) {            System.out.println(name);        }    }}```
**Output:**```textAvaNoahMia```
### Default Array Values
When an array is created with `new`, its elements receive default values.
| Element type | Default value ||---|---|| Numeric types, such as `int` and `double` | `0` or `0.0` || `char` | `'\u0000'` || `boolean` | `false` || Reference types, such as `String` | `null` |
## 5. Using the `Arrays` Library Class
The `Arrays` class is in the `java.util` package. It provides helpful methods for working with arrays.
### Example: Sort and Display an Array
```javaimport java.util.Arrays;
public class Main {    public static void main(String[] args) {        int[] numbers = {40, 10, 30, 20};
        Arrays.sort(numbers);
        System.out.println(Arrays.toString(numbers));    }}```
**Output:**```text[10, 20, 30, 40]```
**Explanation:**- `Arrays.sort(numbers)` sorts the array in ascending order.- `Arrays.toString(numbers)` creates a readable text representation of a one-dimensional array.- `Arrays` must be imported because it belongs to `java.util`.
## 6. Multidimensional Arrays
**Definition:** A multidimensional array is an array whose elements are other arrays. A two-dimensional array is often used to represent rows and columns.
### Example: Two-Dimensional Array
```javapublic class Main {    public static void main(String[] args) {        int[][] scores = {            {80, 90, 85},            {75, 88, 92}        };
        System.out.println(scores[0][1]);        System.out.println(scores[1][2]);    }}```
**Output:**```text9092```
**Explanation:**- `scores[0]` refers to the first row.- `scores[0][1]` refers to the second value in the first row.- Array indexes begin at `0`.
### Loop Through a Two-Dimensional Array
```javapublic class Main {    public static void main(String[] args) {        int[][] numbers = {            {1, 2, 3},            {4, 5, 6}        };
        for (int row = 0; row < numbers.length; row++) {            for (int column = 0; column < numbers[row].length; column++) {                System.out.print(numbers[row][column] + " ");            }            System.out.println();        }    }}```
**Output:**```text1 2 34 5 6```
**Explanation:**- `numbers.length` gives the number of rows.- `numbers[row].length` gives the number of values in the current row.- The outer loop visits each row, and the inner loop visits each value in that row.
## 7. Jagged Arrays
A **jagged array** is a multidimensional array whose rows can have different lengths.
```javapublic class Main {    public static void main(String[] args) {        int[][] numbers = new int[3][];
        numbers[0] = new int[] {1, 2};        numbers[1] = new int[] {3, 4, 5};        numbers[2] = new int[] {6};
        for (int row = 0; row < numbers.length; row++) {            for (int column = 0; column < numbers[row].length; column++) {                System.out.print(numbers[row][column] + " ");            }            System.out.println();        }    }}```
**Output:**```text1 23 4 56```
**Explanation:**- Each row is a separate array.- The rows can contain different numbers of elements.- Use `numbers[row].length` to get the length of the current row.
## 8. Complete Example: Student Test Scores
This example combines arrays, a two-dimensional array, and the `Arrays` library class.
```javaimport java.util.Arrays;
public class Main {    public static void main(String[] args) {        String[] students = {"Ava", "Noah", "Mia"};
        int[][] scores = {            {85, 90},            {78, 88},            {92, 95}        };
        for (int row = 0; row < students.length; row++) {            System.out.println(                students[row] + "'s scores: " + Arrays.toString(scores[row])            );        }    }}```
**Output:**```textAva's scores: [85, 90]Noah's scores: [78, 88]Mia's scores: [92, 95]```
**Explanation:**1. `students` is a one-dimensional array of names.2. `scores` is a two-dimensional array of test scores.3. Each row in `scores` contains the scores for the matching student.4. `Arrays.toString()` displays each row in a readable format.
## 9. Student Practice Tasks
1. Create an array of five numbers and display each number using a loop.2. Find and display the largest number in an integer array.3. Create a `String` array of four names and display its length.4. Create a two-dimensional array with three rows and two columns, then print every value.5. Create a jagged array whose rows have different lengths.6. Import `java.util.Arrays`, sort an array, and display the sorted result.7. Create a package named `school` and place a class named `Teacher` inside it.
## Class Summary
In this class, you learned:- **Packages** organize related Java classes.- **Imports** let you use classes from other packages by their simple names.- Java provides library packages such as `java.util` and `java.time`.- **Arrays** store a fixed number of values of the same type.- Array indexes begin at `0`, and the `length` property gives the array size.- **Multidimensional arrays** contain other arrays, and jagged arrays can have rows of different lengths.

