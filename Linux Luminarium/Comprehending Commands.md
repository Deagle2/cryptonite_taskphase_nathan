#Challenge 2: Comprehending Commands
## Cat: not the pet but the command
cat is most often used for reading out files, like so:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
*`cat` is most often used for reading out files..*
To obtain the flag
> cat flag 

## Catting absolute paths
cat for an absolute path 

To obtain flag
> cat /flag

## More catting practice 
File is in a hidden directory
cd cmd cannot be used

## grepping for a needle in a haystack 
_grep_: Primarily searches within files for specific patterns or text strings. It operates on the contents of files.

_find_: Searches for files and directories in a filesystem based on various criteria, such as name, type, size, and more. It operates on the file system structure.

to obtain flag
> grep pwn.college

## Listing files
Introduction to *ls* cmd - List files/directories
To obtain the flag
> ls challenge
> /challenge/run

## Touching Files
*touch* cmd introduction - Creation of a file

To Obtain flag
> touch /tmp/pwn
> touch /tmp/college
> /challenge/run

## Removing files
*rm* cmd - Removing files

To obtain flag 
> rm delete_me
> /challenge/check

## Hidden Files
*ls -a* can be used to list hidden files, starting with .`file`

