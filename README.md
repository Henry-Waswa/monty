# Monty
Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files.
## Monty byte code files
Files containing Monty byte codes usually have the .m extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:

```
 push 0$
push 1$
push 2$
  push 3$
                   pall    $
push 4$
    push 5    $
      push    6        $
pall$

```
Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:

```
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$
$
push 2$
  push 3$
                   pall    $
$
$
                           $
push 4$
$
    push 5    $
      push    6        $
$
pall This is the end of our program. Monty is awesome!$

```
## Commands
1. ```push```
Pushes an integer onto the stack.
2. ```pall```
Prints all integers on the stack, starting at the top..
3. ```pint```
Prints the integer at the top of the stack.
4. ```pop```
Removes top element of stack.
5. ```swap```
Swaps top two elements of the stack.
6. ```add```
Add top two elements of the stack, remove them, and push result onto stack.
7. ```sub```
Subtract top two elements of the stack, remove them, and push result onto stack.
8. ```div```
Integer divide top two elements of the stack, remove them, and push result onto stack.
9. ```mul```
Multiply top two elements of the stack, remove them, and push result onto stack.
10. ```mod```
Integer division remainder top two elements, remove them, push result onto stack.
11. ```pchar```
Print the ascii character based on top integer in stack.
12. ```pstr```
Print the ascii characters related to integers in stack until 0 or >255.
13. ```rotl```
Rotate stack. Top element becomes last. Second from top becomes top.
14. ```rotr```
Rotate stack. Last element becomes top, Top element becomes second from top.
15. ```stack```
Changes mode to first in first out (the default behavior). Front of queue becomes top of stack.
16. ```queue```
Changes mode to last in first out. Top of stack becomes front of queue.
## Getting started
Clone the repository and run "gcc -o monty *.c". Then run "./monty \<scriptname\>"
## Usage Examples
The simplest usage is to push a few values onto the stack then print them all. Lets say we have a file like so:

```
push 1
push 2
push 3
pall

```
When we run this with "./monty scriptfile" we get the output:
```
3
2
1

```
To use some of the math functions, we can write a script like so:
```
push 1
push 2
push 3
pall
add
add
pall

```
This nets us an output:

```
3
2
1
6

```
If we want to print numbers as a string, we can have a script like:

```
push 49
push 50
push 51
pstr
```
This gets the output "321"
Available operation codes:
| Opcode | Description |
|------------------- | --------------|
|push   | Pushes an element to the stack. e.g (push 1 # pushes 1 into the stack)|
|pall   | Prints all the values on the stack, starting from the to of the stack.|
|pint   | Prints the value at the top of the stack.|
|pop    | Removes the to element of the stack. |
|swap   | Swaps the top to elements of the stack.|
|add    | Adds the top two elements of the stack. The result is then stored in the second node, and the first node is removed.|
|nop    | This opcode does not do anything.|
|sub    | Subtracts the top two elements of the stack from the second top element. The result is then stored in the second node, and the first node is removed.|
|div    | Divides the top two elements of the stack from the second top element. The result is then stored in the second node, and the first node is removed.|
|mul | Multiplies the top two elements of the stack from the second top element. The result is then stored in the second node, and the first node is removed.|
|mod    | Computes the remainder of the top two elements of the stack from the second top element. The result is then stored in the second node, and the first node is removed.|
|#      | When the first non-space of a line is a # the line will be trated as a comment.|
|pchar  | Prints the integer stored in the top of the stack as its ascii value representation.|
|pstr   | Prints the integers stored in the stack as their ascii value representation. It stops printing when the value is 0, when the stack is over and when the value of the element is a non-ascii value.|
|rotl   | Rotates the top of the stack to the bottom of the stack.|
|rotr   | Rotates the bottom of the stack to the top of the stack.|
|stack  | This is the default behavior. Sets the format of the data into a stack (LIFO).|
|queue  | Sets the format of the data into a queue (FIFO).|

...

## Author
* **HenrWy . Waswa** - [Henry-Waswa](https://github.com/Henry-Waswa)
