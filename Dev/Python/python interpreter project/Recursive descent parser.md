In Computer Science, a recursive descent parser is a kind of top-down parser built from a set of mutually recursive procedures (or non-recursive equivalent) where each suck procedure implements one of the nonterminals of the grammar. Thus structure of the resulting program closely mirrors that of the grammar it recognizes.

### **What is a Recursive Descent Parser?**

A **recursive descent parser** is a type of **top-down parser** that breaks down input (like a mathematical expression or a programming statement) into smaller parts using **recursive functions**.

It is called "recursive descent" because:

1. It starts **from the top** (the main rule) and **goes down** step by step.
2. It calls **functions recursively** to process the smaller parts of the input.

This kind of parser is used to **analyze and understand structured text**, like source code or mathematical expressions.

### **How Does It Work?**

Think of parsing as **reading a sentence** while following grammar rules.
For example, let's say we have this **simple math expression**:

```2 + 3 * 4```

And we have a basic **grammar rule** that says:
- A **sum** is made of numbers added or subtracted.
- A **term** is made of numbers multiplied or divided.
- A **number** is just a number.

A **recursive descent parser** follows these rules **step by step**, calling itself when needed.
### **Step-by-Step Breakdown**

Let’s define the grammar:

```
Expression -> Term ( ("+" | "-") Term )*
Term       -> Factor ( ("*" | "/") Factor )*
Factor     -> Number | "(" Expression ")"
```

- An **Expression** consists of **Terms** combined with `+` or `-`.
- A **Term** consists of **Factors** combined with `*` or `/`.
- A **Factor** is either a **Number** or an **Expression inside parentheses**.