<!---
{
  "id": "7130a694-458e-4e24-80b7-d8673f765e69",
  "teaches": "Two ways to run python",
  "depends_on": [],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-07",
  "keywords": ["python", "REPL"]
}
--->

# Two ways to run python

## Introduction
Python is a script interpreter that can be used in several distinct ways, each with its own strengths and applications. In this exercise, we explore how Python can be run and what its specific use cases are.

Python was originally designed by **Guido van Rossum** as a cleaner alternative to shell scripts, especially `bash`. Over the years, Python has become a standard tool available on most Linux distributions and has been widely adopted for tasks ranging from system administration to scientific computing and web development.

When we talk about "running Python," we must remember that ultimately, all code is translated into **binary instructions** executed by the CPU. These are often packaged into **libraries**, many of which are written in C and compiled into native binaries. For instance, the Python `print` function internally calls a low-level system routine that is part of such a precompiled library.

Script interpreters like Python excel at **gluing together** such system libraries into more complex applications. As Python programmers, our task is to orchestrate these library calls correctly.

This brings us to three principal ways to run Python:

1. **Interactively** (e.g. via REPL)
2. **As a Script File**
3. **Embedded in a Webpage** (e.g. via PyScript) -- not part of this exercise

Understanding these methods helps us use Python effectively across platforms.


### Further Readings and Other Sources
- [A Byte of Python (Free Book)](https://python.swaroopch.com/)
- [Official Python Tutorial](https://docs.python.org/3/tutorial/index.html)
- [Real Python (Practice-Based Learning)](https://realpython.com/)

## Tasks
1. **Install python**:  If you haven't done it, check whether python is installed on your system. Open a new terminal and run `python3 --version`. The output should tell you, whether python is installed or not. If you run Linux, python should be already installed. If you are running windows, you might have to install it. Go to [python.org](https://www.python.org/downloads/windows/), download the latest version of python3, install it and restart your computer.

2. **Interactive**: In your already opened terminal, type `python3` and hit enter. This will open the Python3-REPL. REPL stands for Read-Evaluate-Print-Loop, which is an acronym to describe this terminal-shell like behavior. 
You can now interactively prompt your machine, to perform certain tasks. Let's calculate the sum of all numbers between 1 and 100. Type:

```python3
gaussian_sum = sum( x for x in range(1,101))
print(gassuan_sum)
```

Make sure to type `101` as the upper limit, since the upper limit is not included in pythons `range()` function!

3. **Built Ins**: In order to figure out, which commands you can use without loading a library by running 
```python3
>>> dir(__builtins__)
```
The python interactive interface also features `tab`-complete as you know it from your terminal.
By the way, you can find a cheat-sheet of all `python3` built-ins in [./assets/built_ins.md](assets/built_ins.md).


4. **Loading a library**: In order to load a library you can use the `import` statement. Let's take the `os`-library as an example and use a command from it:
```python3
>>> import os
>>> os.getcwd()
>>> os.chdir('..')
>>> os.listdir()
```

Exit your interactive `python`-Interpreter by typing:
```python3
>>> exit()
```

Using the interactive version can be really helpful, especially for prototyping. If you want to dive more into it, look at these two exercises and learn more about running python interactively or even in a web-interface called _JuPyter_: 
* [Interactive Python](github.com/STEMgraph/missing)
* [JuPyter](github.com/STEMgraph/missing)

5. **Running Python as a Script**: When you figured out how to use python to prototype, you will also want to store certain procedures in a file, just as we already did in the [bash-examples](github.com/STEMgraph/missing). Create a new directory for these python files and jump into it:
```bash
mkdir  ~/python_files && cd ~/python_files
```
Now let's put our function from earlier into that file. [Open the file with `vim`](https://github.com/STEMgraph/2c7334b3-b07d-48d6-a562-79072d8e166e), call it `gaussian.py` and fill the following in and make sure, that you use one `tab`-character as an indent for all lines after the _if-main_-part:
```python3
if __name__ == "__main__":
  gaussian_sum = sum( x for x in range(1,101))
  print(gaussian_sum)
```
Save and close the file with `:wq`. 
Without opening an interactive terminal, you can now simply write:
```bash
python3 gaussian.py
```
Your program will run to completion and then end itself.

6. **Shebang! - Linux Only**: You can simplify calling your program by adding the [execution permissions](https://github.com/STEMgraph/be5c2a4a-756f-4303-961c-e616e0cdab11) and adding a shebang. A shebang is a line at the beginning of a program, that tells your execution environment what interpreter the following script should be launched with. You can do that by adding the path of the interpreter to the first line of your program and then add the execution permissions. Here are the three steps to take:
* Run `which python3` this returns the path under which your python-interpreter can be found
* Add `#!<path>` as the first line of your program, where `<path>` is the return-value of the previous expression. E.g.: `#!/usr/bin/python3.11`
* Print the content of the directory in which your python script is located using `ls`. Take a look at the permissions in the first column. Now run `chmod +x my_python_program.py`. Run `ls` again and observe the change in the first column. 
You successfully added a shebang and the permissions. Now run your python-script by simply typing: `./my_python_program.py`, or call the `realpath` of the program.

## Questions

1. What does REPL stand for, and why is it useful?
2. Why does `range(1, 101)` include 100 but not 101?
3. What happens when you call `print()` in Python? What's executed under the hood?
4. What is the role of `__name__ == "__main__"` in a script?
5. How does a shebang line help in Linux environments?
6. What's the difference between importing a library and accessing a built-in?


## Advice

Use the **interactive mode** when you're experimenting or prototyping. It's perfect for testing small pieces of logic quickly. When things become more structured or repetitive, start saving your code into scripts. 

The transition from REPL to script is a crucial step in your learning path—embrace it early.

Also: don't copy-paste blindly. Type it out. It will train your fingers and brain.
