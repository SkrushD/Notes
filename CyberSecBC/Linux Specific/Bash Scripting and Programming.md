### Bash Scripting and Programming
Compound commands
	are several individual commands that  we would originally run separately _linked_ together to create a new command
Review
```bash
">" # output to a file
">>" # appends to an existing file
"|" # runs a command in successsion using information from the last command
```
New compounding operators
```bash
";" # executes in order whether or not any of these commands error out
"&&" # executes commands in order until a command errors out. will only run the command if the prior command was successful
``` 
Variables
	: is a container used to hold a specific value. Different variables can hold different types of data.
	- myvariable=/etc/passwd
		sets myvariable to /etc/passwd. Use with $myvariable
	- adding quotes will allow you to add text to your variable commands
	- nested commands in variable `$(ls)`
	- nest with n\ moves output down one line
		"list dirs: `\n$(ls)`
			Strings
			: data types composed of a sequence of textual and/or numerical characters.
			Integers
			: a data type that is a whole number value

##### Day 2

Comments
	: non-executeable text within the script  denoted by "#"
		Placing a # in front of a line tells bash to ignore it i.e. "commented out"
if command
```bash
if [ value = value ]
	then #command goes here
	else #command if false goes here
fi
# options for comparing values include
&& # check if a second condition is true and must be true for then to run
|| # checks if a second condition is true and if either condition  was true runs then
```
Extra conditionals
```bash
	= # this strings is equal to another
	== # if two strings are equal.
    != # if two strings are not equal
    -gt # if one integer is greater than another.
    -lt # if one integer is less than another
    -d /path # checks for existence of a directory.
    -f filename # checks for existence of a file
```
Global Variables
```bash
-   $USER // user name as value   
-   $UID // user id as value  
-   $(<command>) // command as a value 
-   $days // list of the days of the week
-   $months // list of the months in the year
```
For loops
	: allow us to runa block of code multiple times in a row, without having to repeatedly enter that code
```bash
for each in $list
	do # command goes here
done
```
Capitalism.sh
```bash
for day in ${days[@]}
	do
	if [ $day = 'sun' ] || [ $day = 'sat' ]
	then
	echo "it is $day. take it easy
	else
	echo "it is $day. get to work!"
	fi
done
```
