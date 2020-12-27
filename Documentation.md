# Help and Documentation

**NOTE:** To see package documentation, look at the **'/usr/share/doc'** directory in the Linux filesystem.

## Manual

### Default Command

```bash
    man { command }
```

Shows documentation for a command from the Unix Programmer's Manual.

### Full Description Summary

```bash
    man -f { command }
    whatis { command }
```

Both **manual** with the *full* tag and **whatis** display short descriptions of all manual pages covering the specified *command*, along with the chapter numbers.

### Full Description

```bash
    man -k command
    apropos command
```

**NOTE:** In English, **apropos** means relevant.

Both **manual** with the *kindred* tag and **apropos** display all manual pages covering AND refrencing the specified command.

### Chapter Descriptions

```bash
    man -a { command }
    man { chapter # } { command }
```

The *all* tag displays all chapters covering the specified *command*. A specific chapter can be displayed by including a number argument.

### Manual Database

```bash
   sudo mandb 
```

Updates manual pages. 

- - - - -

## Information

```bash
   info 
   info { command } 
```

GNU, which ironically stands for *"GNU's not Unix"*, is an operating system. Its creators also made their own documentation which is a more modern version of **man** pages. **Information** displays all available topics, while adding a *command* argument will display information pages for that particular command. 

While on the information page:
* **/**: Keyword Search
* **h**: Displays Help

## Help

```bash
    cd --help
    help
```

Some popular commands such as **change directory** are built into the bash terminal rather than being located in the filesystem. These commands may not have a man page associated with them, but their documentation can be viewed using the *help* tag. The **help** command displays a short synopsis for built-in shell commands. 

## Graphical Manuals

```bash
    gnome-help
    khelpcenter
```

Linux desktop systems also have a graphical help application. These programs usually contain custom help for the desktop itself. **gnome-help** is for GNOME, while **khelpcenter** is for KDE.