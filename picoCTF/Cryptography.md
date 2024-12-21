# Challenge: Custom Encryption
**Flag :** `picoCTF{custom_d2cr0pt6d_8b41f976}`

# How you approached the challenge:

We're given 2 files, `enc_flag` and a python file `flag_info`
`enc_flag` contains:|
```
a = 94
b = 21
cipher is: [131553, 993956, 964722, 1359381, 43851, 1169360, 950105, 321574, 1081658, 613914, 0, 1213211, 306957, 73085, 993956, 0, 321574, 1257062, 14617, 906254, 350808, 394659, 87702, 87702, 248489, 87702, 380042, 745467, 467744, 716233, 380042, 102319, 175404, 248489]
```
The .py contains:

![image](https://github.com/user-attachments/assets/3c2711a4-007c-4b19-9edf-7444b8fd7503)
![image](https://github.com/user-attachments/assets/a60733b2-8cb1-4843-9210-852570d3574f)



We can use the follow python program to get the flag:
```
def generator(g, x, p):
  return pow(g, x) % p

def decrypt(cipher, key):
  decrypted_text = ""
  for number in cipher:
      decrypted_num = number // (key * 311)
      decrypted_text += chr(decrypted_num)
  return decrypted_text

def dynamic_xor_decrypt(ciphertext, text_key):
  decrypted_text = ""
  key_length = len(text_key)
  for i, char in enumerate(ciphertext):
    key_char = text_key[i % key_length]
    decrypted_char = chr(ord(char) ^ ord(key_char))
    decrypted_text += decrypted_char
  return decrypted_text

a = 94
b = 21
cipher = [131553, 993956, 964722, 1359381, 43851, 1169360, 950105, 321574, 1081658, 613914, 0, 1213211, 306957, 73085, 993956, 0, 321574, 1257062, 14617, 906254, 350808, 394659, 87702, 87702, 248489, 87702, 380042, 745467, 467744, 716233, 380042, 102319, 175404, 248489]
p = 97
g = 31


u = generator(g, a, p)
v = generator(g, b, p)
shared_key = generator(v, a, p)
ciphertext = decrypt(cipher, shared_key)
print(dynamic_xor_decrypt(ciphertext, "trudeau"))
```


- Here I found out "Diffie-Hellman Key Exchange" was used
- `generator(g, x, p)` is used for the formula of g^x mod p // g^x % p
  where 
p: A prime number used as the modulus.
g: A primitive root modulo p
x: The private key used for generating the public key.

(the private and public keys in Diffie-Hellman are not the same)
- u = generator(g, a, p) is the public key of a
- v = generator(g, b, p) is the public key of b
- shared_key = generator(v, a, p) // This is equal to `(g^(a*b)) % p`
-  The word "trudeau" is used as a static encryption key for the XOR operation.
-  Running the program gives us the flag
  

## Reference
1) [Encryption Method](https://www.geeksforgeeks.org/implementation-diffie-hellman-algorithm/)

---

# C3

**Flag:** `picoctf{adlibs}`

# How you approached the challenge:

- We are given 2 files,

 *ciphertext*: `DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl`
  
and

_convert.py_ file:
```
import sys
chars = ""
from fileinput import input
for line in input():
  chars += line

lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""

prev = 0
for char in chars:
  cur = lookup1.index(char)
  out += lookup2[(cur - prev) % 40]
  prev = cur

sys.stdout.write(out)
```

We can figure out the ciphertext using the following program:
```
import sys

# Cipher lookup strings
lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

# Prompt for input
chars = input("Enter the ciphertext: ")

# Output variable
out = ""

# Decrypting the ciphertext
prev = 0
for char in chars:
    if char in lookup2:
        cur = (lookup2.index(char) + prev) % 40  # Reverse the calculation
        out += lookup1[cur]  # Map back to lookup1
        prev = cur  # Update prev for the next iteration
    else:
        out += char   

# Print the decrypted text
print("Decrypted text:", out)
```
### Terminal Output

```
Enter the ciphertext: DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl
Decrypted text: #asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():       
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print chars[i] #prints
        b += 1 / 1
```
![image](https://github.com/user-attachments/assets/7195f852-0146-4ca0-8729-f63300c42f94)


Running the output obviously doesn't give the flag, nor does it output anything at all so I figured out this must have been a text that needed to be 

```
chars =  """#asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print chars[i] #prints
        b += 1 / 1 
"""

b = 1
output = ""
for i in range(len(chars)):
    if i == b ** 3:  # Process characters at cube indices
        print(chars[i], end="")  # Print without newlines
        b += 1
print("\t is the Flag " , output)
```

### Terminal Output

```
adlibs   is the Flag  
```
---
I used `print("\t is the Flag " , output)`( for better readability/aesthetic purpose, the output was getting printed before the  string for some reason)

# What you learned through solving this challenge:

1. Custom Cyclical Cipher concepts
2.  Mapping in C3, lookup1 contains the characters of the encrypted message, lookup2 contains the characters used to form the plaintext.

# Other incorrect methods you tried:

- Used a cryptogram solver for the cipher text
- In the decrypted text for the last program, I used only `#asciiorder, #fortychars, #selfinput, #pythontwo`, which did give me an output but not the whole flag ( got adl as output)

  ---

  # miniRSA

**Flag:** `picoCTF{n33d_a_lArg3r_e_606ce004}`

How you approached the challenge:

- We're given the following values of N, e (public key), c (ciphertext):
```
 N: 29331922499794985782735976045591164936683059380558950386560160105740343201513369939006307531165922708949619162698623675349030430859547825708994708321803705309459438099340427770580064400911431856656901982789948285309956111848686906152664473350940486507451771223435835260168971210087470894448460745593956840586530527915802541450092946574694809584880896601317519794442862977471129319781313161842056501715040555964011899589002863730868679527184420789010551475067862907739054966183120621407246398518098981106431219207697870293412176440482900183550467375190239898455201170831410460483829448603477361305838743852756938687673
  e: 3

ciphertext (c): 2205316413931134031074603746928247799030155221252519872649649212867614751848436763801274360463406171277838056821437115883619169702963504606017565783537203207707757768473109845162808575425972525116337319108047893250549462147185741761825125
```
- We can use an RSA decoder, since I already have experience in dcode.fr I used the website to decode the 3 values, inputting the values directly gives us the flag

![image](https://github.com/user-attachments/assets/a92addc4-1560-4abc-be1e-8e3d881b498b)


# What you learned through solving this challenge:

1. I learnt a basic concept of RSA. RSA is an asymmetric cryptography algorithm, where asymmetric means the public and private keys are different.


# References

- [RSA-CIPHER](https://www.dcode.fr/rsa-cipher)
- [rsa](https://www.tutorialspoint.com/cryptography/cryptography_rsa_algorithm.htm)
