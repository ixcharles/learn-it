
# Intermediate Bash Commands and Scripting Concepts

This course explores intermediate Bash commands and scripting concepts, expanding your knowledge to write more complex and efficient shell scripts. Mastery of these concepts will enable automation, conditional logic, and effective process management within Bash scripts.

## Table of Contents
1. [Understanding Bash Shell Scripting](#understanding-bash-shell-scripting)
2. [Variables and Data Types in Bash](#variables-and-data-types-in-bash)
3. [Conditionals (if, elif, else)](#conditionals-if-elif-else)
4. [Loops (for, while, until)](#loops-for-while-until)
5. [Functions and Arguments in Bash Scripts](#functions-and-arguments-in-bash-scripts)
6. [Handling Input and Output in Scripts](#handling-input-and-output-in-scripts)
7. [File Test Operators](#file-test-operators)
8. [Redirecting Output and Errors](#redirecting-output-and-errors)
9. [Creating and Using Custom Bash Aliases](#creating-and-using-custom-bash-aliases)
10. [Job Control and Background Processes](#job-control-and-background-processes)

## 1. Understanding Bash Shell Scripting
- **Definition**: Bash scripting is a way to automate tasks by writing a series of commands in a text file that the shell can execute.
- **Example**: A basic script to print "Hello, World":
  ```bash
  #!/bin/bash
  echo "Hello, World"
  ```
- **Explanation**: The first line `#!/bin/bash` specifies the interpreter, and the script executes the command `echo` to display text.

## 2. Variables and Data Types in Bash
- **Definition**: Bash allows the use of variables to store data, and while Bash is untyped, variables can hold strings, integers, or arrays.
- **Example**:
  ```bash
  name="Alice"
  age=25
  echo "Name: $name, Age: $age"
  ```
- **Explanation**: Variables are created without a type declaration and referenced using `$`.

## 3. Conditionals (if, elif, else)
- **Definition**: Conditionals allow for branching logic based on boolean tests.
- **Example**:
  ```bash
  if [ $age -ge 18 ]; then
    echo "Adult"
  else
    echo "Minor"
  fi
  ```
- **Explanation**: The `if` statement checks conditions; `-ge` is used to check if the age is greater than or equal to 18.

## 4. Loops (for, while, until)
- **Definition**: Loops allow repeating tasks multiple times.
- **Example**:
  - **For loop**: 
    ```bash
    for i in {1..5}; do
      echo "Number $i"
    done
    ```
  - **While loop**:
    ```bash
    count=1
    while [ $count -le 5 ]; do
      echo "Count $count"
      ((count++))
    done
    ```
- **Explanation**: The `for` loop iterates through a range, and the `while` loop runs while a condition is true.

## 5. Functions and Arguments in Bash Scripts
- **Definition**: Functions allow for modular scripting and reusing code.
- **Example**:
  ```bash
  greet() {
    echo "Hello, $1!"
  }
  greet Alice
  ```
- **Explanation**: `$1` refers to the first argument passed to the function.

## 6. Handling Input and Output in Scripts
- **Definition**: Bash provides mechanisms to interact with the user and handle output.
- **Example**:
  - **Input**:
    ```bash
    read -p "Enter your name: " name
    echo "Hello, $name"
    ```
  - **Output**: 
    ```bash
    printf "Hello, %s!\n" "$name"
    ```
- **Explanation**: `read` takes user input, and `echo` or `printf` outputs data.

## 7. File Test Operators
- **Definition**: File test operators check the attributes of files or directories.
- **Example**:
  ```bash
  if [ -f "file.txt" ]; then
    echo "File exists"
  fi
  ```
- **Explanation**: The `-f` checks if the file exists and is a regular file. Other operators include `-d`, `-r`, `-w`, and `-x` for checking directory existence, readability, writability, and executability.

## 8. Redirecting Output and Errors
- **Definition**: Output and errors can be redirected to files or other commands.
- **Example**:
  - Redirect standard output: 
    ```bash
    ls > files.txt
    ```
  - Redirect standard error: 
    ```bash
    ls non_existent_file 2> error.log
    ```
  - Redirect both output and error:
    ```bash
    ls > output.txt 2>&1
    ```
- **Explanation**: `>` redirects output, and `2>&1` redirects errors to the same location.

## 9. Creating and Using Custom Bash Aliases
- **Definition**: Aliases allow for creating shorthand commands to simplify frequently used commands.
- **Example**:
  ```bash
  alias ll='ls -l'
  alias gs='git status'
  ```
- **Explanation**: Aliases are defined using `alias` and can be added to `.bashrc` to make them persistent.

## 10. Job Control and Background Processes
- **Definition**: Job control allows managing background processes and controlling tasks.
- **Example**:
  - Run a command in the background:
    ```bash
    long_running_process &
    ```
  - Bring a background job to the foreground:
    ```bash
    fg %1
    ```
  - Check jobs:
    ```bash
    jobs
    ```
- **Explanation**: The `&` symbol runs commands in the background, while `fg` brings jobs to the foreground.

## Conclusion

### Key Takeaways:
1. Bash scripting allows automating tasks and creating complex workflows.
2. Variables and functions are key to writing modular and reusable scripts.
3. Understanding conditionals and loops is essential for branching and iterating logic.
4. File test operators and output redirection enhance file handling and error management.
5. Job control helps manage processes and background tasks efficiently.

### Practical Exercise:
1. Write a script that prompts the user for their age and prints whether they are an adult or minor using conditionals.
2. Create a script that accepts a filename as an argument and checks if it exists using file test operators.
3. Write a script that loops through a list of items and prints them one by one using a `for` loop.
4. Use redirection to capture the output of `ls` and any error messages into separate files.
