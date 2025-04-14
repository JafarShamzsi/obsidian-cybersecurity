All high-level languages need to be converted to machine code so that the computer can understand the program after taking the required inputs. The software by which the conversion of the high-level instructions is performed line-by-line to machine-level language, other than compiler and assembler, is known as **INTERPRETER**.

==Like in Python you have interpreter that’s why you can just run it after u build it, but in java or C you have compiler because after u write the code you need to compile it before running the code and if the compiling gives and error it won’t run.==

The interpreter in the compiler checks the source code line-by-line and if an error is found on any line, it stops the execution until the error is resolved. Error correction is quite easy for the interpreter as the interpreter provides a line-by-line error.  But the program takes more time to complete the execution successfully. Interpreters were first used in 1952 to ease programming within the limitations of computers at the time. It translates source code into some efficient intermediate representation and executes them immediately.

==so Python is the Interpreted language that’s why when u run it, the code will run line by line not all in once. What that means is if u have a error in line 12 but your code is let’s say 30 line long when it comes to the line 12 it will stop i won’t go after that, you need to fix that error first for the interpreter to go beyond that when it runs==

![[Pasted image 20250315123224.png]]
==This is how the interpreter works. It takes the code you wrote in high level language (Python is a High level language) and it translates it to the machine level that so it can run.==

Source programs are compiled before time and stored as machine-independent code, which is then linked at run-time and executed by an interpreter. An Interpreter is generally used in micro-computers. It helps the programmer to find out the errors and to correct them before the control moves to the next statement. The interpreter system performs the actions described by the high-level program. For interpreted programs, the source code is needed to run the program every time. Interpreted programs run slower than the compiled programs.

**Self-Interpreter** is a programming language interpreter which is written in a language that can interpret itself.

==**Self-Interpreter** is a interpreter that is written for the language in the same language itself. Let’s say we write a Python interpreter in the Python language. This helps to develop and the bootstrap the language. New versions of the language can be developed inside of the language itself.==
Self-interpreters are significant in the study of language design and implementation, as they provide a way to reflect on the language's structure and behavior within the language itself.

## Need for an Interpreter

The first and vital need of an interpreter is to translate source code from high-level language to machine language. However, we already had [the compiler](https://www.geeksforgeeks.org/introduction-of-compiler-design/) to serve the purpose, the compiler is a very powerful tool for developing programs in a high-level language. However, there are several demerits associated with the compiler. If the source code is huge in size, then it might take hours to compile the source code, which will significantly increase the compilation duration. Here, the Interpreter plays its role. The interpreter can cut this huge compilation duration. As they are designed to translate single instruction at a time and execute them immediately. So instead of waiting for the entire code, the interpreter translates a single line and executes it.