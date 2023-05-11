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

`find` can also be used to search a specific directory other than the current directory by giving it a desired directory as an argument. For example, the directory /Pictures/Feburary can be searched from the /Pictures directory with the command `find ./Feburary`. This command will result in the output:

```
$ find ./Feburary
./Feburary
./Feburary/newdog.png
```
However, there are many more ways to use `find` beyond just listing the full contents of a given directory.

## Using `find` With Command Line Options

The main way to expand upon the functionality of `find` is by using command line options. Command line options are used by specifying the name of the desired option and then the arguments for that option after the main argument of a command. For example, many command line options are used in the following command structure: `find ./Feburary -exampleCommandOption exampleCommandArgument`. As can be seen, the option name is preceded by `-` and is typed _before_ the option argument. Although there are many such options for `find`, this lab report will cover only 4 of the most useful such command line options.

#### The `-name` Option

The `-name` option is probably the most common used command line option for `find` (and one of the most used command line options of any command). As 

#### The `-type` Option

#### The `-mtime` Option

#### The `-size` Option

## Sources
This lab report was written by consulting the [Lab Report 3 guidelines](https://ucsd-cse15l-s23.github.io/week/week5/#week5-lab-report) and a [useful tutorial webpage on using the `find` command](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/).
