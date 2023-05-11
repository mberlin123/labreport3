# Lab Report 3
## Introduction to `find`
There are many useful commands in Bash. One example of a useful command is `find`. In it's most basic form with no arguments, `find` lists all of the files and subdirectories in the current directory as well as any files and subdirectories within a subdirectory of the current directory.

For example, consider the following directory /Pictures:

```
/Pictures
    /January
        birthdaycake.png
    /Feburary
        newdog.png
    pictureideas.txt
```

Running the `find` command in this directory will result in the following output:
```
$ find
.
./Feburary
./Feburary/newdog.png
./January
./January/birthdaycake.png
./pictureideas.txt
```
However, there are many more ways to use `find` beyond just listing the full contents of a directory.

## Using `find` With Command Line Arguments
