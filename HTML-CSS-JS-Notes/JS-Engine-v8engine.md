# JS Engine

> JS is single threaded non blocking asynchronous concurrent language

> A confusing bit of history is that JavaScript was created in 1996. It was then submitted to Ecma International in 1997 for standardization, which resulted in ECMAScript. At the same time, because JavaScript conformed to the ECMAScript specification, JavaScript is an example of an ECMAScript implementation.

- A JavaScript engine is a program that interprets and executes JavaScript code.

- Basically a translator for the computer between JavaScript and a language that the computer understands.

- It's responsible for parsing, compiling, and executing JavaScript code within a web browser or server environment.

- There are many JavaScript Engines out there and typically they are created by web browser vendors. All engines are standardized by ECMA Script or ES.

[List of ECMAScript engines](https://en.wikipedia.org/wiki/List_of_ECMAScript_engines)

> Examples of popular JavaScript engines include _V8 (used in Chrome and Node.js)_, _SpiderMonkey (used in Firefox), and JavaScriptCore (used in Safari)_. These engines continuously evolve to improve performance, optimize code execution, and support new language features.

## How does JavaScript work?

- JavaScript engine = V8 engine (written in C++)
- JavaScript is a single threaded language that uses a call back queue
- Interpreted language (well it depends on the implementation) _In modern engines, the interpreter starts reading the code line by line while the profiler watches for frequently used code and flags then passes is to the compiler to be optimized._

<details>
    <summary> <b>Interpreter vs Compiler</b> </summary>
  Here's a comparison of interpreters and compilers in Markdown table format:

| Feature      | Interpreter                                               | Compiler                                                        |
| ------------ | --------------------------------------------------------- | --------------------------------------------------------------- |
| Execution    | Interprets code line-by-line at runtime                   | Translates entire code to machine code first, then executes     |
| Speed        | Generally slower due to runtime interpretation            | Generally faster as code is precompiled                         |
| Memory Usage | Lower memory usage since code is not compiled             | Higher memory usage during compilation                          |
| Debugging    | Easier debugging since errors are reported as encountered | Harder debugging since errors may be reported after compilation |
| Portability  | Portable across platforms without recompilation           | Platform-specific binaries may be generated                     |
| Examples     | Python, JavaScript, Ruby                                  | C, C++, Go, Rust                                                |

This table provides a brief comparison between interpreters and compilers in terms of their execution, speed, memory usage, debugging capabilities, portability, and examples of languages that utilize each approach.

#### JavaScript is typically considered an interpreted language,

- as it is executed line-by-line by a JavaScript engine at runtime.
- However, modern JavaScript engines, like V8 (used in Chrome and Node.js), employ a combination of interpretation and compilation techniques to optimize performance.

- Initially, the JavaScript code is parsed and compiled into an intermediate representation, such as bytecode or machine code.

- This compilation step occurs before execution and allows for optimizations like just-in-time (JIT) compilation, where frequently executed code paths are further compiled into highly efficient machine code.

- So while JavaScript is fundamentally an interpreted language, the presence of compilation stages and optimization techniques blurs the line between interpretation and compilation.

</details>

- A JS file just doesn’t work if you try to run it in a computer with CPU it doesn’t understand JS file. That’s where the V8 engine comes to the rescue and helps the CPU to run the JS file.

#### Q. Who created the first JavaScript Engine?

- _Brendan Eich_, an American computer programmer and technology executive.
- He created the JavaScript programming language and co-founded the Mozilla project, the Mozilla Foundation, and the Mozilla Corporation.
- Spider Monkey - which Firefox still uses.
- On 28 May 2015, CEO Brendan Eich and CTO Brian Bondy founded Brave Software.

## V8 Engine

_V8 engine which is the most popular, common and the fastest is used in the chrome and node js is written in C++ (low level language)_

![Image](https://images.ctfassets.net/aq13lwl6616q/3o7Q3edCrVJG9Zzj6VMZ1K/28136a643636dfa04090f3fb5c5467ff/javascript_engine.png)

- In v8 engine, _interpreter is called Ignition_, _compiler = turbofan_.

- When we run a JavaScript file, the code is broken down into tokens; you’ve probably heard the terms lexical analysis, lexing, or Tokenizer.

- Lexical analysis is just the process of breaking down code into tokens based on the meaning of the keyword or what the code is trying to do.

- These “tokens,” as we call them, are then formed into an AST, and there is a fun tool that allows you to view the [AST](https://astexplorer.net/).

#### Parser:

- A Parser or Syntax Parser is a program that reads your code line-by-line.

- It understands how the code fits the syntax defined by the Programming Language and what it (the code) is expected to do.

- Parses JavaScript code and converts it into an abstract syntax tree (AST), which represents the structure of the code.

- _Parsing is the process of analyzing the source code, checking it for errors, and breaking it up into parts._

#### The AST:

- The parser produces a data structure called the Abstract Syntax Tree or AST.

- AST is a tree graph of the source code that does not show every detail of the original syntax, but contains structural or content-related details.
- Certain things are implicit in the tree and do not need to be shown, hence the title abstract.

#### The Interpreter

- An interpreter directly executes each line of code line by line, without requiring them to be compiled into a machine language program.

- Interpreters can use different strategies to increase performance.

- They can parse the source code and execute it immediately, translate it into more efficient machine code, execute precompiled code made by a compiler, or some combination of these.

- In the V8 engine, the interpreter outputs bytecode.

#### The Compiler

- The compiler works ahead of time to convert instructions into a machine-code or lower-level form so that they can be read and executed by a computer.

- It runs all of the code and tries to figure out what the code does and then compiles it down into another language that is easier for the computer to read.

**Have you heard of Babel or TypeScript?**

- They are heavily used in the Javascript ecosystem and you should now have a good idea of what they are.

- Babel is a Javascript compiler that takes your modern JS code and returns browser compatible JS (older JS code).

- Typescript is a superset of Javascript that compiles down to Javascript. Both of these do exactly what compilers do. Take one language and convert into a different one!

#### The Combo = JIT Compiler

- In modern engines, the interpreter starts reading the code line by line while the **profiler** watches for frequently used code and flags then passes is to the compiler to be optimized.

- In the end, the JavaScript engine takes the bytecode the interpreter outputs and mixes in the optimized code the compiler outputs and then gives that to the computer.

- This is called "Just in Time" or JIT Compiler.

## Keywords:

#### Babel:

- Babel is a free and open-source JavaScript transcompiler that is mainly used to convert ECMAScript 2015+ code into backwards-compatible JavaScript code that can be run by older JavaScript engines.
- It allows web developers to take advantage of the newest features of the language.

#### TypeScript:

- TypeScript is a free and open source programming language developed and maintained by Microsoft.
- It is a strict syntactical superset of JavaScript and adds optional static typing to the language.
- It is designed for the development of large applications and transpiles to JavaScript.
