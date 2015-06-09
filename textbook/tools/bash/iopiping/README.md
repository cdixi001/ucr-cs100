#Piping and IO Redirection Examples


##What You Should Already Know
link to io redirection tutorial here
link to piping tutorial here
link to grep tutorial here

##Let's Begin!
Fun and engaging sentence or rhetorical question here

Input/Output redirection and piping make life infinitely easier by changing the flow of information between programs.
They accomplish this by changing file descriptors.

##Input/Output Examples
Input and Output operators establish communication between a program and a file.
Remember that the input and output operators can only be used on files! See linkhere for more information on input/output operators.
```
ls -l < inputfile
```
Instead of printing all files/folders in the current directory with detailed info, this command will only print (with detailed info) the files/folders listed in `inputfile` (separated by newline).

```
ls > outputfile
```
This command will print nothing to the screen, but `outputfile` will contain the name of every file in the current directory on a new line.


```
ls -l < inputfile > outputfile
```
This command prints nothing to the screen.
Outputfile contains detailed info about the files listed in inputfile.



##Piping
Piping establishes communication between two programs.

In `left | right`, the output of left acts as the input to right.
The pipe `|` connects `stdout` of `left` to `stdin` of `right`.

For example
```
ls | grep cpp
```
This command takes the ouput of `ls` and feeds it (technically pipes it) to `grep cpp`.
`ls` lists all the files in the current directory and of those files, grep will print to `stdout` the ones that contain "cpp".

Piping is often used in conjunction with `grep` or `sed` for finding phrases in files.
Sentence about regular expressions and link to tutorial.

##Piping and IO Redirection
IO involves program and file and that program can be used as one side of a pipe command.

```
sort inputfile | grep 'cs100' >> outputfile
```
All the lines in `inputfile` containing `cs100` appended to `outputfile` in sorted order.

With shell commands, there is never just one way to do things.
There isn't really a best way either.
The best way is a subjective balance of shortness and readability.
The following also appends all lines of `inputfile` containing `cs100` in sorted order to `outputfile`.
```
cat inputfile | grep 'cs100' | sort >> outputfile
```
It first prints `inputfile` to `stdout`, searches for "cs100", and then sorts those lines into `outputfile`.


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
Programs become extremely useful when they can communicate with each other.
By themselves, they are already powerful, but piping and i/o redirection give us a way to combine programs to perform otherwise complex tasks.
