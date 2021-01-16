# Reading

## What is Jupyter Lab?

> JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner

Start JupyterLab using:

`jupyter lab`

You may access JupyterLab by entering the notebook server’s URL into the browser. JupyterLab sessions always reside in a workspace. The default workspace is the main /lab URL:

`http(s)://<server:port>/<lab-location>/lab`

- File: actions related to files and directories

- Edit: actions related to editing documents and other activities

- View: actions that alter the appearance of JupyterLab

- Run: actions for running code in different activities such as notebooks and code consoles

- Kernel: actions for managing kernels, which are separate processes for running code

- Tabs: a list of the open documents and activities in the dock panel

- Settings: common settings and an advanced settings editor

- Help: a list of JupyterLab and kernel help links

Numpy Tutorial

NumPy is a commonly used Python data analysis package

Here is the code to import csv library and create a new csv.reader object with opening of the file.

- Pass in the keyword argument delimiter=";" to make sure that the records are split up on the semicolon character instead of the default comma character.

- Call the list type to get all the rows from the file.

- Assign the result

``` python
import csv
with open('winequality-red.csv', 'r') as f:
    wines = list(csv.reader(f, delimiter=';'))
```

Bookmark/Skim
[x] Numpy Arrays done!