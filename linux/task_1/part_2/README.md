## Task1.Part2


1) Examine the **tree** command. Master the technique of applying a template, for example, display all files that contain a character c, or files that contain a specific sequence of characters. List subdirectories of the root directory up to and including the second nesting level.
```bash
tree -P '*c*' -L 2
```

![](https://i.imgur.com/yHjQMJG.png)

Options available in `tree` command in Linux
- –help 	–help 
- –version Outputs the version of the tree.

- `-a` or `–all`	Includes hidden files and directories in the tree.

- `-d` or `–dirs-only`	 List directories only.

- `-f` or `–full-path`	Prints the full path prefix for each file. 

- `-i` or `–ignore-case`	 Ignores case when sorting filenames.

- -x	Stay on the current file system only, as with find -xdev. 

- -I	 Do not list those files that match the wild-card pattern. 

- `-p` or `–prune`	Omits the specified directory from the tree.

- –filelimit #	Do not descend directories that contain more than # entries. 

- -t	 Sort the output by last modification time instead of alphabetically.

- –noreport 	 Omits printing of the file and directory report at the end of the tree listing. 

- -s	 Print the size of each file along with the name.

- -u	 Print the username, or UID # if no username is available, of the file.

- -g	Print the group name, or GID # if no group name is available, of the file

- -D	Print the date of the last modification time for the file listed. 

- –inodes	Prints the inode number of the file or directory 

- –device	Prints the device number to which the file or directory belongs 

- -F	Append a `/’ for directories, a `=’ for socket files, a `*’ for executable files and a `|’ for FIFO’s, as per ls -F 

- -q	Print non-printable characters in file names as question marks instead of the default carrot notation.

- -N	Print non-printable characters as is instead of the default carrot notation. 

- -r	Sort the output in reverse alphabetic order. 

- –dirsfirst	List directories before files. 

- -n	Turn colorization off always, over-ridden by the -C option. 

- -C 	Turn colorization on always, using built-in color defaults if the LS_COLORS environment variable is not set. Useful to colorize output to a pipe. 

- -A	Turn on ANSI line graphics hack when printing the indentation lines.

- -S	Turn on ASCII line graphics (useful when using linux console mode fonts). This option is now equivalent to `–charset=IBM437′ and will eventually be depreciated. 

- -L level	 Max display depth of the directory tree. 

- -R	 Recursively cross down the tree each level directories (see -L option), and at each of them execute tree again adding `-o 00Tree.html’ as a new option. 

- -H baseHREF 	Turn on HTML output, including HTTP references. Useful for ftp sites. baseHREF gives the base ftp location when using HTML output. That is, the local directory may be `/local/ftp/pub’, but it must be referenced as `ftp://host-name.organization.domain/pub’ (baseHREF should be `ftp://hostname.organization.domain’). Hint: don’t use ANSI lines with this option, and don’t give more than one directory in the directory list. If you want to use colors via CSS stylesheet, use the -C option in addition to this option to force color output. 

- -T title	Sets the title and H1 header string in HTML output mode. 

- –charset charset	Set the character set to use when outputting HTML and for line drawing. 

- –nolinks	Turns off hyperlinks in HTML output. 

- -o file name	  Send output to file name. 

![](https://i.imgur.com/ifIhfPB.png)

![](https://i.imgur.com/lHhMDS8.png)

view with HTML

![](https://i.imgur.com/GIJgfQ3.png)

[HTML file](index.html)

special simbol

![](https://i.imgur.com/mNy1JXV.png)
---
2) What command can be used to determine the type of file (for example, text or binary)? Give an example.

The **file** command in Linux is used to determine the type of a file, whether it's a text file, binary file, or some other format. 

```bash
file [option] filename
```
![](https://i.imgur.com/TlH6SyX.png)

The option in the syntax allows you to add variables to the Linux file command. Here are some of the most common ones:

- -b or –brief – fetches a short description of the file type.
- file * – lists all file types in the current working directory.
- -i or –mime – shows the MIME file type.
- -s or –special-files – reads special files.
- -z or –uncompress – checks and displays information inside compressed files.
- -c or –checking-printout – checks a magic file’s parsed version.
- -m or –magic-file – utilizes an alternative magic file provided by the user.
- -d – displays internal debugging information using the standard format.
- <regex range> – fetches file types in specific ranges.
- -0 or –print0 – prints a null character at the end of the file name.
- –help – shows the file command’s help message. It also lists acceptable options and their usage.

![](https://i.imgur.com/wNtZaDI.png)

3) Master the skills of navigating the file system using relative and absolute paths. How can you go back to your home directory from anywhere in the filesystem?

**Relative Paths**: Relative paths are specified relative to your current working directory. For example, if you're in the /home/username/Documents directory, a relative path like Downloads would refer to /home/username/Documents/Downloads.

**Absolute Paths**: Absolute paths specify the full path from the root directory (/) to a specific location in the file system. For example, the absolute path to the /home/username/Downloads directory is /home/username/Downloads, regardless of your current working directory.

To go back to your home directory from anywhere in the file system, you can use the tilde (~) character, which represents your home directory. Here are two common ways to navigate to your home directory:

```bash
cd ~
```

![](https://i.imgur.com/2SyYuyr.png)

---
4) Become familiar with the various options for the ls command. Give examples of listing directories using different keys. Explain the information displayed on the terminal using the -l and -a switches.

![](https://i.imgur.com/rTOfnEW.png)

### Basic Listing:

By default, the ls command lists the files and directories in the current directory in a simple format.
    
```bash
ls
```
### Listing with -l (Long Format):

The -l option (long format) provides detailed information about files and directories, including permissions, owner, group, file size, modification date, and name.

```bash
ls -l
```
```
total 20
-rw-r--r-- 1 user user 12345 Sep 5 10:00 file.txt
drwxr-xr-x 2 user user  4096 Sep 5 09:55 directory/
```

- The first column indicates file type and permissions.
- The second column shows the number of hard links.
- The third and fourth columns specify the owner and group.
- The fifth column is the file size in bytes.
- The sixth column shows the modification date and time.
- The last column displays the file or directory name.

### Listing with -a (All Files):

The -a option (all files) displays hidden files and directories, which are those whose names start with a dot (.).

```bash
ls -a
```

### Listing in Reverse Order:

The -r option (reverse) lists files and directories in reverse order (from Z to A).

```bash
ls -r
```

### Listing by File Size:

The -S option lists files and directories by file size, with the largest files first.

```bash
ls -S
```

### Listing with Human-Readable File Sizes:

The -h option (human-readable) displays file sizes in a more human-friendly format, using units like KB, MB, or GB.

```bash
ls -lh
```

### Listing by Modification Time:

The -t option lists files and directories in order of modification time, with the most recently modified first.

```bash
ls -t
```

### Listing Only Directories:

The -d option lists only directories and not their contents.

``` bash
ls -d */
```

### Listing with Colorized Output:

Many Linux distributions have colorized output enabled by default. If it's not, you can use the --color=auto option to enable colorized output.

```bash
ls --color=auto
```

---
5) Perform the following sequence of operations:
    - create a subdirectory in the home directory;
    - in this subdirectory create a file containing information about directories located in the root directory (using I/O redirection operations);
    - view the created file;
    - copy the created file to your home directory using relative and absolute
    addressing.
    - delete the previously created subdirectory with the file requesting removal;
    - delete the file copied to the home directory.

    ![](https://i.imgur.com/p1ZxlHx.png)
---
6) Perform the following sequence of operations:
    - create a subdirectory test in the home directory;
    
    ![](https://i.imgur.com/VqoHNFc.png)