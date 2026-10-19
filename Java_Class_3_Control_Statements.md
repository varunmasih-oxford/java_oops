# Java Class 3: Control Statements

## 1. If-Else Statement

**Definition:** The `if-else` statement runs one block of code when a condition is true and another block when it is false.

### Example: Check Voting Eligibility

```java
public class Main {
    public static void main(String[] args) {
        int age = 20;

        if (age >= 18) {
            System.out.println("Eligible to vote");
        } else {
            System.out.println("Not eligible to vote");
        }
    }
}
```

**Output:**
```text
Eligible to vote
```

## 2. Switch Statement

**Definition:** The `switch` statement selects one option from multiple cases.

### Example: Display a Day

```java
public class Main {
    public static void main(String[] args) {
        int day = 2;

        switch (day) {
            case 1:
                System.out.println("Monday");
                break;
            case 2:
                System.out.println("Tuesday");
                break;
            case 3:
                System.out.println("Wednesday");
                break;
            default:
                System.out.println("Invalid day");
        }
    }
}
```

**Output:**
```text
Tuesday
```

- `case` defines an option.
- `break` stops execution from continuing into the next case.
- `default` runs when no case matches.

## 3. For Loop

**Definition:** A `for` loop repeats code, usually when the number of repetitions is known.

### Example: Print Numbers from 1 to 5

```java
public class Main {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.println(i);
        }
    }
}
```

**Output:**
```text
1
2
3
4
5
```

- `int i = 1` sets the starting value.
- `i <= 5` is the condition.
- `i++` increases `i` by 1 after each iteration.

## 4. While Loop

**Definition:** A `while` loop repeats code as long as its condition is true. The condition is checked before the loop body runs.

### Example: Print Numbers from 1 to 5

```java
public class Main {
    public static void main(String[] args) {
        int i = 1;

        while (i <= 5) {
            System.out.println(i);
            i++;
        }
    }
}
```

**Output:**
```text
1
2
3
4
5
```

**Important:** Update `i` inside the loop. Otherwise, the condition may stay true and create an infinite loop.

## 5. Do-While Loop

**Definition:** A `do-while` loop runs the code first and checks the condition afterward. Therefore, it always runs at least once.

### Example: Print Numbers from 1 to 5

```java
public class Main {
    public static void main(String[] args) {
        int i = 1;

        do {
            System.out.println(i);
            i++;
        } while (i <= 5);
    }
}
```

**Output:**
```text
1
2
3
4
5
```

**Key Difference:**
- `while`: checks the condition before running the code.
- `do-while`: runs the code once before checking the condition.

## 6. Practical Program: Marks Grading

**Problem:** Display a grade based on marks out of 100.

```java
public class Main {
    public static void main(String[] args) {
        int marks = 85;

        if (marks < 0 || marks > 100) {
            System.out.println("Invalid marks");
        } else if (marks >= 90) {
            System.out.println("Grade A+");
        } else if (marks >= 80) {
            System.out.println("Grade A");
        } else if (marks >= 70) {
            System.out.println("Grade B");
        } else if (marks >= 60) {
            System.out.println("Grade C");
        } else if (marks >= 40) {
            System.out.println("Grade D");
        } else {
            System.out.println("Fail");
        }
    }
}
```

**Output for `marks = 85`:**
```text
Grade A
```

The program checks conditions from top to bottom and runs the first matching block.

## 7. Practical Program: Multiplication Table

**Problem:** Print the multiplication table of 5 from 1 to 10.

```java
public class Main {
    public static void main(String[] args) {
        int num = 5;

        for (int i = 1; i <= 10; i++) {
            System.out.println(num + " x " + i + " = " + (num * i));
        }
    }
}
```

**Output:**
```text
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
5 x 10 = 50
```

## 8. Student Practice Tasks

1. Use `if-else` to check whether a number is even or odd.
2. Use `switch` to display a message for a number from 1 to 7.
3. Use a `for` loop to print numbers from 10 down to 1.
4. Use a `while` loop to print the multiplication table of 7.
5. Use a `do-while` loop to print numbers from 1 to 5.
6. Create a marks-grading program that checks different marks.
7. Print the multiplication table of a number stored in a variable.

## Class Summary

In this class, you learned:
- `if-else` for decision-making.
- `switch` for selecting between multiple cases.
- `for`, `while`, and `do-while` loops for repetition.
- How to build a marks-grading program.
- How to print a multiplication table.
