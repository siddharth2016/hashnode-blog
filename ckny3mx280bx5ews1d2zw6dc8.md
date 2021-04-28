## Shell Script Basics

The best thing about GNU/Linux is that it’s packed with utilities that improve productivity immensely. One such utility is a shell that can help accomplish complex tasks with just a few sequences of commands. Most of the time, users operate shell in an interactive way. 

However, it becomes really productive when we leverage the scripting capabilities of the shell.

In this article, we are going to explore the basics of shell scripting, how simple `echo` command can be used in a shell script file, how to write comments, working with variables and conditionals.

Keeping it short and simple, let's get started!

---

### Shell Script Printing

When we are working with shell scripts printing on the output screen is called echoing which can be done using `echo`.

```bash
$ echo "Hello Shell"
Hello Shell
```

Let's do this inside a shell script file. Follow the below steps:

1. Create a file, name it whatever you want with the `.sh` extension. Let's say `echo_script.sh`.
2. Add following inside the file - `echo "Hello Shell"`, hit `Save` and open a terminal on the file location.
3. On the terminal, write - `$ bash echo_script.sh` and hit enter, you should be able to see - `Hello Shell`.

### Shell Script Comments

Comments are used to improve the readability of the script. Shell uses the pound `#` symbol for comments. A line beginning with the pound `#` symbol is ignored by the shell interpreter during execution. 

The script given below shows the usage of the comment:

```bash
# Display Hello Shell using echo command of shell, filename.sh
echo "Hello Shell"
```

Go to terminal and type - `$ bash filename.sh` (replace `filename` with whatever name you have given) and hit enter. You should be able to see - `Hello Shell` without printing anything given after the `#` symbol.

### Shell Script Variables

We can define variables to store information, which can be accessed within the shell script. There are certain rules we need to follow while defining variables:

1. The variable name can contain any combination of letters from A-Z or a-z, digits from 0-9 or an underscore (_) character.
2. The variable name should start with a letter or an underscore character.
3. Variables are case sensitive.

By convention, shell variables are defined in the upper case. Given below is a simple script, which shows the usage of a variable within it:

```bash
$ cat hello.sh
NAME="CodeKaro"
echo "Hello $NAME"
```

`cat` command is used to display the content of a file given after that. Try your hands on it.

So, we have a file `hello.sh` which contains a variable `NAME` which we used in the `echo` statement as `$NAME` that is after the `$` symbol. Here we saw variable declaration and how inside double quotes a variable can be used.

If you hit - `$ bash hello.sh` and hit enter, you should be able to see - `Hello CodeKaro` on the terminal.

### Shell Script Conditionals

Like other programming languages, shell supports conditional expressions like – *if*, *if-else* and *case*. Let us understand this with simple examples:

1. `if` expression: In case we want to verify whether a file exists or not, we can use the if expression, as follows:

```bash
$ touch file.txt #this creates a file
 
$ cat file_existance.sh
if [ -e file.txt ]; then
echo “file.txt file exists”
fi
```

The script given above generates the following output when it is executed:

```bash
$ bash file_existance.sh
file.txt file exists
```

2. `if-else` expression: Let us modify the above script to generate output when the file does not exist:

```bash
$ rm file.txt
$ cat file_existance.sh
if [ -e file.txt ]; then
echo “file.txt file exists”
else
echo “file.txt file does not exists”
fi
```

Type following and hit enter:

```bash
$ bash file_existance.sh
file.txt file does not exists
```

3. `case` statement: Shell provides a switch statement-like functionality using the case statement. Let us understand this with the example given below:

```bash
$ cat case_statement.sh
read -p “Enter the day: “ DAY
 
case $DAY in
Mon) echo “Today is Monday”
;;
 
Tue) echo “Today is Tuesday”
;;
 
Wed) echo “Today is Wednesday”
;;
 
*) echo “Unknown day”
;;
esac
```

The script given above generates the following output when it is executed:

```bash
$ bash case_statement.sh
Enter the day: Mon
Today is Monday
```

```bash
$ bash case_statement.sh
Enter the day: Tue
Today is Tuesday
```

```bash
$ bash case_statement.sh
Enter the day: Invalid
Unknown day
```

In the `case` statement, an asterisk (*) denotes a default case.

Well, that's it from me. 

We covered printing, variables, comments and conditionals, not too much, right? 

---

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏

> *Image Credits - <a href='https://www.freepik.com/vectors/book'>pch.vector</a>*