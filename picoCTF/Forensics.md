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
