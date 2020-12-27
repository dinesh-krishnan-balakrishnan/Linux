# Navigating the Filesytem

## Pathnames

* **Absolute Pathname:** Absolute pathnames start with a **/**, which represents the root directory. The pathname then lists out the name of sub-directories to traverse through to reach the specified destination. 

* **Relative Pathname:** Relative pathnames work like absolute pathnames, except they show how to reach the specified destination from the current user location, not the root directory.

- - - - - -

## Viewing Contents

### Present Working Directory

```bash
   pwd 
```
Diplays the current working directory.

### Tree

```bash
   tree
   tree -d 
```

The tree package may not be present in some OS such as Ubuntu, but can be downloaded easily using the package manager. It shows a tree view of directories and files starting from the current directory. The *directories* flag is used to supress listing file names.

### List

```bash
   ls
   ls -la
   ls -l { filename } 
```

Lists the contents of the working directory, not including sub-directories. Hidden files can also be displayed with the *all* flag, while extra details can be displayed with the *long* flag. Details about a specific file can be displayed by passing in a filename as an argument and using the *long* option.

### Which & Where Is

```bash
   which { command }
   whereis { command } 
```
**which** locates the file location of the command executable. **whereis** functions like **which**, except it searches a larger range of system directories and contains the file locations for man pages (documentation) plus source code.

- - - -

## Changing Directories

### Change Directory

```bash
   cd
   cd ~ 
```

**Home Directory**: **~** is a shorthand for the user's **HOME** directory. Both commands shown above will change to this directory.
```bash
   cd .. 
   cd -
```

**Parent & Previous Directory**: '**..**' is used to change to the parent directory, while '**-**' is used to change to the previous working directory.

```bash
   cd { pathname }
```

**Pathname:** The user can change to a specific directory by using either relative or absolute pathnames.

### Push Directory & Pop Directory

```bash
    pushd .
    popd
```
**Push Directory** and **Pop Directory** are stack commands. **Push Directory** pushes the specified directory into a stack, the example above pushing the current directory. **Pop Directory** removes the last pushed directory from the stack, also navigating to that directory. 


