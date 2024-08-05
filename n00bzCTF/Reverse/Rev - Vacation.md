# Rev - Vacation (100 points)
## Writeup Author - Gluk0zka

---

### Task
Attached files:
![run.ps1](assets/vac_run.ps1)
![output.txt](assets/vac_output.txt)


---

### Solution

Looking at the code written in PowerShell, you can see that the code applies the XOR operation with the key 3 to the flag ask codes.

```powershell
$newBytes.Add($_ -bxor 3)
```
We also know the output, so we can apply the XOR operation to the output with the correct key. Here is the python code **Don't forget to escape \\t**
```python
def decrypt(encrypted_text):
  decrypted_bytes = []
  for byte in encrypted_text.encode('ascii'):
    decrypted_bytes.append(byte ^ 3)
  return bytes(decrypted_bytes).decode('ascii')
encrypted_text = "m33ayxeqln\sbqjp\\twk\{lq~" 
decrypted_text = decrypt(encrypted_text)
print(decrypted_text)
```

---
### Flag

```
n00bz{from_paris_wth_xor}
```
