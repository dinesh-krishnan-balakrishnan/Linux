# Environment Variables and Aliases

An environment variable is essentially a character string that contains information used by one or more applications. These values may be given preset values by the system, or may be set directly by the user.

```bash
    echo $SHELL

    VARIABLE='value with spaces'
    export <VARIABLE>=<value>
```

The 'echo' command allows the user to easily see the values of environment variables. While a variable can be declared without the export command, the export command makes the variable available to child processes. To add a variable and its value permanently, add the export command to the *~/.bashrc* file.

## HOME

The **HOME** environment variable represents the home directory of the user. '~' is simply an abbreviation for **\$HOME**. In fact, 'cd' without arguments redirects to the **\$HOME** path.

## SHELL

**SHELL** points to the user's default command shell, the program that handles whatever the user types in a terminal window. (bash)

## PATH

The **PATH** environment variable is an ordered list of directories that are scanned to find the appropriate program or script to run, based on the entered command. Each directory is seperated by a ':', while a null directory indicates the current directory at any given time.

>EX: :path1:path2

In the example above, the current directory, path1 directory, and path2 directory will be searched for an executable.

```bash
    export PATH=<pathname>:$PATH
    export PATH=$PATH:<pathname>
```

The above code shows how to add another directory to the **PATH** variable. Essentially, the variable needs to be recreated with the
extra path added to the string.

## PS1

Prompt Statement (PS) is used to customize the prompt string in the user's terminal windows to display desired information. **PS1** is the primary prompt variable which controls what the command line prompt looks like.

Special Characters for **PS1**:
| **\u** - User name
| **\h** - Host name
| **\w** - Current working directory
| **\!** - History number of this command
| **\d** - Date

**NOTE:** When the special characters are used in the value, the value needs to be surrounded by quotes.

## History Environment Variables

| Variable         | Description                                                    |
| ---------------- | -------------------------------------------------------------- |
| **HISTFILE**     | The location of the history file.                              |
| **HISTFILESIZE** | The maximum number of lines in the history file (default 500). |
| **HISTSIZE**     | The maximum number of commands in the history file.            |
| **HISTCONTROL**  | How commands are stored.                                       |
| **HISTIGNORE**   | Which command lines can be unsaved.                            |

## Aliases

Aliases are similar to environment variables such that they store information. In this case though, they store an instruction. To create an alias:

```bash
    alias <variable>='<instruction (command-flags-arguments)>'
```