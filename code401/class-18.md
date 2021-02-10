# Reading

## Python Regular Expressions Tutorial

> You will start with importing re - Python library that supports regular expressions.

> copyfile() copies the contents of the source to the destination and raises IOError if it does not have permission to write to the destination file.

> The implementation of copyfile() uses the lower-level function copyfileobj(). While the arguments to copyfile() are filenames, the arguments to copyfileobj() are open file handles. The optional third argument is a buffer length to use for reading in blocks.

>  Use -1 to read all of the input at one time or another positive integer to set a specific block size.

> The copy() function interprets the output name like the Unix command line tool cp. If the named destination refers to a directory instead of a file, a new file is created in the directory using the base name of the source.

> By default when a new file is created under Unix, it receives permissions based on the umask of the current user. To copy the permissions from one file to another, use copymode().

> shutil includes three functions for working with directory trees. To copy a directory from one place to another, use copytree(). It recurses through the source directory tree, copying files to the destination. The destination directory must not exist in advance.

> he which() function scans a search path looking for a named file. The typical use case is to find an executable program on the shell’s search path defined in the environment variable PATH.

> get_archive_formats() returns a sequence of names and descriptions for formats supported on the current system.

>Use make_archive() to create a new archive file.

> disk_usage() returns a tuple with the total space, the amount currently being used, and the amount remaining free.

| basics | definitions|
|---|---|
| basic/ordinary characters |The match() function returns a match object if the text matches the pattern. Otherwise, it returns None|
| wild or special characters |reserved metacharacters that denote something else and not what they look like|
| repetitions | re module handles repetitions using special characters|
|  groups and named groups |allows you to pick up parts of the matching text|
|  greedy vs. non-greedy matching |When a special character matches as much of the search sequence (string) as possible, it is said to be a "Greedy Match"|

## shutil

> The shutil module includes high-level file operations such as copying and archiving



## [Automation Ideas](https://www.youtube.com/watch?v=qbW6FRbaSl0&t=69s)

## Optional: [Automating Your Browser and Desktop Apps](https://www.youtube.com/watch?v=dZLyfbSQPXI)

[x] Bookmarked! [Watchdog](https://pythonhosted.org/watchdog/)