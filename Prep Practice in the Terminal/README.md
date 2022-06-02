# Summary


***Practice the Terminal***

From practicing the command line assignment I found out that there is a lot of information to be discovered that was never according to my mind, especially having a [cheatsheet](https://github.com/h4mz411y/reading-notes/blob/main/Prep%20Practice%20in%20the%20Terminal/CHEATSHEET.md) which helped a LOT which my speed and accurcay.


The terminal offers you access to your computer's file and folder hierarchy, and you navigate using your keyboard in the same way that you would in Finder or Explorer. It takes some getting used to, but building a mental model in this area is essential to working with code.


## What is the command line?

The command line is a text interface for your computer. Just like Windows Explorer on Windows or Finder on Mac OSX it lets you navigate through the files and folders of your computer, but it is completely text based. The command line works by typing commands against a prompt, which then gets passed to the operating system of the computer that runs these commands.

## Navigation around the terminal in WSL
* Once you opened up your terminal, type in the following after the Dollarsign or > sign and hit enter the dollar sign or > is the prompt, you don’t have to retype that in the terminal, only the characters that come after them)

```
$ pwd
```
* Now that you know how to tell where you are in your computer, you might ask yourself: how I do know which files are in a directory? That’s where the ls command comes in handy
```
$ ls

```

* Let’s say we wanted to move to the Desktop folder: just type in your terminal
```
cd <your directory>
```
## File and Directory Manipulation

* Many commands and programs can create files. The most basic method of creating a file is with the touch command. This will create an empty file using the name and location specified.

```
cd
touch file1
```

* Create a Directory with “mkdir”

```
cd
mkdir test
```