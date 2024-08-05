# Programming - Sillygoose (267 points)
## Writeup Author - Gluk0zka

---

### Task
Attached files:
```
-- sillygoose.py
```

**sillygoose.py:**
```python
from random import randint
import time
ans = randint(0, pow(10, 100))
start_time = int(time.time())
turns = 0
while True:
    turns += 1

    inp = input()

    if int(time.time()) > start_time + 60:
       print("you ran out of time you silly goose") 
       break

    if "q" in inp:
        print("you are no fun you silly goose")
        break

    if not inp.isdigit():
        print("give me a number you silly goose")
        continue

    inp = int(inp)
    if inp > ans:
        print("your answer is too large you silly goose")
    elif inp < ans:
        print("your answer is too small you silly goose")
    else:
        print("congratulations you silly goose")
        f = open("/flag.txt", "r")
        print(f.read())

    if turns > 500:
        print("you have a skill issue you silly goose")
```
---

### Solution

After analyzing the code, we can see that this is a simple children's game. Let's write a code that will reduce the uncertainty by 2 times each time. Thus, he will be able to guess the number in 500 attempts.
```python
import socket  
  
def main():  
  host = 'ip' 
  port = 1234
  
  with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as client_socket:  
    client_socket.connect((host, port))  
    low = 0  
    high = pow(10, 100)
    for _ in range(500):
      guess = (low + high) // 2  
      client_socket.send(str(guess)+'\n').encode())  
      response = client_socket.recv(1024).decode()  
      print(f"Guess: {guess}, Response: {response}")  
      if "too large" in response:  
        high = guess - 1  
      elif "too small" in response:  
        low = guess + 1  
      else:  
        print(f"Correct answer: {guess}")  
        return
    print("Failed to find the answer within 500 attempts.")  
if _name_ == "_main_":  
  main()
```

---
### Flag

```
n00bz{y0u_4r3_4_sm4rt_51l1y_g0053}
```