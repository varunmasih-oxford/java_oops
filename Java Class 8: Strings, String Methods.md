# Java Class 8: Strings, String Methods, StringBuffer, and StringTokenizer

## 1. Strings

**Definition:** A `String` is a sequence of characters used to store text. In Java, `String` is a class.

### Example

```java
public class Main {
    public static void main(String[] args) {
        String name = "Rahul";

        System.out.println(name);
    }
}
```

**Output:**
```text
Rahul
```

**Explanation:**
- `String name` declares a variable that can hold text.
- `"Rahul"` is a string literal.
- Strings are immutable, which means their contents cannot be changed after they are created. String operations that appear to change a string create a new string instead.

### String Concatenation

The `+` operator joins strings together.

```java
public class Main {
    public static void main(String[] args) {
        String firstName = "Rahul";
        String lastName = "Sharma";

        String fullName = firstName + " " + lastName;

        System.out.println(fullName);
    }
}
```

**Output:**
```text
Rahul Sharma
```

## 2. Common String Methods

Java provides methods for checking, comparing, and working with strings.

### Example

```java
public class Main {
    public static void main(String[] args) {
        String text = "Hello Java";

        System.out.println("Length: " + text.length());
        System.out.println("Uppercase: " + text.toUpperCase());
        System.out.println("Lowercase: " + text.toLowerCase());
        System.out.println("Character at index 1: " + text.charAt(1));
        System.out.println("Contains Java: " + text.contains("Java"));
    }
}
```

**Output:**
```text
Length: 10
Uppercase: HELLO JAVA
Lowercase: hello java
Character at index 1: e
Contains Java: true
```

**Explanation:**
- `length()` returns the number of characters.
- `toUpperCase()` returns a new string in uppercase.
- `toLowerCase()` returns a new string in lowercase.
- `charAt(index)` returns the character at the given index. Indexes start at `0`.
- `contains(text)` checks whether the string contains the given text.

### More Useful String Methods

| Method | Purpose |
|---|---|
| `equals(other)` | Checks whether two strings have the same contents |
| `equalsIgnoreCase(other)` | Compares strings without considering letter case |
| `trim()` | Removes leading and trailing whitespace |
| `substring(start)` | Returns part of a string from `start` to the end |
| `substring(start, end)` | Returns characters from `start` up to, but not including, `end` |
| `indexOf(text)` | Returns the first index of the text, or `-1` if not found |
| `replace(old, new)` | Returns a string with matching characters or text replaced |
| `startsWith(text)` | Checks whether the string begins with the given text |
| `endsWith(text)` | Checks whether the string ends with the given text |
| `isEmpty()` | Checks whether the string has zero characters |

### Example: Using More String Methods

```java
public class Main {
    public static void main(String[] args) {
        String text = "  Learn Java  ";

        System.out.println("Trimmed: " + text.trim());
        System.out.println("Substring: " + text.substring(2, 7));
        System.out.println("Index of Java: " + text.indexOf("Java"));
        System.out.println("Replaced: " + text.replace("Java", "Python"));
    }
}
```

**Output:**
```text
Trimmed: Learn Java
Substring: Learn
Index of Java: 8
Replaced:   Learn Python
```

### Comparing Strings

Use `equals()` to compare the contents of strings. The `==` operator checks whether two references point to the same object.

```java
public class Main {
    public static void main(String[] args) {
        String first = new String("Java");
        String second = new String("Java");

        System.out.println(first.equals(second));
        System.out.println(first == second);
    }
}
```

**Output:**
```text
true
false
```

**Explanation:**
- `equals()` compares the text inside the strings.
- `==` compares whether the references point to the same object.

## 3. StringBuffer

**Definition:** `StringBuffer` is a class used to create and modify a sequence of characters. Unlike `String`, a `StringBuffer` can be changed without creating a new object for every modification.

### Example

```java
public class Main {
    public static void main(String[] args) {
        StringBuffer message = new StringBuffer("Hello");

        message.append(" Java");
        System.out.println(message);

        message.insert(5, " there");
        System.out.println(message);

        message.replace(0, 5, "Welcome");
        System.out.println(message);
    }
}
```

**Output:**
```text
Hello Java
Hello there Java
Welcome there Java
```

**Explanation:**
- `append(text)` adds text to the end.
- `insert(index, text)` inserts text at a specified index.
- `replace(start, end, text)` replaces characters from `start` up to, but not including, `end`.

### More StringBuffer Methods

| Method | Purpose |
|---|---|
| `delete(start, end)` | Removes characters from `start` up to, but not including, `end` |
| `reverse()` | Reverses the character sequence |
| `length()` | Returns the number of characters |
| `toString()` | Converts the `StringBuffer` to a `String` |

### Example: Delete and Reverse

```java
public class Main {
    public static void main(String[] args) {
        StringBuffer text = new StringBuffer("Java Programming");

        text.delete(4, 16);
        System.out.println(text);

        text.reverse();
        System.out.println(text);
    }
}
```

**Output:**
```text
Java
avaJ
```

**Explanation:**
- `delete(4, 16)` removes characters starting at index `4` up to index `16`.
- `reverse()` reverses the characters in the buffer.

> **Note:** `StringBuffer` is synchronized and safe to use when multiple threads may modify it. For many single-threaded situations, `StringBuilder` is another mutable string option.

## 4. StringTokenizer

**Definition:** `StringTokenizer` breaks a string into smaller pieces called tokens, using delimiter characters such as spaces or commas. It is part of the `java.util` package.

### Example: Split Text Using Spaces

```java
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) {
        String sentence = "Java is easy to learn";
        StringTokenizer tokenizer = new StringTokenizer(sentence);

        while (tokenizer.hasMoreTokens()) {
            System.out.println(tokenizer.nextToken());
        }
    }
}
```

**Output:**
```text
Java
is
easy
to
learn
```

**Explanation:**
- `new StringTokenizer(sentence)` uses whitespace as the default delimiter.
- `hasMoreTokens()` checks whether another token is available.
- `nextToken()` returns the next token.

### Example: Use a Custom Delimiter

```java
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) {
        String data = "apple,banana,orange";
        StringTokenizer tokenizer = new StringTokenizer(data, ",");

        while (tokenizer.hasMoreTokens()) {
            System.out.println(tokenizer.nextToken());
        }
    }
}
```

**Output:**
```text
apple
banana
orange
```

**Explanation:**
- The comma `,` is specified as the delimiter.
- Each part between commas becomes a token.

> **Note:** For many modern string-splitting tasks, Java's `String.split()` method is commonly used. `StringTokenizer` is still useful to learn and may appear in existing code.

## 5. Complete Example: String, StringBuffer, and StringTokenizer

```java
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) {
        String sentence = "Java makes coding fun";

        System.out.println("Original: " + sentence);
        System.out.println("Uppercase: " + sentence.toUpperCase());

        StringBuffer message = new StringBuffer(sentence);
        message.append("!");
        System.out.println("Updated: " + message);

        StringTokenizer tokenizer = new StringTokenizer(sentence);
        System.out.println("Words:");

        while (tokenizer.hasMoreTokens()) {
            System.out.println(tokenizer.nextToken());
        }
    }
}
```

**Output:**
```text
Original: Java makes coding fun
Uppercase: JAVA MAKES CODING FUN
Updated: Java makes coding fun!
Words:
Java
makes
coding
fun
```

**Explanation:**
1. The `String` variable stores the original sentence.
2. `toUpperCase()` returns an uppercase version.
3. `StringBuffer` adds an exclamation mark to the sentence.
4. `StringTokenizer` separates the sentence into words.

## 6. Student Practice Tasks

1. Create a string containing your full name and display its length.
2. Convert a sentence to uppercase and lowercase.
3. Check whether a string contains a specific word.
4. Compare two strings using `equals()` and `equalsIgnoreCase()`.
5. Use `substring()` to display part of a string.
6. Create a `StringBuffer`, append text, and reverse it.
7. Use `StringTokenizer` to separate a comma-separated list of names.
8. Ask the user for a sentence and count its words using `StringTokenizer`.

## Class Summary

In this class, you learned:
- A `String` stores text and is immutable.
- String methods can inspect, compare, and create modified strings.
- `equals()` compares string contents; `==` compares references.
- `StringBuffer` is mutable and provides methods such as `append()`, `insert()`, and `reverse()`.
- `StringTokenizer` separates text into tokens using delimiters.
```
