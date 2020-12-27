# Introduction to The Command Line

## Main Benefits

1. No GUI overhead is incurred.
   
2. Scripts can be made to automate tasks and series of procedures. 
   
3. It is possible to sign into remote machines on the Internet.

4. 6 console-based virtual terminals (VTs) are automatically enabled, compared to a single graphic VT.

- - - -

## General Syntax

* **Command:** The name of the program that is being executed.
>EX: ls

* **Options (Flags):** Options modify what a command will do, and start with either one or two dashes. This is to differentiate them from arguments.
>EX: ls -l (One flag), ls -la (Two flags)

* **Arguments:** Arguments are parameters upon which a command executes. 
>EX: touch file.txt (file.txt is the argument)

* **Instruction:** A combination of a command with or without options and arguments that performs a specific task.

* **Note:** Some commands don't need arguments or options to execute, and most commands accept many arguments and options.

- - - -

## Using the Command Line

**NOTE:** To exit a currently running process on the terminal, press 'CTRL-c'.

### Super User Do

```bash
    sudo { instruction }
```
The sudo keyword temporarily elevates an user's status to that of a **root** user. A **root** user has the highest level of access in a system; as a result, restrictions on certain commands are removed and the user won't be constantly warned when making important file changes.

### bash

```bash
   bash
   exit
```

Starts a new bash shell. To leave the bash shell run the **exit** command.

### history

```bash
   history
```

Lists previously executed commands, which is stored in *~/.bash_history*. If multiple terminal sessions are open, the commands typed in a session aren't saved until that session is closed. Previously executed commands can also be accessed using the *Up* and *Down* arrow keys or pressing *CTRL-R* and performing a search. Lastly, typing *!!* executes the last command.

### History Environment Variables

There are multiple environment variables related to the bash history file. They are:

* **HISTFILE:** The location of the file.
* **HISTFILESIZE:** The maximum number of lines in the file (Default is 500).
* **HISTSIZE:** The maximum number of commands in the file.
* **HISTCONTROL:** How commands are stored.
* **HISTIGNORE:** Which commands won't be recorded by the history file.