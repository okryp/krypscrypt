# Krypscrypt (KS)

This document is to describe the basic blueprint for this scripting language. It
may change as the language comes into fruition, however the baseline will remain
 as is.

## Main inpsirations

This language will be inspired by my goto favourite programming languages, and 
will include (what are in my opinion) their best features.

The programming languages in question will be:
- C
- Lua
- Ruby
- Python

## Feature Set

### Types

Krypscrypt is a language that includes the classic C types ( int, float, char ), 
 with the addition of the boolean type.

Example:
```
int i = 10;
bool b = true;
float f = 3.14;
char c = "strings!"; 
```

Types are declared before the name of a variable, however they are not 
mandatory, as the interpreter will automatically asign a type to a variable if 
not set by the user.

Example:
```
i = 10;
b = true;
f = 3.14;
c = "strings!";
```

#### Strings

Strings are nothing more than an array of characters, and will be treated the 
same as in C.

#### Integers and Floating point numbers

Due to Krypscrypt not being a low level language, there will be no specifying 
between unsigned and signed integers and floats.

### Functions

Krypscrypt allows the user to write functions like any good programming language
 lets you. Functions can be declared to return something using the `return` 
 keyword. Function return types can be declared by putting the return type 
 before the declaration of the function with the `fn` keyword.

Example:
```
    // No return type declared:
    fn addition(int a, int b) {
        return (a + b);

    }

    // Return types declared
    int fn addition(int a, int b) {
        return (a + b);
    }

    /**
    *   Both will return the exact same result, but one is more verbose, and 
    *   will never return a type different than what is declared.
    */

    int fn wrong(){
        return false; // WILL RESULT IN AN ERROR
    }
```

#### Comments

As seen in the codeblock above, comments are declared by `//` and multiline 
comments are declared with `/* */` (the asterisks at the beginning of each 
comment line is my preffered way of doing it)

#### Semicolons
Semicolons are not mandatory, but they do make the code read better :V

It won't downright give you a BRIGHT RED error looking semicolon like python, 
but rest easy knowing that they are not mandatory.

### Loops and recursion

For and while loops are the only loops you will ever need in your life.

Both declared with their respective `for` and `while` keywords.

Example:

```
    // For loop attributes are separated by semicolons just like in C
    
    // Example of automatic typecasting due to lack of type keyword.
    for (i = 0; i < 10; i++) {
        print("${i}\n");
    }

    // Expected result: 10 lines printing each number from 0 to 9;

    int i = 0;
    while (i != 10) {
        print("${i}\n);
        i += 1;
    }

    // Expected result: 10 lines printing each number from 0 to 9;

    /*
    *   Just like in bash, you can use $_ to refer to the last used variable 
    *   when using recursive functions such as in the example below
    */

    int i = 0;
    
    int fn checkValue(int a) {
        if (a != 10) {
            print("${a}\n");
            checkValue($_);
        }

        print("Value is already 10");
        return 0;
    }

    checkValue(i);
```

#### Variables in strings

If you wish to include a variable in a string such as in the examples above, you
 can use the `${varName}` syntax.

### If/else

If/else blocks are opened by the `if` keyword, and `else` to use as a fallback 
of sorts.

Elif is not included in the language, however it does include the

### Switch

Switch statements are declared by the `switch` keyword, the switch statement 
includes cases declared with `case`, and the `default`, keyword for a fallback 
if none of the cases occurs (Not mandatory, but advised). There is no `break`
keyword because if a switch case is reached, it shouldn't just keep going if it 
it already reached it's case.

Example:

```
    int temperature = 10;
    switch (temperature) {
        case 0 {
            print("It's hella COLD");
        }

        case 10 {
            print("It's unpleasant");
        }

        case 20 {
            print("It's nice and pleasant");
        }

        default {
            print("Case unknown");
        }
    }

    // Expected result: It's unpleasant
```

### Struct

The closest thing to OOP in krypscrypt you will ever see, are structs. The 
`struct` keyword will allow the user to create variables with multiple values 
attatched to unique keys.

Example:

```
    struct Person {
        char name,
        int age
    }

    Person Olaf = {"Olaf", 20};
```

Note how unlike in C, krypscrypt does not make use of typedefs for structs. 
Moreso familiar to classes in other programming languages, but missing the 
`this` keyword.

### Other built-in features

#### print()

`print()` is a builtin function that prints whatever you put into it out in the
standard output.

#### Bitwise Operators

The bitwise operators are included for people who prefer doing math with them,
such as low level programmers.

```
    Keywords availible are:
    NOT, AND, OR, NAND, NOR, XOR, XNOR

    These can be also represented by:
    !!, &&, ||. !&, !|, ^, ^!

    Also included are bitwise right, and bitwise left shifts:
    >>, <<
```

The symbols above are not to be confused with the keywords `not`, `and` and, 
`or`. These keywords are specifically used for comparison between values. These 
can also be represented with their own shortcut symbols:
```
    not = !,
    and = &,
    or = |,

    smaller than = >
    larger than = <
    smaller or equal to = <=
    larger or equal to = >=
    equal to = ==

    THERE WILL BE NO RANDOM TRUTYNESS LIKE IN JAVASCRIPT
```

#### Ternary operator

The ternary operator (`?`) can be used to shorten down an if/else block into a
one-liner. Most often used when using an if/else block to decide what to return;

Example:

```
    int fn checkValue(int a, int b) {
        return a > b ? a , b;
    }

    Code above will return a if it is larger than b, and vice versa
```
---
**More Features to be added in the future after discussions**

---
