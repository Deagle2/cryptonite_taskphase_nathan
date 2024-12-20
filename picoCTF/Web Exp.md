# Challenge: Forbidden Paths

**Flag:** `picoCTF{7h3_p47h_70_5ucc355_e5fe3d4d}`
---
### How you approached the challenge:
- Three `.txt` files are given, and an input field is provided on the webpage to specify which file to read.
- The file lives in `/usr/share/nginx/html/`, so we enter `../../../flag.txt` in the input field to reach `/flag.txt`. The `../` is used to navigate up one level in the directory structure. (Both `../../../flag.txt` and `../../../../flag.txt` worked.)
- By clicking the "Read" button, the webpage redirects to a different page ending with `/read.php` and displays the flag.

![blob](https://github.com/user-attachments/assets/363cb2ea-ceac-4c63-b4ba-84b24fc5c0a7)
---
### What you learned through solving this challenge:
1. Directory traversal can be used to navigate to other directories and access files outside the intended directory.

### Other incorrect methods you tried:
- Changed the URL to end with `/flag.txt`.
- Changed the URL to `../../../flag.txt`.

## References:
    N/A

***

# Challenge: Cookies

**Flag:** `picoCTF{3v3ry1_l0v3s_c00k135_96cdadfd}`

---

### How you approached the challenge:
- The webpage has a search bar with the prompt `snickerdoodle`, so I entered the same exact text and searched, which returned the response: `I love chocolate chip cookies!`
- Since the CTF name was "cookies," I suspected the flag might be stored in the cookies. Using **Inspect Element > Application > Storage > Cookies**, I found two cookies: `authname` and `name`.
- The `authname` cookie didn’t seem useful, but the `name` cookie had the value 0. I changed the value to 1, which gave me the same response: I love chocolate chip cookies!. 
- Suspecting I was on the right track, I tested further by changing the value to -1, which resulted in an invalid cookie error.
- Changing the value to other positive numbers, such as 2, 3, etc., returned different texts. Finally, when I set the value to 18, I received the flag.

---

![blob](https://github.com/user-attachments/assets/20653a5e-f89c-4851-97af-c927deacc532)


---

### What you learned through solving this challenge:
1. Manipulating cookie values could reveal sensitive information.
   


### Other incorrect methods you tried:
- Changing the cookie value to a negative number.
- Entering cookie in the search bar instead of the given prompt.



## References:
N/A


*** 

# Challenge: SOAP

**Flag:** ` picoCTF{XML_3xtern@l_3nt1t1ty_540f4f1e} `

## How you approached the challenge:

- We are tasked with finding the hidden file in /etc/passwd. A hint is given pointing to `XML external entity Injection`, also known as XXE attack.
- The only interactive elements on the website are 3 buttons ` Details `, we can normally exploite XXE vulnerability to  retrieve the /etc/passwd file by submitting the following XXE payload:
- Go to Dev Tools > Network Tab, I clicked on the first "Details" button
- Send a new request by adding a new XXE attack payload in the body and click on the response to get the flag
 
 ```
  <!--?xml version="1.0" ?-->
<!DOCTYPE foo [<!ENTITY example SYSTEM "/etc/passwd"> ]>
<data>&example;</data>

 ```

- Explanation of payload:
  1. <!DOCTYPE> allows us to define an external entity, in this case `&example`, foo is placeholder
  2. `[<!ENTITY example SYSTEM "/etc/passwd"> ]>`, gives example as the contents inside /etc/passwd
  3. The XXE payload defines an external entity, a placeholder `&example`, whose value is the contents of the /etc/passwd file. When the XML is read by the             program, it may automatically replace `&example`, with the actual data from that file. 
![image](https://github.com/user-attachments/assets/6a3dee48-850f-43dd-b887-30536dce69e8)

***

### What you learned through solving this challenge:

1. SOAP - ( Simple Object Access Protocol) is a message convention that permits appropriated components of an application to convey. It uses XML to send messages over a network(HTTP)
2. XXE attack, There are many types of XXE  attacks, the method used in this ctf is where an external entity is defined containing the contents of a file, and returned in the application's response.

### Other incorrect methods you tried:

- It took a few tries to send the payload as it failed the first few tries (no response)

### References

- [PORTSWIGGER](https://portswigger.net/web-security/xxe)
- [W3SCHOOLS-SOAP](https://www.w3schools.com/XML/xml_soap.asp)
- [reference 2](https://book.hacktricks.xyz/pentesting-web/xxe-xee-xml-external-entity)
---
***
# Additional Challenges
***
# Challenge: Picobrowser

**Flag:** `picoctf{s3cr3t_ag3nt_84f9c865}`

---
### How you approached the challenge:

- On opening the website I got a warning that I was not in "picobrowser", the flag would only be accessible on using picobrowser 

- A technique of "User-agent spoofing/masking"/"Header Manipulation" , a method of changing the User-Agent using Developer Tools

- Start with opening Inspect Element > Network Tab > Network Conditions  > User Agent > Uncheck ` Use browser default` > Enter a custom User-Agent string that matches "picobrowser".

![blob](https://github.com/user-attachments/assets/8ca7269a-a191-413d-9c97-b4676d0fadfc)
---
![blob](https://github.com/user-attachments/assets/001aed03-f9c0-462b-b669-190208b13411)
---

### What you learned through solving this challenge:

1.  User Agent switching

#### References

- [reference 1](https://www.searchenginejournal.com/change-user-agent/368448/)


***

# Challenge: login 

**Flag:** `picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}`

How you approached the challenge:

- https://login.mars.picoctf.net/
- Checking the page source by CTRL+shift+u  you see
```
<!doctype html>
<html>
    <head>
        <link rel="stylesheet" href="styles.css">
        <script src="index.js"></script>
    </head>
    <body>
        <div>
          <h1>Login</h1>
          <form method="POST">
            <label for="username">Username</label>
            <input name="username" type="text"/>
            <label for="username">Password</label>
            <input name="password" type="password"/>
            <input type="submit" value="Submit"/>
          </form>
        </div>
    </body>
</html>
```
- On clicking on index.js (hyperlink), I saw a string  of long text that looks like base64, on converting the given text we obtain the flag

![blob](https://github.com/user-attachments/assets/9e98e120-d2e7-4fef-a7e0-095a89c1144d)

![blob](https://github.com/user-attachments/assets/81788187-dafd-4402-9440-568d36d04e92)

---

### What you learned through solving this challenge:

- N/A

### Other incorrect methods you tried:

- SQL Injection methods 

### References

- [reference 1](https://www.base64decode.org/)

***
