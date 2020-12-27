# Globbing and System Searches

## Globbing

Globbing is the practice of searching for files and directories based on patterns of characters, using wildcards. When globbing the wildcards undergo file expansion and find matching files/directories. The wildcards are:

| Wildcard | Result                                             |
| -------- | -------------------------------------------------- |
| ?        | Matches any single character                       |
| *        | Matches any string of characters                   |
| [set]    | Matches any character in the set of characters     |
| [^set]   | Matches any character not in the set of characters |

**NOTE:** Globbing using wildcards isn't the same as using regex. 

## Using Globbing

```bash
   ls -a [a-z].*
```
In the example above, all files that have a single alphabet character name will be printed out to the console.

```bash
   ls -a "filename/pathname"
```

To stop typed content from globbing, put double quotes around the content.

- - - -

## POSIX Character Sets

POSIX has a character set standard that uses specific keywords to represent sets. These are:

* **[:upper:]** - Uppercase Letters ([A-Z])

* **[:lower:]** - Lowercase Letters ([a-z])

* **[:alpha:]** - Uppercase & Lowercase Letters	([A-Za-z])	

* **[:digit:]** - Digit ([0-9])

* **[:xdigit:]** - Hexadecimal Digits ([0-9A-Fa-f])

* **[:alnum:]** - Letters & Digits ([0-9A-Za-z])

* **[:word:]**	- Letters, Numbers, & Underscore ([[:alnum:]_])

* **[:punct:]** - Punctuation (Graphic Characters & [^[:alnum]])

* **[:blank:]** - Space and Tab ([ \t])

* **[:space:]** - [ \t\n\r\f\v]

* **[:cntrl:]** - Control Characters

* **[:graph:]** - Graphic Characters ([^[:cntrl:]])	

* **[:print:]** - Graphic Characters & Space	([[:graph:] ])	graphic characters and space

- - - -

## System Searches

### Filesystem Database & Locate

```bash
   sudo updatedb
   locate file/pathname
```

Linux systems have a database of the filesystem, which 
automatically updates once a day. The database can be 
manually updated by running the **update database** command 
as a super user. The **locate** command then uses this database to find all matching files and directories that match the argument string.

### Find

```bash
   find { pathname }
   find -type { f / d / l } -name '{ file/pathname }'
   find -iname '{ file/pathname }'
```

**Find** lists all contents in the specified directory, the current directory being used if no directory is specified. With the *type* tag, **find** can target files, directories, or symbolic links. Lastly, the *name* and *ignore-case name* tags causes the **find** command to search for the specified file or directory.

**NOTE**: Globbing is required to use the *name* tag. Else, the find command will search for the exact specifed file or directory and no more. When using globbing, surround the *file/pathname* in quotes. If not, globbing will occur before the command executes and a file/pathname literal will be used for the *name* option.


```bash
   find -exec instruction {} ';'
   find -ok instruction {} '+'
```

Both the *execute* and *ok* tags perform commands on the results produced by find. The only difference is that the *ok* tag will prompt the user before executing. **';'** will execute the statement for each file/pathname found, while **'+'** will pass all file/pathnames into one statement. The squiggly brackets indicate where to place the command arguments.

```bash
   find -ctime { days }
   find -atime -{ days }
   find -mtime +{ days }
```

Files and directories can be further filtered down by searching using their *creation time*, *last accessed time*, and *last modified time*. The plus sign represents greater than, while the minus sign represents less than.

```bash
   find pathname -size { file/directory size } 
   find pathname -size +10M
```

Files and directories can also be searched for by their size, the default unit being bytes. The example above searches for files that are greater than 10 megabytes. 

| Unit      | Symbol |
| --------- | ------ |
| Bytes     | c      |
| Kilobytes | k      |
| Megabytes | M      |
| Gigabytes | G      |

