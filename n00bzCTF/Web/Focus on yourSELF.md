Focus on yourSELF - 429 Points
---
Author - _MeRa_
---
Task Describtion
---
![image](https://github.com/user-attachments/assets/fb536a1f-a5fc-45f5-86a9-cd1669f496b1)
---
Brief Solution
---
Vulnerability - Local File Inclusion (LFI) in view function

Impact        - One can read files in host OS.

Fix           - principle of least privilege, cleaning user input.

---
Full Solution
---
![image](https://github.com/user-attachments/assets/32737baa-79f1-4236-9bc6-893f356d568d)

After instance launched we've got Image Gallery service with only two funcs:
                                     1. View stored images
                                     2. Upload them
Clicking View button we see in URL image GET param with nature.jpg filename as value, that means 
LFI.
Let't change filename on smth interesting. For example /etc/passwd file. Spoiler: we see nothing,
just because of application contatinates internal path for image (e.x. /app/assets/) and entered path (image.jpg)
That's why we need to go upper in dirs, to get /etc/passwd

![image](https://github.com/user-attachments/assets/7fdd804c-a7ff-44bb-be53-e5873ba44534)

We've got image. Cool. But it is in Base64. Now we should to decode it.

![image](https://github.com/user-attachments/assets/b9858d3b-f611-44c2-8868-38c092e7ed4e)

Yep. It's LFI. The Task name hints us to read smth... self) Sooo, lets read /proc/self/environ to 
read local variables.

![image](https://github.com/user-attachments/assets/aac971c9-8ec9-403c-aaa0-5d409aa0f3ae)

n00bz{Th3_3nv1r0nm3nt_det3rmine5_4h3_S3lF_8e6c5eacaef6}

Baaaam!
