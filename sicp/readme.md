# sicp
Structure and Interpretation of Computer Programs

## Overview
A computer science study group that will meet twice a month to work through SICP, MIT's computer science textbook. It takes you from complete beginner to not complete beginner. You start with making a function that squares its input and end with building an interpreter.

The book is in scheme, a stripped down dialect of LISP. It you haven't used LISP before it will look completely new to you, it's very heavy on the parentheses. Don't get caught up in the syntax or the fact that it's not PowerShell or C#. What we learn in this class will make us better programmers across languages and situations.

## Getting started
1. Get a copy of the book, it's available in print from online retailers and also for free online many places because the book is MIT licensed.
   - Originally formatted [SICP at MIT Press](https://mitpress.mit.edu/sicp/full-text/book/book.html)
   - Beautifully formatted in HTML5 with SVG illustrations [SICP HTML5 & SVG ebook](sarabander.github.io/sicp/)
2. Setup your environment
   - At the time of writing this, 2017-12-12, using DrRacket is the easiesty way to support code in Scheme. You should install the DrRacket "IDE" then install the SICP language package with its package manager.
   - [DrRacket](http://racket-lang.org/) is the download location of DrRacket.
   - [Instructions for installing the SICP language](https://docs.racket-lang.org/sicp-manual/)
3. Test your SICP language install **sicp-test.rkt** is in the root of the repo.
```lisp
#lang sicp
(inc 42)
```
Should return 43.

#### Optional - setup VS Code
1. Install extensions
   - **Code Runner** to execute the files
   - **Racket** for syntax highlighting
2. Setup the path for the Racket code runner if needed, my VS Code workspace settings has an example. If you put racket.exe on the path you *probably will not* need to modify this.

## Material