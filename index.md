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

The main way to expand upon the functionality of `find` is by using command line options. Command line options are used by specifying the name of the desired option and then the arguments for that option after the main argument of a command. For example, many command line options are used in the following command structure: `find ./Feburary -exampleCommandOption exampleCommandArgument`. 
As can be seen, the option name is preceded by `-` and is typed _before_ the option argument. Command line arguments can also often times be used together at the same time in different combination. 
Although there are many such options for `find`, this lab report will cover only 4 of the most useful such command line options.

* ### The `-name` Option

The `-name` option is probably the most common used command line option for `find` (and one of the most used command line options of any command). It has two main uses. The first is for narowing down your `find` search if you know a portion of the name of the file(s) you are looking for. For example, if in the /technical/plos directory, you only care about files with "pmed" in the name, you can run the `find` command as follows:

`find ./technical/path -name pmed*`

The resulting output is:

```
$ find ./technical/plos/ -name pmed*
./technical/plos/pmed.0010008.txt
./technical/plos/pmed.0010010.txt
./technical/plos/pmed.0010013.txt
./technical/plos/pmed.0010021.txt
./technical/plos/pmed.0010022.txt
./technical/plos/pmed.0010023.txt
./technical/plos/pmed.0010024.txt
./technical/plos/pmed.0010025.txt
./technical/plos/pmed.0010026.txt
./technical/plos/pmed.0010028.txt
./technical/plos/pmed.0010029.txt
./technical/plos/pmed.0010030.txt
./technical/plos/pmed.0010034.txt
./technical/plos/pmed.0010036.txt
./technical/plos/pmed.0010039.txt
./technical/plos/pmed.0010041.txt
./technical/plos/pmed.0010042.txt
./technical/plos/pmed.0010045.txt
./technical/plos/pmed.0010046.txt
./technical/plos/pmed.0010047.txt
./technical/plos/pmed.0010048.txt
./technical/plos/pmed.0010049.txt
(Continues for many more files)
```

As can be seen, only files that begin with `pmed` are listed using this variation of the `find` command. It is important to note that the `*` at the end of `pmed` specifies that any characters after `pmed` are allowed. If the command `find ./technical/path -name pmed` is run instead, `find` will look for files only with the exact name `pmed` and therefore will not output any files at all as no files in the directory are named `pmed`.

Another way to use the `-name` option is to specify by file extension. An example of how this could be used is to only output files in the `/technical` directory that are `.txt` files, ignoring any other file (or directory). To do this, the `*` from the `plos` example is once again used as follows:

`find ./technical -name *.txt`

As before, the `*` signals to bash that any file name is acceptable so long as it ends with the content after the `*` (in this case `.txt`). This command therefore results in the following output:

```
$ find ./technical -name *.txt
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
./technical/911report/preface.txt
./technical/biomed/1468-6708-3-1.txt
./technical/biomed/1468-6708-3-10.txt
./technical/biomed/1468-6708-3-3.txt
./technical/biomed/1468-6708-3-4.txt
(And so on for every other .txt file in ./technical)
```

As these two examples of `-name` show, `-name` is a both useful and versatile command option that can be frequently used in bash.

* ### The `-type` Option

The `-type` option is used with similar syntax to the `-name` option. However, instead of filtering by names, it filters by type. Type is not the same thing as extension. Instead, type refers to a broader category of entities on the file system such as whether an item is a file, a directory, or something else. Although Linux contains many different options to use the `-type` option for as the file system is used for many various purposes, the most common use of `-type` is to filter by files or by directories.

For example, while in the `/technical` directory, to list the subdirectories of the `./technical` folder, the following command can be used:

`find -type d`

This command results in the following output:

```
$ find -type d
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```

`-type` can also be used in the opposite way, that is to filter by files. This can be done with the following command:

`find -type f`

This command results in the following output (when run in the `./technical` folder):

```
$ find -type f
./911report/chapter-1.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
./911report/chapter-12.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-2.txt
./911report/chapter-3.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-8.txt
./911report/chapter-9.txt
./911report/preface.txt
./biomed/1468-6708-3-1.txt
./biomed/1468-6708-3-10.txt
./biomed/1468-6708-3-3.txt
(And so on for every file in the ./technical folder)
```

* ### The `-mtime` Option

The `-mtime` option is used to filter files by the date in which they were last modified. The `-mtime` option works similarly to the previous two examples, however there is one major difference. The user can choose to filter files either by a "less than" or "greater than" approach. That is, files can be filtered by "last modified since 5 days ago" or "last modified before 5 days ago". The syntax to do this is slightly different than the previous two options.

To filter files by recently modified **in the last 1 day**, the following command is used:

`find -mtime -1`

This command will return the following output:

```
$ find -mtime -1
.
./911report
./911report/chapter-1.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
./911report/chapter-12.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-2.txt
./911report/chapter-3.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-8.txt
./911report/chapter-9.txt
./911report/preface.txt
./biomed
./biomed/1468-6708-3-1.txt
./biomed/1468-6708-3-10.txt
```

As can be seen, this command basically returns the same result as the normal `find` command, because every file in the `./technical` directory was modified in the last day (due to being recently downloaded).

However, if instead files are filtered by recently modified **before the last 1 day** as in the following command:

`find -mtime +1`

The output will instead be:

```
$find -mtime +1

```

You're reading that right! There will be no output to the command, as there are no files (or directories) in the `./technical` folder that were modified before 1 day ago.

* ### The `-size` Option

The final option that will be covered in this lab report is the `-size` option. `-size` works very similarily to the `-mtime` option.

To filter by files **larger than** 100 kilobytes, the following command can be used:

`find -size +100k`

Which gives the following output:

```
$ find -size +100k
./911report/chapter-1.txt
./911report/chapter-12.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-3.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./biomed/1471-2105-3-2.txt
./government/About_LSC/commission_report.txt
./government/About_LSC/State_Planning_Report.txt
./government/Env_Prot_Agen/bill.txt
./government/Env_Prot_Agen/ctm4-10.txt
./government/Env_Prot_Agen/multi102902.txt
./government/Env_Prot_Agen/tech_adden.txt
./government/Gen_Account_Office/ai9868.txt
./government/Gen_Account_Office/d01376g.txt
./government/Gen_Account_Office/d01591sp.txt
./government/Gen_Account_Office/d0269g.txt
./government/Gen_Account_Office/d02701.txt
./government/Gen_Account_Office/gg96118.txt
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./government/Gen_Account_Office/im814.txt
./government/Gen_Account_Office/May1998_ai98068.txt
./government/Gen_Account_Office/pe1019.txt
./government/Gen_Account_Office/Sept27-2002_d02966.txt
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
```

Similarly, to filter by files **smaller than** 2 kilobytes **and are files**, the following command can be used:

`find -size -2k -type f`

Which gives the following output:

```
$ find -size -2k -type f
./plos/pmed.0020191.txt
./plos/pmed.0020226.txt
```

## Sources
This lab report was written by consulting the [Lab Report 3 guidelines](https://ucsd-cse15l-s23.github.io/week/week5/#week5-lab-report) and a [useful tutorial webpage on using the `find` command](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/).
