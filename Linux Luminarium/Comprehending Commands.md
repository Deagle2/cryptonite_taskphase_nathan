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
__grep_: Primarily searches within files for specific patterns or text strings. It operates on the contents of files.

_find_: Searches for files and directories in a filesystem based on various criteria, such as name, type, size, and more. It operates on the file system structure.

to obtain flag
grep pwn.college

