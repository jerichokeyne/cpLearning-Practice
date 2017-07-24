Welcome to the guide on learning the Linux command line. Let's jump right in.

### Introduction
To open a terminal in Ubuntu go over to the dash and start a search for "Terminal" then open the application.
On most default installations you can also press Ctrl+Alt+T to open a new terminal.

### Understanding the prompt
When you first open the terminal you should see something similar to:
```Bash
test@ubuntu-vm:~$
```
`test` - is your username

`ubuntu-vm` - is your hostname

`~` - is your current location (in this case the 'home folder')

`$` - means you are running as a standard user (you will see `#` if you are running as `root`)


### First Command
Here's a useful command to know:
```Bash
ls
```
When you run this command you should get something similar to this:
```
Desktop  Documents  Downloads  Music  Pictures  Projects  Public  Templates  Videos
```
What you are seeing is all of the files in your current directory (directory is used to mean folder in Unix)
There's also a decent chance you saw everything in blue (if you didnt see any colors try running `ls --color`)
When you run `ls` and see blue text that means that file is a directory (yes, folders are files in Unix/Linux)
Grey text means it is a regular file
Green text means it is executable

If you want to see what files are in a directory use:
```Bash
ls $fileName
````
Replace `$fileName` with the name of a file, for example: `ls Desktop`

### Moving around
Now, seeing the files are good and all, but what if we want to go into one of those directories.
```Bash
cd $fileName
```
Again replace `$fileName` with the name of a directory (you will get an error if you try to `cd` into a file that's not a directory), for example: `cd Documents`
Now you should see your prompt change to something like:
```Bash
test@ubuntu-vm:~/Documents$
```
Now if you want to go back home you have a few different options
```Bash
cd ~
```
That is the proper way but you can also run just `cd` to get back home

Another useful command to know is:
```Bash
cd ..
```
This will take you up one directory

Another useful command is:
```Bash
pwd
```
This will print your present working directory

### Making files
If you want to just create a file you have a few different options, but you should stick to this for now:
```Bash
touch $fileName
```
This will create a file with the name of $fileName in the current directory, again replace $fileName with an actual file name

Note: if you want to make a file in a different directory run
```Bash
touch path/to/file
```
For example: `touch Desktop/hello.txt' or 'touch ~/Desktop/hello.txt', these both can do the same thing. The first uses a relative path, it will make a file named 'hello.txt' in a directory named 'Desktop' that is in your current directory. The second uses an absolute path, it will make a file named 'hello.txt' in a directory named 'Desktop' in your home folder

Now if you want to make a new directory run:
```Bash
mkdir $fileName
```
This will create a directory with the name of $fileName in the current directory

### Editing files
There are lots of file editors, but if you just want to append text to a file or overwrite file you can use the following:
```Bash
echo $text >> $fileName
```
Replace $text with whatever you want and $fileName with the name of a file
This will append the file with the text you write, for example: `echo hello world >> hello.txt` will append 'hello world' to 'hello.txt'
If 'hello.txt' doesn't exist it will be created

If you don't want to append text use:
```Bash
echo $text > $fileName
```
Be careful with that command, it will completly overwrite the file with the new text

Now, what if you want to view those files you created:
```Bash
cat $fileName
```
That will print out the contents of a file

Now what if you want an actual text editor
You have lots of different choices, here I will mention two, but feel free to go lookup more (eg: vi, vim, emacs, ed)
For a graphical editor run:
```Bash
gedit $fileName
```
This will open up a file in a normal looking text editor
Ctrl+s is save
Ctrl+f is search
Ctrl+o is open a new file
Ctrl+n is open a new window
Ctrl+q is exit

For a command line based editor run:
```Bash
nano $fileName
```
There are two bars at the bottom stating common shortcuts, it also says the version of nano and the file name on the top bar
Ctrl+o is save (write out)
Ctrl+w is search
Ctrl+x is exit

### Finding Files
If you want to find a file run:
```Bash
find -name "$fileName"
```
This will recursively search through all the files in the current directory to find a file
If you want to find all files with a certain extension (eg: .txt) run:
```Bash
find -name "*.txt"
```
If you want to find all files with a certain string ($string) in the name run:
```Bash
find -name "*$string*"
```

### Finding Text in Files
If you want to find a string ($string) in a file ($fileName) run:
```Bash
grep $string $fileName
```
This will return all lines with $string inside of $fileName

If you need the $n lines around that line run:
```Bash
grep -C $n $string $fileName
```
This will give the line with $n lines before that and $n lines after, using `-A` or `-B` instead of `-C` will give you just the lines after or before
