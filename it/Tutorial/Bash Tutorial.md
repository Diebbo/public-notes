# Bash Scripting Basics

## Introduction
Bash (Bourne Again SHell) is a command language interpreter widely used in Unix and Linux systems. It allows users to automate tasks by writing scripts. This tutorial provides a basic overview of Bash scripting.

## Getting Started
1. **Creating a Bash Script:**
   Create a new file with a `.sh` extension, e.g., `myscript.sh`.
   ```bash
   touch myscript.sh
	```

## Hello World

Let's start with a simple "Hello, World!" script.

```bash
#!/bin/bash
echo "Hello, World!"
```

- `#!/bin/bash`: Indicates the path to the Bash interpreter. Could be even python with `#!/bin/python3`
- `echo "Hello, World!"`: Prints the text to the terminal.

## Variables

Declare variables to store data.

```bash
#!/bin/bash
name="John" 
echo "Hello, $name!"
```

- `name="John"`: Declares a variable named `name` with the value "John".
- `echo "Hello, $name!"`: Prints the concatenated string.

## User Input

Read user input using `read` command.

```bash
#!/bin/bash
echo "Enter your name:"
read username 
echo "Hello, $username!"```

- `read username`: Reads user input and stores it in the variable `username`.

## Conditional Statements

Use `if` statements for conditional execution.
if a command ended correctly -> 0 otherwise any other number.
`if` -> pass if it's 0

```bash
#!/bin/bash
echo "Enter a number:"
read num
if [ $num -gt 0 ]; then
	echo "Positive number."
 else
    echo "Non-positive number." 
fi```

- `if [ $num -gt 0 ]; then`: Checks if the number is greater than 0.
- `else`: Executes if the condition is not met.
- `fi`: Ends the `if` block.

## Loops

Execute commands repeatedly using loops.

```bash
#!/bin/bash 
for i in {1..5}; do
	echo "Iteration $i" 
done
```

- `for i in {1..5}; do`: Loop from 1 to 5.
- `echo "Iteration $i"`: Print each iteration.


```bash
for file in dir/*; do
	# some stuff
done
```

- notice the wild character `*` e.g. `echo * ~ ls .`

## Functions

Define reusable code using functions.

```bash
#!/bin/bash
greet() {
	echo "Hello from the function!"
 }  
 
 # Call the function
greet
```

- `greet() { ... }`: Defines a function named `greet`.
- `greet`: Calls the function.

# Env
## Running a program

```bash
./program.sh
```

- runs a program in another terminal, not saving the *envirable* variable

```bash
source ./program.sh
```

- run within the same shell process