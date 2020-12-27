# File & Directory Management

## Comparing Content

### Difference

```bash
   diff { 1st-filename } { 2nd-filename }
   diff -r { 1st-directory } { 2nd-directory }
```

**Difference** compares files and directories, with the following options:

| diff Option | Usage |
| ----------- | ----- |
| -c          | Provides a listing of differences that include three lines of context before and after the lines differing in content. |
| -r          | Used to recursively compare subdirectories, as well as the current directory. |
| -i          | Ignore the case of letters. |
| -w          | Ignore differences in spaces and tabs (white space). |
| -q          | Be quiet: only report if files are different without listing the differences. |

### Compare

```bash
   cmp { 1st-filename } { 2nd-filename }
```

Compares binary files.

### Difference - 3 Files

```bash
   diff3 { 1st-filename } { common-file } { 2nd-filename }
```

Compares three different files.

- - - - -

## Patches

### Creating Patches

```bash
   diff -Nur { original-file/pathname } { new-file/pathname } > { patch-file }
```

With the correct arguments, **difference** can be used to create a patch file.

### Applying Patches

```bash
   patch { original-file } { patch-file }
   patch < { patch-file }
```

To patch a single file, enter both the original and patch file as arguments to **patch**. If an entire directory nees to be modified, change **patch**'s input stream to the patch file.

- - - - -

## Copying Content

```bash
   cp { original-file } { new-file }
   rsync { original-file } {new-file }

   cp -r { original-file } { new-file }
   rsync -r { original-file } { new-file }

   rsync --progress -avrxH  --delete /originaldir /newdir
```

**copy** and **remote synchornization** copy files and directories, but **rsync** is much more efficient. It only copies files and changes that don't already exist at the destination. **rsync** also has the ability to copy files over a network. A good combination of tags is shown on 'rsync' above.

- - - - -

## Compressing Content

### gzip

```bash
   gzip { filename }
   gzip -r { pathname }

   gzip -d { filename }
   gunzip { filename }
```

**gzip** is the fastest compression method. That said, it also has the least file compression; its compressed files are larger than those produced by other commpression methods. Both **gzip** with the *decompress* tag and **gunzip** decompress GZIP files.

### bzip2

```bash
   bzip2 { filename }
   bzip2 { pathname }

   bzip2 -d { filename }
   bunzip2 { filename }
```

**bzip2** is a bit slower than **gzip**, but has more file compression. The command automatically detects whether a file or directory is being compressed. Both **bzip2** with the *decompress* flag or **bunzip2** decompress BZIP2 files.

### xz

```bash
   xz { filename }
   xz { pathname }

   xz -d { filename }
   xz -dcf { 1st-file } { 2nd-file } > { new-file }
```

**xz** is the slowest compression program, but also has the most efficient compression. It is currently used to store archives of the Linux kernel.**xz** combined with the *decompress*, *keep *, and *force* tags will allow the user to concatenate many files together, compressed or not.

### zip

```bash
   zip { new-filename } { original-filename }
   zip -r { new-pathname } { original-pathname }

   unzip { filename }
```

**zip** is a legacy program only really used in Linux when receiving a zipped file form a Windows user. Zipping files requires a new name to be specified; it doesn't just change the extension.

### Tape Archive

```bash
   tar -zcvf { new-file/pathname }.tar.gz { original-file/pathname }
   tar -jcvf { new-file/pathname }.tar.bz2 { original-file/pathname }
   tar -Jcvf { new-file/pathname }.tar.xz { original-file/pathname }

   tar -xzvf {file}.tar.gz
```

**tar** historicially stands for *tape archive*, and was used to archive files to a magnetic tape. It allows the user to use the **gzip**, **bzip2**, or **xz** compression methods to create a compressed file called a *tarball*. *x* stands for *extract*.