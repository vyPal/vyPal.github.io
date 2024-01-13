---
title: "Intro to CaffeineC (v1)"
description: An introduction to the basics of the CaffeineC (v1) programming language
date: 2023-12-18T20:08:24+01:00
draft: false
image: cover.png
categories:
  - CaffeineC
tags:
  - programming
  - caffeinec
---

## What is CaffeineC
CaffeineC is a programming language that I made for some reason. Nobody asked for it, and it's not better than other languages (except for python, I don't like python).
Should you still use it? No, probably not. At least, not yet. CaffeineC is in it's early stages of development, it doesn't have many features, and I still have 
no clue what I'm doing.

## What can it do
The short answer is not much. The longer one is that the current version can't do much. It is very limited in terms of working with other files or libraries, 
and doesn't have many built-in ones for that matter. You can basically print stuff to the console and that is it. A newer version is being worked on, 
but it is not yet very stable.

## Some basics
### Defining variables
So as in any good programming language, you can define variables. It is pretty easy in CaffeineC, not as easy as in python maybe, but still pretty easy.
It involves the `var` keyword, followed by a variable name, the variable type, an optional assignment, and a semicolon at the end.

It should look something like this:
```cffc
var a: int = 10;
```
### Using expressions
Most of the CaffeineC programming language syntax is made up of expressions. Any mathematical operation is an expression. Comparisons are expressions. Function calls are 
expressions. In any expresssion there is a left side and a optional right side. Each side can have a constant, variable, function call or some other stuff. So as a basic example, we will just do some basic addition:
```cffc
a = a + 2
```
This example should add 2 to `a` and then save the value to `a`
### Defining functions
Another useful feature is the ability to define functions. Smaller (or bigger) blocks of code, that you need to run multiple times, and you don't want to just copy and paste.
Again, CaffeineC uses a keyword to prefix the function definition, in this case `func`. The only required parts for a function is the keyword and a name for the function.
But arguments and a return type may also be specified.

```cffc
func add(x: int, y:int):int {
  return x + y
}
```
This is a very simple function for adding two numbers together. It is not really necessary, but it is an easy way to show how functions work.
### Built-in functions
To make the programming language somewhat usable, it includes two builtin functions: `print` and `sleep`.

The `print` function takes one argument, which can be a string or a number. This input gets formatted and a newline character gets added to the end.

The `sleep` function also only takes one argument, this time it's the time in **nanoseconds** that the program should sleep for. You can either directly write 
the number of nanoseconds, but that can be lengthy, so I added a `duration` type. This type consists of a number and a suffix. This suffix can be one of: 
`ns`, `us`, `ms`, `s`, `m`, or `h`. The compiler automatically converts this synta to a number in nanoseconds.
## Example program
With the information above, we can construct a simple program:
```cffc
var a:int = 5;
var b:int = 10;

func add(x: int, y:int):int {
  return x + y
}

print add(a, b);
```
This program is very simple, but it demonstrates how the programming language works. If you have used any normal programming language before, you should (hopefully) 
be able to figure out what this program does. If not, idk, learn some other programming language first.

Anyway, save this as `example.caffc`
## Installing the compiler
The easiest way to install the compiler, is to go to [the releases page](https://github.com/vyPal/CaffeineC/releases/tag/v0.0.2) and download either the `.exe` file 
if you are on windows, or the other file if you are on linux. The copy the executable file into the same directory where your `example.caffc` file is, and run:
```bash
./CaffeineC build demo.caffc
```
or if you are on windows:
```bash
./CaffeineC.exe build demo.caffc
```
You should now have a file named `output` or `output.exe` in the same directory, it you run it, it should print `15` in the command line.