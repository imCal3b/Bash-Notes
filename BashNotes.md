## Bash Commands  
--- 
A list of useful Bash (Bourne Again Shell) commands  
(Test Change!!)
---

**- Directories -**  
  
|Command|Option|Description|
|-------|------|-----------|
|pwd||prints the file path of the current working directory|
|cd||use to change directories|
|cd ~/ |~/ or ~|use to move into the home directory|
||./ or .|describes the current working directory|
|cd ..|..|use to move to the previous directory|
|cd -|-|use to move between previous directory (back/forth)|

---

|Command|Syntax|Example|
|-------|------|-------|
|locate|locate \<options\> \<search-text\>|\\$ locate first [or] \\$ locate ".txt"|  

The **locate** command is used to locate a specific file or directory. You can keep your search broad oif you dont know what exactly it is you're looking for, or you can narrow the scope by using wildcards or regular expressions.  

---

|Command|Syntax|Example|
|-------|------|-------|
|grep|grep \<options\> pattern \<file(s)\>|\$ grep "quantum computing" qc.txt|  

The **grep** command is used to search text for patterns specified by the user. There are often times where you will be tasked with finding a particular string or pattern within a file, but you dont know where to start looking.  

In the example  above, we are searching the qc.txt file for the string "quantum computing". This will search through and output the line in qc.txt that contains the string we were searching for.  

> *- Flags (options) -*  
>
> |Flag|Description|
> |-|-|
> |**-i**|Ignore the case sensitivity of the search statement|
> |**-o**|Print only the matched parts of a matching line|
> |**-v**|Select non-matching lines (invert selection)|  
>  
> *- Pattern Options -*   
>
> |Operator|Description|Example|
> |-|-|-|
> |**^\<text\>**|using the '^' operator tells grep to search for lines beginning with a specified pattern| ~\$ grep "^q" qw.txt|
> |__\*__|using the '\*' searches all files|~\$ grep "^q" \*|  
> |__\<text\>\$__|using the '\$' searches the end of each line for pattern|~\\$ grep "ing\\$" \*|
> |__.__|using '.' in a pattern allows any charactr to pass through|~\$ grep "^d...rwx" \*|
  
```bash
echo "find all lines in all files that begin with 'q'"
grep "^q" *

echo "find all lines in all files that end with 'ing'"
grep "ing$" *

echo "locate all the files that are directories"
ls -lt | grep "^d" *

echo "locate all directories with group rwx"
ls -lt | grep "^d...rwx" *
 ```

---

|Command|Syntax|Example|
|-------|------|-------|
|cat|cat \<options\> \<file(s)\> [operand] \<file(s)\>|\$ cat qw.txt > qubit.txt|  

The **cat** command is used to read a file, create a file, and concatenate (join/combine) files. The cat command can be joined with operands like redirect stdout ">" or pipe "|" to pass data from the file(s) cat was called on, to other files or to perform other operations on the initial file.  

---

|Command|Syntax|Example|
|-------|------|-------|
|less [or] more|less \<file\> [or] more \<file\>|\$ less qw.txt|  

the **less** or **more** command is used to view the contents of a text file without opening an editor. Its faster to use and theres no chance of you inadvertently modifying the file.  

The **more** command shows the document in the terminal. If it does not fit on one page (screen) it will show the file  in multiple pages, however, you cannot go backwards through the pages, only forwards.  

The **less** command shows the document in smaller incriments and allows you to scroll up and down through the file.

---

|Operand|Syntax|Example|
|-------|------|-------|
|>|\<command-w/-output\> *>* \<file\>|\$ cat qw.txt > qubit.txt|  
|>>|\<command-w/-output\> *>>* \<file\>|\$ cat Quantum.txt >> qubit.txt|  

The **>** operand reffers to *redirect stdout*. This takes the output from the preceding command (that you would typically see in the terminal) and sends it to a file you give the command.   
* A single > operator overwrites the file its pointing to. If the reveiving file is empty, it will be filled with the output of the initial command.
* Two >> operators are used to append data to the end of a file. If the receiving file already contains data, the new data will be added to the bottom of the file.  

In the case of the example above, the cat command combined with the redirect would concatenate the first file to the second file (concatenate qw.txt to qubit.txt). If the file right of the operand has not already been created, a new file will be created with the given name.  

---

|Operand|Syntax|Example|
|-------|------|-------|
|\||\<command-w/-output\> \| \<second-command\>|\$ cat qubit.txt \| wc -w > words.txt|  

The **|** operand reffers to *pipe*. A pipe takes the standard output of one command and passes it as the input to another.  

In the example above, the text of the qubit.txt file is being passed as the input to the next command, which is then redirecting its output to the text file words.txt using the redirect operand.  

---

|Command|Syntax|Example|
|-------|------|-------|
|cp|cp \<options\> \<source-file\> \<new-file-name [or] directory\>|\$ cp qw.txt quantum.txt|  

The **cp** command is used to copy or create a copy of a particular file. Along with the name of the source file, you also need to specify either a new fiile name to store the copy to or the directory you would like to make the copy to.  

In the example above we are copying the qw.txt file and storing the copy as quantum.txt. Alternatively we could've specified a new directory to store the copy of the qw.txt file.  

---

|Command|Syntax|Example|
|-------|------|-------|
|chmod|chmod \<options\> [permissions] \<file-name\>|\$ chmod g+rx ex.sh|  

The **chmod** command is used to modify the read, write, and excecute permissions of a particular file or directory for either the owner, members of the file's group, or other users. The permissions can be set such that each of the three classes of users have different permissions on the same file.  

There are situation you will come across where yoou will try to upload a file or modify a document and recieve an error message because you dont have access.  

*Examples of file permissions lines*  
> **Command: ~\$  _ls -l_**  
> drwxrwxr-x 3 vagrant vagrant 8328 Jan 13 04:32 seng265  
> -rwxrwxr-- 1 vagrant vagrant 4096 Jan 15 09:17 test.c  

|Permissions|# Dir. Entries|Owner|Group|Size|Mod. time/date|File Name|
|-----------|--------------|-----|-----|----|--------------|---------|
|drwxrwxr-x|3|vagrant|vagrant|8328|Jan 13 04:32|seng265| 
|-rwxrwxr--|1|vagrant|vagrant|4096|Jan 15 09:17|test.c|  

 

**Permissions:**  
The first statement in a line when listing the contents of a directory is the permissions statement for the files or directories within the current working directory.  

*Note: The owner of the file or directory has full control over the permissions.*  

We can get some valuable information about the permissions of a file or directory through reading the permissions line...  

|Type|User perm.|Group perm.|Other perm.|
|----|----------|-----------|-----------|
|**d**\|rwxrwxr-x|d\|**rwx**\|rwxr-x|drwx\|**rwx**\|r-x|drwxrwx\|**r-x**|  

**Type**  
The type of a file is identified by the file designator.  

|Identifier|Description|
|----------|-----------|
|-|Regular file|
|d|Directory|
|c|character device|
|l|symbolic link|
|p|named pipe|
|s|socket|
|b|block device|     

When using the *chmod* command to change file/directory permission, we must specify what changes we want to make. There are three categories that can be changed within the permissions statement to achieve different results...  

**<div align="center"> [permissions] = [class][operator][mode] </div>**      

**Class**  
The class defines who specifically we want to change permissions for.  

|Class|Description|
|-----|-----------|
|u|User - The owner of the file|
|g|Group - Users who are members of the files group|
|o|Other  - Users who are not the owner and not members of the files group|
|a|All - Identifies all users of the file (equivalent to "ugo")|  

**Operator**  
The operator defines whether we want to give or remove permission of a specified mode for a specified user.  

|Operator|Description|
|--------|-----------|
|+|Gives permission to a specified class for a specified mode|
|-|Takes away permission from a specified class for a specified mode|  

**Mode**  
The mode defines the type of ability we want to give to or take from a user for a particular file or directory.  

|Mode|Description|
|----|-----------|
|r|Read - Allows a user to read/access a file or directory|
|w|Write - Allows a user to write/modify a file or directory|
|x|Execute - Allows a user to excecute a file or directory|  
|-|No permission is given. No user can access the mode of which '-' is a place holder|  

---


 
