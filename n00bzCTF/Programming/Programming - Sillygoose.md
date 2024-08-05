# Programming - Sillygoose (267 points)
## Writeup Author - Gluk0zka

---

### Task
There's no way you can guess my favorite number, you silly goose. Author: Connor Chang

Attached files:
[sillygoose.py](assets/sillygoose.py)

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
