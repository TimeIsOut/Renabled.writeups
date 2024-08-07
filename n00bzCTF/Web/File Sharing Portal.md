File Sharing Portal - 478 Points
---
Author - _MeRa_
---
Task Describtion
--

![image](https://github.com/user-attachments/assets/81981fee-4363-401b-a7fc-0ae99936abd6)

---
Brief Solution
---

Vulnerability - SSTI in Unpacked File

Impact - Remote Code Execution (RCE), that leads to full compromise of system.

Fix - Forget about formatting strings in Template Rendering. Use render_template_string arguments.

---
Full Solution
---
![image](https://github.com/user-attachments/assets/8cc208cc-71b9-4645-86e1-ad59d4aa4a93)

Once opened this task, you'd think, that File Upload Vulneratbilities. But it's... More interesting.

Let's look at sources.

![image](https://github.com/user-attachments/assets/d350fd69-ac70-453a-961e-644dd8a1d964)

As you see, after unpacking .tar file, function renders <a> tag, that includes name - variable, that will be added by formatting.

So, if your file is template, func will happily render it. Fortunatly for us.

Checking SSTI

![image](https://github.com/user-attachments/assets/2382b779-4bab-4653-abb0-d981a2ce27aa)

Cool. Here we go

![image](https://github.com/user-attachments/assets/73298e9d-e053-4769-988f-60d2c363d922)

I left the part with searching payloads for RCE and ls, just because it's borring)

The main part :)

![image](https://github.com/user-attachments/assets/a3021a0b-c593-4505-9d4b-8f327233df0e)

![image](https://github.com/user-attachments/assets/bceaa9a4-1da7-4525-b575-93632310ea8b)


Ta Daaa!
