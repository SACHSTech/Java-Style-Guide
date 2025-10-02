# Java Style Guide  
_A reference on house Java coding style for ICS3U and ICS4U students at St. Augustine CHS in Markham, Ontario, Canada._


## Introduction
This document explains how we format and write Java programs in our courses. Consistent style makes code easier to read, debug, and share.  

- ICS3U Students: Use this guide as you begin programming.  
- ICS4U Students: Use this as a refresher and note special conventions when we begin **Object-Oriented Programming (OOP)**.

## Beginning of Your Program

1. **Package statements** should be at the very top of your file.
2. **Import statements** come next.
3. **Program header block comment** should follow, describing the program.
4. **Class declaration** comes last.  
   - Class names must always start with a **capital letter**.  
   - In ICS3U (pre-OOP), you may only work with a single class (often `Main` or extending `ConsoleProgram`).
   - In ICS4U (OOP), you’ll define multiple classes. Follow **PascalCase** (e.g. `StudentRecord`, `BankAccount`).

**Example:**
```java
package unit1;
import codehs.*;

/**
 * A program Hypotenuse.java that lets you enter the two sides
 * of a right angled triangle, and then prints the hypotenuse.
 * @author: D. Cheng
 */
public class Hypotenuse extends ConsoleProgram {
    ...
}
```

## Variables

### Naming Rules
- Must start with a **letter**, `$`, or `_`.  
- The rest may contain **letters, numbers, or `_`**.  
- Cannot contain spaces.  
- Cannot be a Java keyword (e.g. `class`, `int`).  
- Case-sensitive (`firstName` is different than `FirstName`).

### Naming Conventions
- Variables should **start with a lowercase letter**.  
- Use **camelCase** for multi-word names (`firstName`, `orderNumber`).  
- **Be descriptive**: `numberOfCars`, not `n`.  
- Units may be included if meaningful: `distanceKm`, `timeSec`.  
- **Boolean variables** often start with `is`, `has`, or `should` (e.g. `isDone`, `hasValue`).  

**Note:** Some other teaching styles add type prefixes (`intNumApples`, `strUserName`).  
This is **not industry standard** and unnecessary in Java because the type is already declared.  
Instead, focus on **clear, descriptive names**.

✅ **Good:**
```java
int totalBooks;
boolean isOpen;
String userName;
```

❌ **Bad:**
```java
int b;  // too vague
int 6numStudents;  // invalid
int my Score; // contains space
int intNumApples; // prefix is redundant
```

## Commenting

- Use **good names** and structured code to reduce the need for excessive comments.  
- Write comments when something needs explanation.  
- Always put a **space** after `//` or `/**`.  
- Comments should be **indented** with the code they describe.

✅ **Good:**
```java
// This is a comment

/**
 * This is a Javadoc comment
 */
while (true) {
    // Do something
    something();
}
```

❌ **Bad:**
```java
//This is a comment
/**This is a javadoc comment*/
while (true){
// Do something

something();
}
```

## Indentation

- Use **4 spaces** per indentation level (not tab characters).  
  - Most editors (IntelliJ, VS Code) auto-convert tabs to spaces.  
- Indent code inside every `{ }` block.

## Whitespace

### Operators
- **Always surround binary operators with spaces.**
- Use **parentheses** to make order of operations clear.
 
✅ **Good:**
```java
a = b * d;
a = (b + c) * d;
```

❌ **Bad:**
```java
a=b*d;
a=(b+c)*d;
```

### Reserved Words
- Java reserved words should be followed by a space.  

    ✅ `while (true) {`  
    ❌ `while(true){`  

### Commas
- Commas should be followed by a space.  

    ✅ `doSomething(a, b, c, d);`  
    ❌ `doSomething(a,b,c,d);`  

### For Loops
- Semicolons in `for` statements should be followed by a space.  

    ✅ `for (i = 0; i < 10; i++) {`  
    ❌ `for(i=0;i<10;i++){`  

## Logical Paragraphs

Think of your code like writing paragraphs in an essay. Use whitespace to separate different “sections” of logic:  
- Variable declarations  
- User input  
- Processing  
- Output  

✅ **Good Example:**
```java
package unit1.mathproblems;
import codehs.*;

/**
 * A simple program to compute the hypotenuse of a right triangle
 * given the length of two sides
 * @author: E. Fabroa
 */
public class Hypotenuse extends ConsoleProgram {

    public void run() {
        // Declare variables
        double hyp;
        double sideA;
        double sideB;

        // Get side lengths
        sideA = readDouble("Enter the length of the first side: ");
        sideB = readDouble("Enter the length of the second side: ");

        // Use Pythagorean Theorem
        hyp = Math.sqrt(Math.pow(sideA, 2) + Math.pow(sideB, 2));

        // Show result
        System.out.println("The length of the hypotenuse is " + hyp);
    }
}
```

❌ **Bad Example:**
```java
package unit1.mathproblems;
import codehs.*;

/**
 * A simple program to compute the hypotenuse of a right triangle
 * given the length of two sides
 * @author: C. Chen
 */
public class Hypotenuse extends ConsoleProgram {
    public void run() {
        double hyp;
        double sideA;
        double sideB;
        sideA = readDouble("Enter the length of the first side: ");
        sideB = readDouble("Enter the length of the second side: ");
        hyp = Math.sqrt(Math.pow(sideA, 2) + Math.pow(sideB, 2));
        System.out.println("The length of the hypotenuse is " + hyp);
    }
}
```

## Javadocs & Methods
When writing your own methods and classes, you should use **Javadoc comments** immediately above methods to describe what they do.

**Format:**
```java
/**
 * A description of your method
 * @param parameterName description of the parameter
 * @return description of the return value
 * @author Your Name
 */
```

**Example:**
```java
/**
 * Computes the difference between two numbers
 * @param num1 The first number
 * @param num2 The second number
 * @return The difference between num1 and num2
 */
private static int diff(int num1, int num2) {
    return num1 - num2;
}
```
