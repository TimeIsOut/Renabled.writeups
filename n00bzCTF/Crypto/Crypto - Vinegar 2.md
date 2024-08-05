# Crypto - Vinegar 2 (135 points)
## Writeup Author - slzzpp

---
### Task
Never limit yourself to only alphabets!

Attached files: [chall.py](assets/vinegar2/chall.py) [enc.txt](assets/vinegar2/enc.txt)

---
### Solution
In short, it is necessary to analyze the encryption algorithm in the file "chall.py "and try to write a decryption algorithm.
Let's analyze the encryption algorithm:
1) Creating a list from our alphabet (for a '"custom Vigener table")
```
alphanumerical = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890!@#$%^&*(){}_?'
matrix = []
for i in alphanumerical:
	matrix.append([i])

output:
[ ['a'], ['b'], ['c'], ['d'], ['e'], ['f'], ['g'], ['h'], ['i'], ['j'], ['k'], ['l'], ['m'], ['n'], ['o'], ['p'], ['q'], ['r'], ['s'], ['t'], ['u'], ['v'], ['w'], ['x'], ['y'], ['z'], ['A'], ['B'], ['C'], ['D'], ['E'], ['F'], ['G'], ['H'], ['I'], ['J'], ['K'], ['L'], ['M'], ['N'], ['O'], ['P'], ['Q'], ['R'], ['S'], ['T'], ['U'], ['V'], ['W'], ['X'], ['Y'], ['Z'], ['1'], ['2'], ['3'], ['4'], ['5'], ['6'], ['7'], ['8'], ['9'], ['0'], ['!'], ['@'], ['#'], ['$'], ['%'], ['^'], ['&'], ['*'], ['('], [')'], ['{'], ['}'], ['_'], ['?'] ]
```

2) Changing the list so that each line contains a cyclically shifted version of the alphabet string
```
idx=0
for i in alphanumerical:
	matrix[idx][0] = (alphanumerical[idx:len(alphanumerical)]+alphanumerical[0:idx])
	idx += 1

output:
[ ['abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890!@#$%^&*(){}_?'], ['bcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890!@#$%^&*(){}_?a'], ['cdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890!@#$%^&*(){}_?ab'], ['defghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890!@#$%^&*(){}_?abc'], ... ]
```

3) We read the flag from the file and remove the spaces, set the key, check that the length of the key is equal to the length of the flag and initialize three empty lists: for the indexes of the flag, key and encrypted values.
```
flag=open('../src/flag.txt').read().strip()
key='5up3r_s3cr3t_k3y_f0r_1337h4x0rs_r1gh7?'
assert len(key)==len(flag)
flag_arr = []
key_arr = []
enc_arr=[]
```

4) Next, we find the index of each character from the flag string in the alphanumeric string and adds these indexes to the flag_array list.
```
for y in flag:
	for i in range(len(alphanumerical)):
		if matrix[i][0][0]==y:
			flag_arr.append(i)

output:
[62, 5, 0, 36, 43, 62, 74, 7, 17, 24, 33, 32, 18, 22, 51, 50, 7, 40, 29, 77, 36, 66, 78, 21, 15, 37, 17, 35, 62, 77]
```

5) Similar to the previous one, only for the secret key
```
for y in key:
	for i in range(len(alphanumerical)):
		if matrix[i][0][0]==y:
			key_arr.append(i)

output:
[36, 20, 15, 37, 17, 78, 7, 2, 19, 10, 24, 5, 35, 7, 38, 23, 17, 36, 6, 39, 79]
```

6) Here, for each flag\[i] symbol, we find its index in the matrix, and then select a symbol from the matrix at the position determined by the corresponding index from key_arr. Adding encrypted characters to enc_array. We combine all the characters from enc_arr into a string and writes them to a file enc.txt.
```
for i in range(len(flag)):
	enc_arr.append(matrix[flag_arr[i]][0][key_arr[i]])
encrypted=''.join(enc_arr)
f = open('enc.txt','w')
f.write(encrypted)
```

After we have figured out how the encryption algorithm works, we will write a decryptor
```
# Alphabet used for encryption and decryption
alphanumerical = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890!@#$%^&*(){}_?'
matrix = []

# Create a matrix with cyclic permutations of the alphabet
for i in alphanumerical:
    matrix.append([i])

idx = 0
for i in alphanumerical:
    matrix[idx][0] = (alphanumerical[idx:len(alphanumerical)] + alphanumerical[0:idx])
    idx += 1

# Function to find the index of a character in the alphabet
def find_index(char):
    for i in range(len(alphanumerical)):
        if matrix[i][0][0] == char:
            return i
    return -1

# Function for decryption
def decrypt(encrypted, key):
    # Ensure the length of the key matches the length of the encrypted text
    assert len(key) == len(encrypted), "The length of the key must match the length of the encrypted text"
    
    flag_arr = []
    key_arr = []
    decrypted_arr = []

    # Convert the encrypted text into indices
    for y in encrypted:
        flag_arr.append(find_index(y))
    
    # Convert the key into indices
    for y in key:
        key_arr.append(find_index(y))

    # Decryption: find the original characters of the flag
    for i in range(len(encrypted)):
        # Use reverse transformation
        decrypted_char = alphanumerical[(flag_arr[i] - key_arr[i]) % len(alphanumerical)]
        decrypted_arr.append(decrypted_char)

    # Join characters into a string
    decrypted = ''.join(decrypted_arr)
    return decrypted

# Example usage of the decryption function
encrypted = "*fa4Q(}$ryHGswGPYhOC{C{1)&_vOpHpc2r0({" 
key = '5up3r_s3cr3t_k3y_f0r_1337h4x0rs_r1gh7?'
decrypted_flag = decrypt(encrypted, key)

print("Decrypted flag:", decrypted_flag)
```
---
### Flag

```
n00bz{4lph4num3r1c4l_1s_n0t_4_pr0bl3m}
```
