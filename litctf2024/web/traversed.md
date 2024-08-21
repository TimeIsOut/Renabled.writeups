Traversed - 123 Points
---
Author - _MeRa_
---
Task Describtion
---

![image](https://github.com/user-attachments/assets/90bb72cf-103a-49a2-a3ce-31a8ea8641c6)

---
Brief and Full solution
---

Vulnerability - LFI & Path Traversal

Impact - Reading local files

Fix - Clearing user input and giving user less privileges

Task solved by two moves:

The first one is reading /proc/self/environ for info... 

![image](https://github.com/user-attachments/assets/2f0ba3e6-ac6f-4553-88ce-ea23d1e756e3)

There is PWD, that equals /app. Sooooo... App is launched in that dir.

The second step is entering in the dir and some guessing for flag file

![image](https://github.com/user-attachments/assets/de6db2a2-ec9a-4051-9ec9-fb0c492101ee)
