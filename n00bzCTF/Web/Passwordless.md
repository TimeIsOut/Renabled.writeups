Passwordless - 100 Points
---
Author - _MeRa_
---
Task Describtion
--
![Task](https://github.com/user-attachments/assets/59767728-f062-4952-8af6-b790aa665f86)
---
Brief Solution
---

Vulnerability  - Open source file with authorization algorithm. String "str(uuid.uuid5(leet,'admin123'))" makes user administrator
Impact         - Unauthorized user can become administrator in app. In our case we get the flag :)
Fix            - Hide the source file for beginning and storing sensitive variables in vaults, not in sources

---
Full Solution
---
![image](https://github.com/user-attachments/assets/2ed297f5-012f-428c-a1af-43885462cb70)

As you see, in code we have two functions: 
                the first one works with usernames and rendering index.html
                the second one is responsible for getting flag and identifying the Admin.
To get flag we need admin uid, that is in if. For it we need leet variable and 'admin123'. Two arguments we found, enter it in Python
IDLE to get answer.

![image](https://github.com/user-attachments/assets/d5f03f0c-0d39-42a0-a994-e88554c5f681)

and now visit the /uid route

n00bz{1337-13371337-1337-133713371337-1337}

![image](https://github.com/user-attachments/assets/b723ab66-8e88-470d-88eb-e011eab90adf)

Booom!
