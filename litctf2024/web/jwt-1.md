jwt-1 - 111 points
---
Author - _MeRa_
---
Task Describtion
---

![image](https://github.com/user-attachments/assets/c4e292e4-8307-49ea-8dda-1e629fe1cf6c)

---
Brief and Full Solution
---

Vulnerability - Service doesn't check JWT

Impact - One can edit cookie and become admin...

Fix - Set up normal check of JWT

![image](https://github.com/user-attachments/assets/2985c6ea-3d1a-414a-83b5-b2bbde35146d)

Simple site with Flag button, that give you "Unauthorized", when click on it. So... We need to register

![image](https://github.com/user-attachments/assets/b1116dac-11c0-43b7-9bf6-5714aa293b33)

Login

![image](https://github.com/user-attachments/assets/9c2ba19e-b134-4bb8-978a-b69903ba991b)

Flag button is still signing "Unauthorized" . Let's check token

![image](https://github.com/user-attachments/assets/37d7eeba-3f10-49d2-8ebd-21c08c57d07a)

I thought, that we need to bruteforce secret, then get admin panel. But there is much easier.

...Let's stupidly edit payload and see, what we'll get

![image](https://github.com/user-attachments/assets/26b2ffc2-3a3b-41a5-a1b5-433f87b59ed0)
![image](https://github.com/user-attachments/assets/2e552e3a-7a34-4934-822f-1cdb8dadcab7)

It's one of the most strange tasks of all)




