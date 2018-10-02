## splab2 - forking processes
###### \[deadline is week06 labtime, October 8-12, 2018 \]

### Aim
- To master process creation system calls

### Objectives
- solve several small tasks that user `fork`, `exec*`, `waitpid`, `exit` etc system calls.

## DOMATH
Write a program `domath.c` and compile it as `domath`. The program should accept **two** arguments, create **four** child processes and pass the arguments to the child processes. Each of the child processes should perfom an arithmetic operation over the arguments (like addition, subtraction, multiplication or division) as shown below. File `domath.c` should contain code of parent process and all its child processes.

```
$ gcc domath.c -o domath
$ ./domath 3 5
child1: 3+5=8
child3: 3*5=15
child2: 3-5=-2
child4: 3/5=0
parent: done.
```

## MATHDO
Write a program `mathdo.c` that will take the same arguments as in the previous task and create **four** child processes. Unlike the previous task this task does not want the parent process to contain code for all its child processes. Instead the parent process spawns child processes written in other programming languages. Let `python` script do addition, a `java` program do subtraction, `nodejs` script do multiplication and a `bash` script do division. (they may need to be installed to your system first)

```
$ gcc mathdo.c -o mathdo
$ ./mathdo 3 5
python: 3+5=8
java: 3-5=-2
nodejs: 3*5=15
bash: 3/5=0
parent: done.
```

## SHELL
Write a program `shell.c` that repeatedly (in a loop) prompts user for a command, reads the command and executes it in a child process. If a user prints `&` in the end of a command your program should run the command as a child process in the background. When user enters `exit` command your program should exit.

```
$ Enter your command: ls -a
.  ..  a.c  b.py  c.cpp  D.java
$ Enter your command: gnome-mines &
$ Enter your command: gnome-calculator -e 2+3
$ Enter your command: exit
```

## PSHELL
Task D is an extension of **SHELL**. Add a built-in command `showjobs` which will show pids of all background processes only if they are still running. Give `pshell.c` name to your program.
```
$ gcc pshell.c -o pshell
$ ./pshell
$ Enter your command: gnome-mines &
$ Enter your command: gnome-calculator -e 2+3 &
$ Enter your command: showjobs
1. [65123]
2. [65124]
$ Enter your command: exit
```

## \*DOMATH the Linux Way (sorry Mac users)

This task is optional.

`fork` and `exec` system calls are UNIX-wide. Linux has it's own `clone` system call for creating processes (actually threads). Complete task **DOMATH** using `clone` system call.

## References

1. `man fork`
2. `man execve`
3. `man waitpid`
4. `man clone`
5. [OSTEP Chapter 5](http://pages.cs.wisc.edu/~remzi/OSTEP/cpu-api.pdf)
6. Chapters 6, 24-28 of Linux Programming Interface by Micheal Kerrisk
7. Chapter 5 of Linux System Programming by Robert Love
