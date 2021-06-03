# Reading

## Read & Write Files in Python

This is a tutorial it teaches:

> What makes up a file and why that’s important in Python

a file is a contigous set of bytes used to store data
Files are composed of three main parts:

1. Header: metadata about the contents of the file (file name, size, type, and so on)
2. Data: contents of the file as written by the creator or editor
3. End of file (EOF): special character that indicates the end of the file

> The basics of reading and writing files in Python

>Additionally, there are built-in libraries out there that you can use to >help you:

1. wave: read and write WAV files (audio)
2. aifc: read and write AIFF and AIFC files (audio)
3. sunau: read and write Sun AU files
4. tarfile: read and write tar archive files
5. zipfile: work with ZIP archives
6. configparser: easily create and parse configuration files
7. xml.etree.ElementTree: create or read XML based files
8. msilib: read and write Microsoft Installer files
9. plistlib: generate and parse Mac OS X .plist files

## Exceptions in Python

> exception error. This type of error occurs whenever syntactically correct Python code results in an error. The last line of the message indicated what type of exception error you ran into.

> If you want to throw an error when a certain condition occurs using raise, you could go about it like this:

x = 10
if x > 5:
    raise Exception('x should not exceed 5. The value of x was: {}'.format(x))

> We assert that a certain condition is met. If this condition turns out to be True, then that is excellent! The program can continue. If the condition turns out to be False, you can have the program throw an AssertionError exception.

> The try and except block in Python is used to catch and handle exceptions. Python executes code following the try statement as a “normal” part of the program

> Warning: Catching Exception hides all errors…even those which are completely unexpected. This is why you should avoid bare except clauses in your Python programs. Instead, you’ll want to refer to specific exception classes you want to catch and handle

> A try clause is executed up until the point where the first exception is encountered.
> Inside the except clause, or the exception handler, you determine how the > program responds to the exception.
> You can anticipate multiple exceptions and differentiate how the program should respond to them.
> using the else statement, you can instruct a program to execute a certain block of code only in the absence of exceptions.
> everything in the finally clause will be executed. It does not matter if you encounter an exception somewhere in the try or else clauses

