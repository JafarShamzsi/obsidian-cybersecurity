## Overview

This codebase implements an interpreter for the Lox programming language as described in Robert Nystrom's book "Crafting Interpreters". It's a complete implementation of a tree-walk interpreter that follows these main stages:

1. **Scanning (Lexing)**: Converting source text into tokens
2. **Parsing**: Building an Abstract Syntax Tree (AST) from tokens
3. **Static Analysis**: Resolving variable bindings
4. **Interpretation**: Executing the code

## Core Components

### Tokens and Lexing

- The `Scanner` class breaks source code into tokens
- Each token is represented by the `Token` class
- `TokenType` enum defines all possible token types (keywords, operators, etc.)

```python
# Example of scanning process
scanner = Scanner(source_code)
tokens = scanner.scan_tokens()
```

### Abstract Syntax Tree (AST)

The interpreter builds two main types of syntax trees:

1. **Expressions**: Represent code that produces values
   - `Expr` is the base class for all expressions
   - Subclasses include: `Binary`, `Unary`, `Literal`, `Grouping`, etc.

2. **Statements**: Represent code that performs actions
   - `Stmt` is the base class for all statements
   - Subclasses include: `Expression`, `Print`, `Var`, etc.

### Parser

- The `Parser` class converts tokens into an AST
- Uses recursive descent parsing with methods for each grammar rule
- Handles operator precedence and associativity rules

```python
# Example of parsing process
parser = Parser(tokens)
statements = parser.parse()
```

### Environment & Variable Resolution

- The `Environment` class manages variable scopes and bindings
- `Resolver` performs static analysis for variable resolution
- Environments can be nested to handle lexical scoping

### Interpreter

- The `Interpreter` class evaluates the AST and executes the code
- Uses the Visitor pattern to process each type of AST node
- Handles runtime error detection and reporting

## Execution Flow

1. **Source Code** → Loaded from file
2. **Scanner** → Converts source to tokens
3. **Parser** → Converts tokens to AST
4. **Resolver** → Performs static analysis on AST
5. **Interpreter** → Executes AST

## Key Language Features Implemented

### Variables and Scope

```lox
var x = 10;
{
  var y = 20;
  print x + y; // 30
}
```

- Variables are declared with `var`
- Lexical scoping with block scope
- Variables are dynamically typed

### Control Flow

```lox
if (condition) {
  // then branch
} else {
  // else branch
}

while (condition) {
  // loop body
}

for (var i = 0; i < 10; i = i + 1) {
  // loop body
}
```

### Functions

```lox
fun add(a, b) {
  return a + b;
}

var result = add(5, 3);
```

- Functions are first-class values
- Support for closures (functions that capture their lexical environment)
- Proper lexical scoping for variables

### Classes and OOP

```lox
class Person {
  init(name) {
    this.name = name;
  }

  sayHello() {
    print "Hello, I'm " + this.name;
  }
}

var person = Person("Alice");
person.sayHello();
```

- Classes with methods
- Instance properties
- Constructors via `init()` method
- Support for `this` to reference the current instance

## Visitor Pattern

The interpreter uses the **Visitor Pattern** extensively:

```python
def accept(self, visitor):
    return visitor.visit_binary_expr(self)
```

Each AST node class has an `accept` method that takes a visitor. The visitor then calls the appropriate method to handle that node type.

## Error Handling

- **Syntax Errors**: Detected during scanning/parsing
- **Runtime Errors**: Detected during interpretation
- Error messages include line numbers for easy debugging

## Key Classes in Detail

### Scanner

Responsible for breaking the source code into tokens:

- Tracks current position in source code
- Identifies keywords, identifiers, literals, operators
- Adds tokens to a list which is returned when scanning is complete

### Parser

Implements a recursive descent parser with these key features:

- Each grammar rule is implemented as a method
- Uses lookahead to determine which rule to apply
- Handles operator precedence through method call ordering
- Provides error synchronization for better error recovery

### Environment

Manages variable scopes and binding:

- Stores variable values by name
- Supports nested scopes via enclosing environments
- Provides methods to define, get, and set variables

### Interpreter

Executes the code by visiting each AST node:

- Each node type has a corresponding visit method
- Evaluates expressions to values
- Executes statements for their side effects
- Manages runtime environment state

## Additional Features

### Function Calls

- Function parameters are evaluated before the call
- Arguments are passed by value
- Function environment is created with the closure as its parent

### Class Implementation

- Classes are first-class values
- Methods are stored in the class
- Instances store properties but inherit methods from their class
- `this` is bound to the current instance when a method is called

## Data Structures

- **AST**: Tree representation of the code
- **Environment Chain**: Linked list of environments for variable lookup
- **Resolver Scopes**: Stack of scopes for static analysis

## Running the Interpreter

The interpreter supports different commands:

```bash
./your_program.sh run path/to/script.lox       # Run a Lox script
./your_program.sh tokenize path/to/script.lox  # Show tokens
./your_program.sh parse path/to/script.lox     # Show AST
./your_program.sh evaluate path/to/script.lox  # Evaluate an expression
```

## Conclusion

This implementation follows a clean, modular design that separates concerns:

1. **Lexical analysis** (Scanner)
2. **Syntactic analysis** (Parser)
3. **Static analysis** (Resolver)
4. **Execution** (Interpreter)

Each phase builds on the previous one, creating a complete interpreter pipeline.

[https://github.com/JafarShamzsi/Python-Interpreter]()
