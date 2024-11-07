# Forbidden Paths

**Flag:** `picoCTF{7h3_p47h_70_5ucc355_e5fe3d4d}`

### How you approached the challenge:
- Three `.txt` files are given, and an input field is provided on the webpage to specify which file to read.
- The file lives in `/usr/share/nginx/html/`, so we enter `../../../flag.txt` in the input field to reach `/flag.txt`. The `../` is used to navigate up one level in the directory structure. (Both `../../../flag.txt` and `../../../../flag.txt` worked.)
- By clicking the "Read" button, the webpage redirects to a different page ending with `/read.php` and displays the flag.

![blob](https://github.com/user-attachments/assets/363cb2ea-ceac-4c63-b4ba-84b24fc5c0a7)

### What you learned through solving this challenge:
1. Directory traversal can be used to navigate to other directories and access files outside the intended directory.

### Other incorrect methods you tried:
- Changed the URL to end with `/flag.txt`.
- Changed the URL to `../../../flag.txt`.

## References:
    N/A


---

# Cookies

**Flag:** `picoCTF{3v3ry1_l0v3s_c00k135_96cdadfd}`

---

## How you approached the challenge:
- The webpage has a search bar with the prompt `snickerdoodle`, so I entered the same exact text and searched, which returned the response: `I love chocolate chip cookies!`
- Since the CTF name was "cookies," I suspected the flag might be stored in the cookies. Using **Inspect Element > Application > Storage > Cookies**, I found two cookies: `authname` and `name`.
- The `authname` cookie didn’t seem useful, but the `name` cookie had the value 0. I changed the value to 1, which gave me the same response: I love chocolate chip cookies!. 
- Suspecting I was on the right track, I tested further by changing the value to -1, which resulted in an invalid cookie error.
- Changing the value to other positive numbers, such as 2, 3, etc., returned different texts. Finally, when I set the value to 18, I received the flag.

---

![blob](https://github.com/user-attachments/assets/20653a5e-f89c-4851-97af-c927deacc532)


---

## What you learned through solving this challenge:
1. Manipulating cookie values could reveal sensitive information.
   

---

## Other incorrect methods you tried:
- Changing the cookie value to a negative number.
- Entering cookie in the search bar instead of the given prompt.

---

## References:
N/A
