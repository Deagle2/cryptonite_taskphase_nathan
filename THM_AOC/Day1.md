## Looks like the song.mp3 file is not what we expected! Run "exiftool song.mp3" in your terminal to find out the author of the song. Who is the author? 

### To obtain flag
- Run exiftool song.mp3 in the terminal after downloading the file from the website
- In the exiftool data, near artist you see - Tyler Ramsbey

## The malicious PowerShell script sends stolen info to a C2 server. What is the URL of this C2 server?

### To obtain flag
- Run ` exiftool somg.mp3 `, next to cmd line arguments there's a github link, go to the link
- You will see  $c2Url = "http://papash3ll.thm/data" which is the flag

## Who is M.M? Maybe his Github profile page would provide clues?

### To obtain flag

- Basic Osint, go to the github link which is https://github.com/MM-WarevilleTHM > M.M repository which will contain the name

## What is the number of commits on the GitHub repo where the issue was raised?


### To obtain flag
- https://github.com/Bloatware-WarevilleTHM/CryptoWallet-Search/commits/main/
