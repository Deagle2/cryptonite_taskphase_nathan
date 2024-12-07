# m00nwalk

**Flag:** `picoCTF{beep_boop_im_in_space}`

## How you approached the challenge:

- I started the CTF by playing the wav file with the a spectrogram tool to try my luck but it didn't read unfortunately.
- The challenge said "Decode this message from the moon.", for which I researched and found about Slow-scan television (SSTV) encoding which is a picture transmission method used during the moon landing 
- I installed RX-SSTV, an SSTV decoder and I played the .wav file using the same device the RX-SSTV was installed in and played for which I got a clear image
- Mode for RX-SSTV was given as a hint, CMU's Mascot Scotty is a dog, therefore the mode is `Scottie-1`

###  Clear Image with Flag 
![image](https://github.com/user-attachments/assets/27738834-4fc5-40ad-b3d6-e0dbff8352b1)

### RX-SSTV tool 
![image](https://github.com/user-attachments/assets/3819c157-4602-4135-b5a5-af0ede0c6412)





## What you learned through solving this challenge:

1. SSTV -  A type of message encoding for picture Transmission
2. Usage of SSTV Decoding tools

## Other incorrect methods you tried:

- Put the .wav file in a spectrogram tool 
- Playing the .wav file through another device to RX-SSTV, this caused noise and the image generated but was distorted
  
![image](https://github.com/user-attachments/assets/969e5980-94c5-491b-8857-a613a2da184f) Distorted Image


## References

- [reference 1](https://www.qsl.net/on6mu/rxsstv.htm)


---

# tunn3l v1s10n

**Flag:** `flag`

## How you approached the challenge:

- The objective of this challenge is to recover the given file. We are given a corrupt file which doesn't open.

- I started off with looking at the EXIF & Metadata of the file on an online tool which reveals the given is  a .bmp file
![image](https://github.com/user-attachments/assets/24c94e32-c8b8-4b62-9131-47954d1a062a)

- I used https://hexed.it/, an online hexeditor tool to attempt to fix the corrupt .bmp file.

  By comparing the corrupt file to another bitmap file, here I've used wikipedia's as an example
  ![image](https://github.com/user-attachments/assets/b8412f45-0edf-45b8-906e-1f48a7e01598)

1. Blue - Width of the bitmap in pixels
2. Green - Height of the bitmap in pixels. Positive for bottom to top pixel order.
3. 1st Yellow Highlighed  - Offset where the pixel array (bitmap data) can be found
4. 2nd Yellow - Number of bytes in the DIB header (from this point)


- Fixing the first line was simple as it was just replacing the `BA D0` twice with 36 00 and 28 00 respectively

- Fixing the second half was a bit tricky as editing the width value and saving wouldn't fix the corrupted file

- Editing the Height values of the `.bmp` file did the trick
![blob](https://github.com/user-attachments/assets/67499cf3-ecf8-4148-a59d-9410066e187b)



*Additional Info*: Playing around with Hexeditor values, by changing only the Number of bytes in the DIB header i.e., 28 00 and Height of image as eg:- `36 03 00 00` saving the file gives us the following, whihc still gives us the flag: 
![blob](https://github.com/user-attachments/assets/ed4bc639-b7ff-4570-86c9-64aa722aafbc)

## What you learned through solving this challenge:

1. Understood .bmp file structure


## Other incorrect methods you tried:

- Renaming the file to end with .bmp
- Changing the file to a png

References

- [reference 1](https://hexed.it/)
- [reference 2](https://en.wikipedia.org/wiki/BMP_file_format#Example_1)

---

# Trivial File Transfer Protocol

**Flag:** `picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}`

# How you approached the challenge:

- We start of the challenge with a file given to us, tftp.pcapng, I wasn't familiar with the extension and though it was a png
``` 
      $ file tftp.pcapng 

      tftp.pcapng: pcapng capture file - version 1.0
```
- Renaming the extension to a png didnt work. After searching up the pcapng extension, we learn that its a packet capture format for network analysis, hinting to   wireshark so I uploaded the file into wireshark and fortunately there is export in the form of .TFTP.

- After exporting the file to my file explorer the file opens up 6 different files given below:
![image](https://github.com/user-attachments/assets/004edf4e-ec8a-4d1e-bcac-4440e71d7e62)

-  I started with opening the 3 different images which didnt give me much info, then opened up program.deb which contained 2 folders `debian` and `usr`, the bin folder under /usr, bin normally means executable files are present, bin means binary executables, opening bin we see a file called steghide (nothing much), the share folder didnt have much info either.

-  The only hint/info that kept popping up was steghide *(for later)*

-  Instructions.txt and plan file has the following text respectively `GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA` & `VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF`

- You can use https://www.dcode.fr/ to figure out the obfuscated text or random jumbled text, first we figure out what type of encryption it is. I found out that the text is ROT13 Cipher (Shift cipher), decrypting it gives the following:

![image](https://github.com/user-attachments/assets/ea333bc4-f903-4f6d-8872-04ea5d0f35aa)
![image](https://github.com/user-attachments/assets/013f8d01-9349-410d-a53a-62ac0ce1d175)

- They give us a hint to check out the photos, meaning there is hidden data in the bmp file, additionally it says "a program to hide it with `DUEDILIGENCE`", I figured out the program used must have been steghide, due to the many hints in the folder, the passphrase must have been `DUEDILIGENCE` too.
 ```
  $ steghide extract -sf picture3.bmp

  Enter passphrase: 
  wrote extracted data to "flag.txt".
 ```
( Luckily I started with *picture3.bmp*, *picture1* and *picture2*  bitmap files dont seem to have the same passphrase as picture3 )
Opening the file flag.txt gives us the flag



# What you learned through solving this challenge:

1. Wireshark for network analysis basics, filtering, exporting etc
2. Have used steghide for other ctfs before, but improved my skills.

# Other incorrect methods you tried:

- Decrypting didnt work for Substitution cipher or Hill cipher
- Wasn't sure about the extension .pcapng, so tried to change it into .png but didn't work, later learnt that the extension was a Packet capture format where wireshark can be used
- The passphrase didn't work for picture1.bmp or picture2.bmp

# References

- [Wireshark](https://www.wireshark.org/)
