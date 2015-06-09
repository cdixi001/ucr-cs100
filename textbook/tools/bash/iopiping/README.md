#Piping and IO Redirection Examples

##What You Should Already Know
link to io redirection tutorial here
link to piping tutorial here
link to grep tutorial here

##Let;s Begin!
Fun and engaging sentence or rhetorical question here

Input/Output redirection and piping, as you should already know, make life infinitely easier by changing the flow of information between programs.
They accomplish this by changing file descriptors.

##Input/Output Examples
Input and Output operators establish communication between a program and a file.
Remember that the input and output operators can only be used on files! See linkhere for more information on input/output operators.
```
sort < inputfile
```
This command sorts the contents of inputfile based on the first letter in each line.
We can specify different flags (see `man sort`) to change how the lines are sorted.


```
ls > outputfile
```
This command will print nothing to the screen, but outputfile will contain the name of every file in the current directory on a new line.


```
sort < inputfile > outputfile
```
This command prints nothing to the screen. Outputfile contains the contents of inputfile in sorted order.



##Piping
Piping establishes communication between two programs.

In ```left | right```, the output of left acts as the input to right.

For example
```
ls | grep cpp
```
This command takes the ouput of `ls` and feeds it (technically pipes it) to `grep cpp`.
`ls` lists all the files in the current directory and of those files, grep will only display the ones that contain "cpp".

```
output goes here
```
Piping is often used in conjunction with `grep` or `sed` for finding phrases in files. Sentence about regular expressions and link to tutorail.

##Piping and IO Redirection
This is nothing to be scared of. Some sentence here explaining it is simple. IO involves program and file and that program can be used as one side of a pipe commad.

```
sort < inputfile | grep 'cs100'
```
All the lines in inputfile containing `cs100` are displayed in sorted order.

With piping and IO Redirection, there isn't ever just one way to do things.
There isn't really a best way either.
The best way is a subjective balance of shortness and readability.

Probably better to just show output than explain with a giant paragraph. At the end of this command, outputfile looks like this:
```
outputfile contents here
```

##Interesting Stuff
```
sed 's/word1/word2/g' < file1 > file2
```
Places contents of `file1` in `file2` with all instances of `word1` replaced with `word2`.
`file1` does not change.
`sed` is a particularly interesting and important command for searching and replacing.
It has many features which you can read about [here] (LINK HERE).


```
ls -lR | grep .cpp | vim -
```
This command looks recursively through the current directory and displays only the lines that contain "cpp" in vim (instead of the screen).
The `-` is a `vim` parameter that tells `vim` that the file to edit is read from `stdin`.
The `grep .cpp` portion of the code may be modified for any string in file names.


```
ps | grep problemprocess | grep -v grep | awk '(print $2)' | xargs kill
```
http://unix.stackexchange.com/questions/30759

This command kills a process based on its name by obtaining its process id. Explanation of each pipe follows.

```
wget -O -http://izbicki.me/ | grep -E -o "\b[a-z A-Z 0-9.-] + @[a-z A-Z 0-9.-] + \.[a-z A-Z 0-9.-] + \b"
```
Link to quiz maybe? Or change it up a bit. Gets email addresses from a webpage. `grep` does most of the work with its powerful regular expression ability, but its input is from the wget command.

##Conclusion
Programs become extremely useful when they can communicate with each other. By themselves, they are already powerful, but piping and i/o redirection give us a way to combine programs to perform otherwise complex tasks.
