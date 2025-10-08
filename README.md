# Java Style Guide  

Code style conventions often differ depending on the organization, team, or codebase you’re working in. Professional developers are expected to observe and respect the conventions of the project they join, even if they personally prefer a different style.

Here at St. Augustine CHS, this guide will define our standard. Follow it consistently so your code looks professional, readable, and familiar to anyone else in the class.

- ICS3U Students: Use this guide as you begin programming.  
- ICS4U Students: Use this as a refresher and note special conventions when we begin *Object-Oriented Programming (OOP)*.

## Table of Contents

<!-- vscode-markdown-toc -->
* [Beginning of Your Program](#BeginningofYourProgram)
* [Variables](#Variables)
	* [Naming Rules](#NamingRules)
	* [Naming Conventions](#NamingConventions)
* [Commenting](#Commenting)
	* [When to Use Comments](#WhentoUseComments)
		* [Block comments](#Blockcomments)
		* [Inline comments](#Inlinecomments)
* [Spacing & Alignment of Inline Comments](#SpacingAlignmentofInlineComments)
	* [Exception: Aligned inline comments](#Exception)
	* [Cleanliness and Spacing](#CleanlinessandSpacing)
* [Indentation](#Indentation)
* [Whitespace](#Whitespace)
	* [Operators](#Operators)
	* [Reserved Words](#ReservedWords)
	* [Commas](#Commas)
	* [For Loops](#ForLoops)
* [Logical Paragraphs](#LogicalParagraphs)
* [Javadocs & Methods](#JavadocsMethods)
	* [When to Use Javadoc vs Regular Comments](#WhentoUseJavadocvsRegularComments)
		* [Simple Methods and Helper Functions](#SimpleMethodsandHelperFunctions)
		* [Intermediate Methods and Helper Functions](#IntermediateMethodsandHelperFunctions)
		* [Advanced: Object-Oriented Programming](#Advanced:Object-OrientedProgramming)

<!-- vscode-markdown-toc-config
	numbering=false
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->


<br><br>
## <a name='BeginningofYourProgram'></a>Beginning of Your Program

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

<br><br>
## <a name='Variables'></a>Variables

### <a name='NamingRules'></a>Naming Rules
- Must start with a **letter**, `$`, or `_`.  
- The rest may contain **letters, numbers, or `_`**.  
- Cannot contain spaces.  
- Cannot be a Java keyword (e.g. `class`, `int`).  
- Case-sensitive (`firstName` is different than `FirstName`).

### <a name='NamingConventions'></a>Naming Conventions
- Variables should **start with a lowercase letter**.  
- Use **camelCase** for multi-word names (`firstName`, `orderNumber`).  
- **Be descriptive**: `numberOfCars`, not `n`.  
- Units may be included if meaningful: `distanceKm`, `timeSec`.  
- **Boolean variables** often start with `is`, `has`, or `should` (e.g. `isDone`, `hasValue`).  

**Note:** Some style guides suggest adding type prefixes to variable names, e.g.`intNumApples`, `strUserName`. For this style guide, we **will not use these prefixes**. Instead, focus on **clear, descriptive names** and use your IDE's *mouse-hover* feature to reveal more information about a variable's data type.

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

<br><br>
## <a name='Commenting'></a>Commenting

- Use **good names** and structured code to reduce the need for excessive comments.  
- Write comments when something needs explanation.  
- Always put a **space** after `//` or `/**`.  
- Comments should be **indented** with the code they describe.  
- Avoid leaving large blocks of commented-out code or random extra blank lines — clean, compact files are easier to read and mark.

### <a name='WhentoUseComments'></a>When to Use Comments

#### <a name='Blockcomments'></a>Block comments  
Use a **block-style `//` comment** above a logical group of lines to describe their overall purpose.  
This helps the reader understand what that *section* of code is doing.

✅ **Example:**
```java
// Draw roof of house
fill(230, 173, 16);
triangle(200, 400, 300, 300, 400, 400);
```

```java
// Read user input for both sides of the triangle
sideA = readDouble("Enter the first side: ");
sideB = readDouble("Enter the second side: ");
```

Avoid repeating the obvious (`// Set fill colour` when the line already says `fill(...)`).  
Comments should add *meaning*, not noise.

#### <a name='Inlinecomments'></a>Inline comments  
Use **inline comments** at the end of a line for short explanations of something that isn’t immediately obvious. For example, use an inline comment to explain a tricky formula, algorithm, or workaround.

✅ **Example:**
```java
double force = mass * Math.pow(velocity, 2) / radius;  // centripetal force formula
```

❌ **Bad:**
```java
double force = mass * Math.pow(velocity, 2) / radius;  // calculate force
```
The latter example adds no new information.

<br><br>
### <a name='SpacingAlignmentofInlineComments'></a>Spacing & Alignment of Inline Comments
Leave **two spaces** between the semicolon (or end of the statement) and the start of an inline `//` comment. One space to the comment text itself.

✅ **Good:**
```java
int area = width * height;  // Calculate rectangle area
```

❌ **Bad:**
```java
int area = width * height;//Calculate rectangle area
int area = width * height; //Calculate rectangle area
```

#### <a name='Exception'></a>Exception: Aligned inline comments
While the general rule is to use **two spaces** between the end of a statement (semicolon) and the start of an inline `//` comment, you may deviate from this rule to improve readability. Aligning inline comments across related lines of code can make patterns clearer and help others scan your code more easily.

#### <a name='WhenAlignmentHelps'></a>When Alignment Helps
You should align inline comments **only** within small, related sections of code such as a group of variable declarations, configuration lines, or constants. Do not try to maintain alignment across unrelated code blocks or separate logical sections.

✅ **Good Example (Aligned Inline Comments)**
```java
int x = 100;           // X-position of player
int y = 250;           // Y-position of player
int width = 50;        // Player width
int height = 80;       // Player height
double velocity = 3.5; // Movement speed in pixels/frame
```

✅ **Acceptable Example (Alignment Within Block, Standard Elsewhere)**
```java
// Player stats
int score = 0;          // Player's total score
int lives = 3;          // Remaining lives
boolean isAlive = true; // Player state

System.out.println("Game start!");  // Initialize output
```

### <a name='CleanlinessandSpacing'></a>Cleanliness and Spacing
- Keep comments **close** to the code they describe.  
- Remove any unused or outdated comments before submitting.  
- Avoid **extra blank lines** at the end of files or between unrelated comments and code — they make the program look unfinished.

✅ **Good:**
```java
// Draw windows
rect(220, 420, 50, 50);
rect(330, 420, 50, 50);
```

❌ **Bad:**
```java
// Draw windows


rect(220, 420, 50, 50);
rect(330, 420, 50, 50);

```

<br><br>
## <a name='Indentation'></a>Indentation
Consistent indentation makes your code easier to read and understand by visually showing the structure and flow of logic.
- Use **4 spaces** per indentation level (not tab characters).  
  - Most editors (IntelliJ, VS Code) auto-convert tabs to spaces.  
- Indent code inside every `{ }` block.

<br><br>
## <a name='Whitespace'></a>Whitespace
Thoughtful use of whitespace improves readability by separating logical sections of code and preventing lines from feeling crowded or cluttered.

<br><br>
### <a name='Operators'></a>Operators
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

### <a name='ReservedWords'></a>Reserved Words
- Java reserved words should be followed by a space.  

    ✅ `while (true) {`  
    ❌ `while(true){`  

### <a name='Commas'></a>Commas
- Commas should be followed by a space.  

    ✅ `doSomething(a, b, c, d);`  
    ❌ `doSomething(a,b,c,d);`  

### <a name='ForLoops'></a>For Loops
- Semicolons in `for` statements should be followed by a space.  

    ✅ `for (i = 0; i < 10; i++) {`  
    ❌ `for(i=0;i<10;i++){`  

<br><br>
## <a name='LogicalParagraphs'></a>Logical Paragraphs

Think of your code like writing paragraphs in an essay. Use whitespace to separate different “sections” of logic:  
- Variable declarations  
- User input  
- Processing  
- Output  

✅ **Good Example:**
```java
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
/**
 * A simple program to compute the hypotenuse of a right triangle
 * given the length of two sides
 * @author: C. Chen
 */
public class Hypotenuse extends ConsoleProgram {
    public void run() {
        double hyp, sideA, sideB;
        sideA = readDouble("Enter the length of the first side: ");
        sideB = readDouble("Enter the length of the second side: ");
        hyp = Math.sqrt(Math.pow(sideA, 2) + Math.pow(sideB, 2));
        System.out.println("The length of the hypotenuse is " + hyp);
    }
}
```

<br><br>
## <a name='JavadocsMethods'></a>Javadocs & Methods
When writing your own methods and classes, use **Javadoc comments** immediately above methods to describe what they do.

### <a name='WhentoUseJavadocvsRegularComments'></a>When to Use Javadoc vs Regular Comments

Not every method needs a full Javadoc block. The goal is to make code clear, not cluttered. As you move from **ICS3U (introductory programming)** to **ICS4U (object-oriented design)**, the level of documentation should evolve too.

#### <a name='SimpleMethodsandHelperFunctions'></a>Simple Methods and Helper Functions
At the beginning of ICS3U, we're mostly writing short, single-purpose helper methods such as:
```java
public void drawTree() { ... }
public void drawHouse() { ... }
```
These are straightforward, descriptive by name, and don’t take parameters or return values.  
In this case, a **single-line `//` comment** above the method is enough:

✅ **Example:**
```java
// Draws a tree using rectangles and ellipses
public void drawTree() {
    rect(200, 400, 20, 80);
    ellipse(210, 360, 80, 80);
}
```

You don’t need a full Javadoc comment for these. The method name and a short description make the intent clear. 

#### <a name='IntermediateMethodsandHelperFunctions'></a>Intermediate Methods and Helper Functions
Save full Javadoc format for more complex cases, such as when your method:
- Takes one or more parameters, or
- Performs logic that isn’t obvious from its name.

✅ **Example:**
```java
/**
 * Draws a sun at a given position
 * @param x The x-coordinate of the sun’s centre
 * @param y The y-coordinate of the sun’s centre
 */
public void drawSun(float x, float y) {
    fill(255, 204, 0);
    ellipse(x, y, 80, 80);
}
```

#### <a name='Advanced:Object-OrientedProgramming'></a>Advanced: Object-Oriented Programming
By Grade 12, you’re writing code that defines *classes* and *methods* others might reuse — just like real-world software. In this case, **all public methods and classes must use Javadoc comments**, including:
- Each class definition
- Each method that accepts parameters or returns a value
- Each method that performs complex logic or has side effects

✅ **Example:**
```java
/**
 * Represents a bank account that can deposit and withdraw money.
 */
public class BankAccount {
    private double balance;

    /**
     * Deposits money into the account.
     * @param amount The amount to deposit
     */
    public void deposit(double amount) {
        balance += amount;
    }

    /**
     * Gets the current balance.
     * @return The account balance
     */
    public double getBalance() {
        return balance;
    }
}
```