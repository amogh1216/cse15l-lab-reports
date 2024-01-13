# Lab Report 1

## `cd`
* ### no args:
```java
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd 
[user@sahara ~]$ pwd
/home
```
The working directory was `/home` before the command was run. After the command was run the working directory was the same. By adding no arguments after `cd`, there was no directory for the program to "change" into, so the working directory stayed the same. This output is not an error.

* ### path to /home/lecture1
```java
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
The working directory was `/home` before the command was run. After the command was run the working directory was `/home/lecture1`. Since I indicated what directory I wanted to change into, and that directory existed within the working directory (`/home`), the command changed directories into `/home/lecture1`. This output is not an error.

* ### path to /home/lecture1/messages/en-us.txt
```java
[user@sahara ~/lecture1/messages]$ pwd
/home/lecture1/messages
[user@sahara ~/lecture1/messages]$ cd en-us.txt 
bash: cd: en-us.txt: Not a directory
[user@sahara ~/lecture1/messages]$ pwd
/home/lecture1/messages
```
The working directory was `/home/lecture1/messages` before the command was run. After the command was run the working directory was the same. I got an error message because even though the file I changed into existed within the working directory, the specific file is not considered a directory that can be changed into. `cd` will only file into directories, not specific files.

## `ls`
* no args:
* path to /
* path to

## `cat`
* no args:
* path to /
* path to 
