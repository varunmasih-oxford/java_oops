# Java Class 9: ArrayList, Vector, LinkedList, Iterator, and ListIterator
## 1. The `List` Interface
**Definition:** A `List` is a collection that stores elements in a sequence. Lists preserve the order in which elements are added and allow duplicate values.
Java provides several classes that implement the `List` interface, including:- `ArrayList`- `Vector`- `LinkedList`
To use these classes, import them from `java.util`.
```javaimport java.util.ArrayList;import java.util.List;```
## 2. ArrayList
**Definition:** An `ArrayList` is a resizable list. It can grow or shrink as elements are added or removed.
### Example: Create and Display an ArrayList
```javaimport java.util.ArrayList;
public class Main {    public static void main(String[] args) {        ArrayList<String> fruits = new ArrayList<>();
        fruits.add("Apple");        fruits.add("Banana");        fruits.add("Mango");
        System.out.println(fruits);    }}```
**Output:**```text[Apple, Banana, Mango]```
**Explanation:**- `ArrayList<String>` creates a list that stores `String` values.- `add()` adds an element to the end of the list.- `System.out.println(fruits)` displays the list's elements.
### Common ArrayList Methods
```javaimport java.util.ArrayList;
public class Main {    public static void main(String[] args) {        ArrayList<String> fruits = new ArrayList<>();
        fruits.add("Apple");        fruits.add("Banana");        fruits.add("Mango");
        System.out.println(fruits.get(1));
        fruits.set(1, "Orange");        System.out.println(fruits);
        fruits.remove("Apple");        System.out.println(fruits);
        System.out.println("Size: " + fruits.size());        System.out.println("Contains Mango: " + fruits.contains("Mango"));    }}```
**Output:**```textBanana[Apple, Orange, Mango][Orange, Mango]Size: 2Contains Mango: true```
**Explanation:**- `get(1)` returns the element at index `1`.- `set(1, "Orange")` replaces the element at index `1`.- `remove("Apple")` removes the matching element.- `size()` returns the number of elements.- `contains("Mango")` checks whether the list contains `"Mango"`.
**Note:** List indexes begin at `0`, so the first element is at index `0`.
## 3. Vector
**Definition:** A `Vector` is a resizable list, similar to an `ArrayList`. Its methods are synchronized, which can help protect access when multiple threads use the same vector.
### Example
```javaimport java.util.Vector;
public class Main {    public static void main(String[] args) {        Vector<String> colors = new Vector<>();
        colors.add("Red");        colors.add("Green");        colors.add("Blue");
        System.out.println(colors);        System.out.println("First color: " + colors.get(0));
        colors.remove("Green");        System.out.println(colors);    }}```
**Output:**```text[Red, Green, Blue]First color: Red[Red, Blue]```
**Explanation:**- `Vector<String>` creates a vector for storing strings.- `add()` adds elements to the vector.- `get(0)` returns the first element.- `remove("Green")` removes `"Green"` from the vector.
**Remember:** `Vector` is a legacy collection class. For many everyday programs, `ArrayList` is a common choice when synchronized access is not needed.
## 4. LinkedList
**Definition:** A `LinkedList` stores elements as linked nodes. It implements the `List` interface and can also be used as a queue or deque.
### Example: Use LinkedList as a List
```javaimport java.util.LinkedList;
public class Main {    public static void main(String[] args) {        LinkedList<String> names = new LinkedList<>();
        names.add("Rahul");        names.add("Priya");        names.add("Aman");
        System.out.println(names);
        names.addFirst("Neha");        names.addLast("Karan");
        System.out.println(names);    }}```
**Output:**```text[Rahul, Priya, Aman][Neha, Rahul, Priya, Aman, Karan]```
**Explanation:**- `add()` appends an element to the list.- `addFirst()` adds an element at the beginning.- `addLast()` adds an element at the end.
### Example: Remove Elements from a LinkedList
```javaimport java.util.LinkedList;
public class Main {    public static void main(String[] args) {        LinkedList<String> tasks = new LinkedList<>();
        tasks.add("Study");        tasks.add("Exercise");        tasks.add("Read");
        tasks.removeFirst();        tasks.removeLast();
        System.out.println(tasks);    }}```
**Output:**```text[Exercise]```
**Explanation:**- `removeFirst()` removes the first element.- `removeLast()` removes the last element.
## 5. ArrayList vs. Vector vs. LinkedList
| Feature | ArrayList | Vector | LinkedList ||---|---|---|---|| Implements `List` | Yes | Yes | Yes || Keeps elements in order | Yes | Yes | Yes || Allows duplicate elements | Yes | Yes | Yes || Resizable | Yes | Yes | Yes || Synchronized methods | No | Yes | No || Useful for | General list operations and accessing elements by index | Situations requiring synchronized collection methods | Frequent additions or removals at the ends |
Choose a collection based on how your program needs to use the data.
## 6. Iterator
**Definition:** An `Iterator` is an object that can visit elements in a collection one at a time.
### Example: Iterate Through an ArrayList
```javaimport java.util.ArrayList;import java.util.Iterator;
public class Main {    public static void main(String[] args) {        ArrayList<String> fruits = new ArrayList<>();
        fruits.add("Apple");        fruits.add("Banana");        fruits.add("Mango");
        Iterator<String> iterator = fruits.iterator();
        while (iterator.hasNext()) {            String fruit = iterator.next();            System.out.println(fruit);        }    }}```
**Output:**```textAppleBananaMango```
**Explanation:**- `iterator()` creates an iterator for the list.- `hasNext()` checks whether another element is available.- `next()` returns the next element.
### Remove an Element with an Iterator
Use `Iterator.remove()` when removing elements while iterating.
```javaimport java.util.ArrayList;import java.util.Iterator;
public class Main {    public static void main(String[] args) {        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(10);        numbers.add(15);        numbers.add(20);        numbers.add(25);
        Iterator<Integer> iterator = numbers.iterator();
        while (iterator.hasNext()) {            int number = iterator.next();
            if (number % 2 != 0) {                iterator.remove();            }        }
        System.out.println(numbers);    }}```
**Output:**```text[10, 20]```
**Explanation:**- The loop checks each number.- `number % 2 != 0` identifies odd numbers.- `iterator.remove()` safely removes the current element during iteration.
## 7. ListIterator
**Definition:** A `ListIterator` is an iterator for lists that can move both forward and backward. It can also add, replace, and remove elements while traversing a list.
### Example: Move Forward and Backward
```javaimport java.util.ArrayList;import java.util.ListIterator;
public class Main {    public static void main(String[] args) {        ArrayList<String> colors = new ArrayList<>();
        colors.add("Red");        colors.add("Green");        colors.add("Blue");
        ListIterator<String> iterator = colors.listIterator();
        System.out.println("Forward:");
        while (iterator.hasNext()) {            System.out.println(iterator.next());        }
        System.out.println("Backward:");
        while (iterator.hasPrevious()) {            System.out.println(iterator.previous());        }    }}```
**Output:**```textForward:RedGreenBlueBackward:BlueGreenRed```
**Explanation:**- `listIterator()` creates a `ListIterator` for the list.- `hasNext()` and `next()` move forward.- `hasPrevious()` and `previous()` move backward.
### Example: Add and Replace Elements with ListIterator
```javaimport java.util.ArrayList;import java.util.ListIterator;
public class Main {    public static void main(String[] args) {        ArrayList<String> names = new ArrayList<>();
        names.add("Rahul");        names.add("Priya");
        ListIterator<String> iterator = names.listIterator();
        while (iterator.hasNext()) {            String name = iterator.next();
            if (name.equals("Rahul")) {                iterator.set("Rohan");            }        }
        iterator.add("Aman");
        System.out.println(names);    }}```
**Output:**```text[Rohan, Priya, Aman]```
**Explanation:**- `set("Rohan")` replaces the last element returned by the iterator.- `add("Aman")` inserts an element at the iterator's current position.- `ListIterator` supports these operations while traversing the list.
## 8. Iterator vs. ListIterator
| Iterator | ListIterator ||---|---|| Works with many collection types. | Works with lists. || Moves forward through elements. | Moves forward and backward. || Can remove the current element. | Can add, replace, and remove elements. || Does not provide the current list index. | Provides methods for checking list positions. |
## 9. Complete Example: Using a List and ListIterator
```javaimport java.util.ArrayList;import java.util.ListIterator;
public class Main {    public static void main(String[] args) {        ArrayList<String> students = new ArrayList<>();
        students.add("Rahul");        students.add("Priya");        students.add("Aman");
        ListIterator<String> iterator = students.listIterator();
        while (iterator.hasNext()) {            String student = iterator.next();
            if (student.equals("Aman")) {                iterator.set("Anaya");            }        }
        iterator.add("Karan");
        System.out.println("Students: " + students);
        System.out.println("Students in reverse order:");
        while (iterator.hasPrevious()) {            System.out.println(iterator.previous());        }    }}```
**Output:**```textStudents: [Rahul, Priya, Anaya, Karan]Students in reverse order:KaranAnayaPriyaRahul```
**Explanation:**1. The `ArrayList` stores the student names in order.2. `ListIterator` visits each name.3. `set("Anaya")` replaces `"Aman"`.4. `add("Karan")` adds a name at the iterator's current position.5. `hasPrevious()` and `previous()` display the list in reverse order.
## 10. Student Practice Tasks
1. Create an `ArrayList` of five city names and display each name.2. Add, replace, and remove elements in an `ArrayList` of integers.3. Create a `Vector` of colors and display its first and last elements.4. Create a `LinkedList` of tasks. Add one task at the beginning and another at the end.5. Use an `Iterator` to display every element in a list.6. Use an `Iterator` to remove all numbers smaller than `10` from a list.7. Use a `ListIterator` to display a list in forward and reverse order.8. Use a `ListIterator` to replace one item and add a new item.
## Class Summary
In this class, you learned:- A **`List`** stores ordered elements and allows duplicates.- An **`ArrayList`** is a resizable list commonly used for general list operations.- A **`Vector`** is a resizable list with synchronized methods.- A **`LinkedList`** stores linked elements and supports operations at both ends.- An **`Iterator`** visits collection elements one at a time.- A **`ListIterator`** can traverse a list in both directions and modify elements while iterating.
