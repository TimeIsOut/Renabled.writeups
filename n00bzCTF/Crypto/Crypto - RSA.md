# Crypto - RSA (100 points)
## Writeup Author - Gluk0zka

---

### Task
The cryptography category is incomplete without RSA. So here is a simple RSA challenge. Have fun! Author: noob_abhinav

Attached files:
[encryption.txt](assets/encryption.txt)

---

### Solution

First we need to understand what kind of values ​​we are given. C is an encrypted message, and n and e are public keys. And they are related by the formula.

```
C = M^e (mod n)
```
Thus, we do not know the original message (M) in the ASCI format. You can write a code or use an online decoder such as [this](https://www.dcode.fr/rsa-cipher).

---
### Flag

```
n00bz{crypt0_1s_1nc0mpl3t3_w1th0ut_rs4!!}
```
