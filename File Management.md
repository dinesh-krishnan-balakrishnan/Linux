# Managing Files & Directories

## Viewing File Information

### Concatenate

```bash
   cat { filename }
   tac { filename }
```

Files are passed into **concatenate** to join them together and send the result to the output stream. Without any stream redirection, the default output stream will be used: the console log. As a result, the program output will be printed to the console. Using **concatenate** to view should only be used on short files as scroll-back isn't provided. **tac** views a file backwards by starting with the last line.

### Less

```bash
   less { filename } 
```

A paging program used to view larger files. It pauses at each screen of full text and provides scroll-back capabilities. While viewing a file, **/** can be used to search for a pattern from the beginning and **?** from the end.

### Head & Tail

```bash
   head { filename }
   tail { filename }
   head -n { number } { filename }
   tail -{ number } { filename }
   tail -f { filename }
```

**head** and **tail** view the first and last 15 lines of a file respectively. A whole number can be passed as an option to change the number of lines displayed, with or without the *number* tag. The *follow* tag on tail will continuously display new lines added to a file.

### File

```bash
   file { filename }
```

Used to find out the filetype of a specified file. The filetype cannot be understood if the required packages for it aren't installed. File extensions are only used for user understanding and aren't used by the system.

- - - -

## Creating Content

### Touch

```bash
   touch { filename } 
   touch -t { time } { filename }
```

Creates an empty file. The **time** flag can be used to specify the time for the file and can modify the time on existing files. The format for the time is:

>  -t [YY]MMddhhmm[.ss]

### Make Directory

```bash
    mkdir { pathname }
```

Makes a new directory, the pathname inputted being the pathname of the directory.

- - - - -

## Removing Content

### Remove

```bash
    rm { filename } ...
    rm -f { filename }
    rm -ri { file/pathname }
```

Removes the specified files, and recursively removes the specified directories with the *recursive* tag. The *forcefully* tag won't prompt the user when nonexistent &write-protected files are being removed. The *interactive* tag insforms the user of which files are being removed when recursively removing files and directories.

### Remove Directory

```bash
    rmdir { pathname }  
```

Removes a directory at the specified pathname, the pathname including the directory. The directory must be empty, or the command will fail.

- - - - - 

## Moving/Renaming Content

### Moving

```bash
    mv { filename/pathname } ... { pathname }
```
The **move** command is used to move both files and directories. Firt specify all files and directories that need moving. Then specify the new location of interest.

### Renaming

```bash
   mv { filename } { filename }
   mv { pathname } { pathname }
```

Renaming files and directories is essentially the same as moving them, due to the file/pathname change. To rename a file or directory, specify its original name and then its new name. 

- - - - -

## Links

A link in Linux is a pointer to a file or directory. There are two types of links: **hard links** and **soft links**.

### Hard Links

```bash
   ln { original-file/pathname } { new-file/pathname }
```

Hard links are assigned the same *inode* (index node) value of the original file link, meaning they have the same metadata and reference the same physical file location. Hard links will still reference the same file, even if the original file has been moved or deleted. 

**NOTE:** Modifying a filename may break the link and result in the creation of two objects, depending on the editor. Most editors, such as **vi**, **gedit**, and the **move** command will not break links. 

### Soft Links

```bash
   ln -s { original-filename } { new-filename }
```

Soft links are created with the *soft* tag. The link is strictly a pointer containing a pathname and has a different *inode* value than the original. While moving or deleting a file/directory will break the link, soft links can point to objects on different filesystems, partitions, disks, and other media. Think of soft links like Windows shortcuts.