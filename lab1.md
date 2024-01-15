# Lab Report 1

## `cd`
* ### no args
```java
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd 
[user@sahara ~]$ pwd
/home
```
The working directory was `/home` when the command was run. After the command was run the working directory was the same. By adding no arguments after `cd`, there was no directory for the program to "change" into, so the working directory stayed the same. This output is not an error.

* ### path to /home/lecture1
```java
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
The working directory was `/home` when the command was run. After the command was run the working directory was `/home/lecture1`. Since I indicated what directory I wanted to change into as the argument, and that directory existed within the working directory (`/home`), the command changed directories into `/home/lecture1`. This output is not an error.

* ### path to /home/lecture1/messages/en-us.txt
```java
[user@sahara ~/lecture1/messages]$ pwd
/home/lecture1/messages
[user@sahara ~/lecture1/messages]$ cd en-us.txt 
bash: cd: en-us.txt: Not a directory
[user@sahara ~/lecture1/messages]$ pwd
/home/lecture1/messages
```
The working directory was `/home/lecture1/messages` when the command was run. After the command was run the working directory was the same. I got an error message because even though the file I changed into existed within the working directory, the specific file is not considered a directory that can be changed into. `cd` will only works with directories, not files.

## `ls`
* ### no args
```java
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
```
The working directory was `/home/lecture1` when the comand was run. The output was the list of files and directories that exist within the *same* `/home/lecture1` directory since I didn't add any arguments that'd indicate another directory to `ls` in. The output is not an error.

* ### path to /home/lecture1/messages
```java
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ ls messages
cy.txt  en-us.txt  es-mx.txt  zh-cn.txt
```
The working directory was `/home/lecture1` when the command was run (and the same after the command was run). The output was the list of files and directories within the `/home/lecture1/messages` directory because I used `messages` as the argument. The output is not an error. 

* ### path to /home/lecture1/messages/en-us.txt
```java
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ ls messages/en-us.txt 
messages/en-us.txt
```
The working directory was `/home/lecture1` when the command was run (and the same after the command was run). The output was the relative path to the file that I indicated in the argument. It printed exactly what I used as an argument. This is because there are no other files within a specific file. So the terminal will just spit out the only file in the "directory" that was typed, which in this case is the relative path to `en-us.txt` from `/home/lecture1`. 

## `cat`
* ### no args
```java
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ cat
```
The working directory was `/home/lecture1` when the command was run. There was no output and it seems the command is never finished executing. This is because `cat` is supposed to read the contents of a file, but in this case since I add no arguments to a file it tries to read the contents of the working directory, which it can't. That's why it results in this error.

* ### path to /home/lecture1/messages
```java
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ cat messages/
cat: messages/: Is a directory
```
The working directory was `/home/lecture1` when the command was run. There is a error message that indicates that the argument I entered is a path to a directory, not a file. This means it can't be read with the `cat` command. 

* ### path to /home/lecture1/Hello.java



```java
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}
```
The working directory was `/home/lecture1` when the command was run. The output is the contents of the `Hello.java` file that exists in the working directory because `Hello.java` was added as an argument after the `cat` command.
