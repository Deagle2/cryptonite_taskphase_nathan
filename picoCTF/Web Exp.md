# Forbidden paths

## Description
Can you get the flag?
We know that the website files live in /usr/share/nginx/html/ and the flag is at /flag.txt but the website is filtering absolute file paths. Can you get past the filter to read the flag?
Additional details will be available after launching your challenge instance.


## To Obtain Flag
  1. 3 .txt files are given and an input to type what to read is given in the webpage
  2.  The file lives in /usr/share/nginx/html/ so we enter ../../../flag.txt in the input field to reach /flag.txt. ` ../` is used to navigate up to one level of the directory 
  3. On clicking read button the webpage takes us to a different page ending with read.php and gives us the flag

### Flag 
picoCTF{7h3_p47h_70_5ucc355_e5fe3d4d}


