| Category          | Challenges                                   | Status          |
|-|-|-|
| Reverse Engineering        | 1. File-run1                                | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 2. File-run2                                | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 3. Safe Opener                              | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 4. Picker I                                 | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 5. Picker II                                | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 6. ARMssembly 0                             | ![Done](https://img.shields.io/badge/Status-Done-brightgreen)  |
|                            | 7. ARMssembly 1                             | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 8. Vault-Door-Training                      | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 9. Vault-Door-1                             | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 10. Vault-Door-3                            | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 11. Vault-Door-4                            | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 12. Vault-Door-5                            | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 13. Vault-Door-6                            | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |

---
---

# file-run1

## Flag
```
picoCTF{U51N6_Y0Ur_F1r57_F113_e5559d46}
```
### Solution
The file does not have execution permissions initially. We can modify its permissions using `chmod +x` to make it executable and then run it to reveal the flag.


1. Change the file permissions to make it executable:
   ```bash
   chmod +x run
   ```
2. Execute the file:
   ```bash
   ./run
   ```
---

# file-run2


## Flag
```
picoCTF{F1r57_4rgum3n7_96f2195f}
```

### Solution

We are given a file named `run`. 

The hint suggests running the file with an argument. 
We repeat the steps for file-run1 to make it executable.

1. Change the file permissions to make it executable:
   ```bash
   chmod +x run
   ```
2. 
   ```bash
   ./run
   ```
   Output:
   ```bash
   Run this file with only one argument.
   ```
3. With a single argument:
   ```bash
   ./run hi
   ```

Output:
```bash
The flag is: picoCTF{F1r57_4rgum3n7_96f2195f}
```

---

## Safe Opener

### **Flag**
Since the flag format follows `picoCTF{}` , the final flag is:
```
picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}
```

### Solution
We are given a Java file as shown above. 

Looking through the code
```java
public static boolean openSafe(String password) {
    String encodedkey = "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz";
```

The `encodedkey` is a **Base64-encoded string**. To retrieve the original password, we need to decode it.

#### Decoding the Encoded Key
We can use an **online Base64 decoder** like [dcode.fr/base-64-encoding](https://www.dcode.fr/base-64-encoding) or any other Base64 decoder.

After decoding the given string, we get the password:
```
pl3as3_l3t_m3_1nt0_th3_saf3
```

---

# Picker I

## Flag
```
picoCTF{4_d14m0nd_1n_7h3_r0ugh_ce4b5d5b}
```

### Solution

A Python program that takes user input and evaluates function calls dynamically using `eval()`.  is given as a file.
The script contains various functions, including one that reads and prints the flag in a hex-encoded format.


1. The `win()` function reads `flag.txt`, converts each character to hex, and prints it.
2. Running `win()`  directly gives the flag in hexadecimal format.
3. I tried to use a hex --> text/ascii converter but got an error, after a bit of tweaking I figured out that I had to remove the 0x prefix in the hexadecimal number.
4. _70 69 63 6f 43 54 46 7b 34 5f 64 31 34 6d 30 6e 64 5f 31 6e 5f 37 68 33 5f 72 30 75 67 68 5f 63 65 34 62 35 64 35 62 7d_ == **picoCTF{4_d14m0nd_1n_7h3_r0ugh_ce4b5d5b}**

---

# Picker II

## Flag  
```
picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_b924e8e5}
```

### Solution 

1. print(open('flag.txt', 'r').read())

---

# ARMssembly 0

## Flag 
```
picoCTF{DF0BACD4}
```

### Solution

- We get the output as  3742084308 
 -Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267  would be picoCTF{0055aabb}) 
- Converting we get DF0BACD4

---

# ARMssembly 1

**Flag:**: `picoCTF{0000001b}`

###  Solution

We're give the following file [chall_1.s](https://mercury.picoctf.net/static/7cc2b73e671f61f8dc2d40493fb62611/chall_1.S)
For what argument does this program print win with variables 81, 0 and 3?

The flag format is picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

The logic of the given program:

```
str w0, [sp, 12] ;  input x (passed in w0) is stored in [sp + 12]

mov w0, 81          ; w0 = 81
str w0, [sp, 16]    ; 81 stored in [sp + 16]

str wzr, [sp, 20]   ; Stores 0 at [sp + 20]

mov w0, 3           ; w0 = 3
str w0, [sp, 24]    ; stores w0 = 3 at [sp + 24]

ldr w0, [sp, 20]    ; Load 0 into w0
ldr w1, [sp, 16]    ; Load 81 into w1
lsl w0, w1, w0      ; Perform 81 << 0, so w0 = 81
str w0, [sp, 28]    ; Stores 81 at [sp + 28]

ldr w1, [sp, 28]    ; Load 81 into w1
ldr w0, [sp, 24]    ; Load 3 into w0
sdiv w0, w1, w0     ; Perform 81 / 3, so w0 = 27
str w0, [sp, 28]    ; Store 27 at [sp + 28]

```

- So finally [sp + 28] holds the value 27, where result = 27 - x
- If result == 0, the program prints "You win!". This means that the input x also has to be 27

  Finally convert 27 to a zero-padded 8-character hexadecimal string
  1) 27 in decimal = 1B in hexadecimal.
  2) Zero-pad to 8 characters, i.e., add leading zeros until the string is 8 characters long
 
     Giving us the flag as picoCTF{0000001b}


- LDR (Load Register) instructions in ARM architecture are used to load a register with a value from memory
- SDIV is an instruction in ARM that performs signed integer division, taking into account the signs of the two operands

---
# **Vault Door Training**

## **Flag** :
```
picoCTF{w4rm1ng_Up_w1tH_jAv4_be8d9806f18}
```

##  **Solution**

The flag is directly given in the java source file

### Code Snippet:
```java
public boolean checkPassword(String password) {
    return password.equals(" w4rm1ng_Up_w1tH_jAv4_be8d9806f18");
}
```

---
  # Vault Door 3

**Flag:** `picoctf{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}`

### Solution

- We're given the following java program file:
![image](https://github.com/user-attachments/assets/63383028-fa07-4db4-bcaf-28e39a442f44)

This vault uses for-loops and byte arrays and the hint we're given is to "Make a table that contains each value of the loop variables and the corresponding buffer index that it writes to". I wasn't experienced with Java so I used python to get the flag

```python
target = "jU5t_a_sna_3lpm18gb41_u_4_mfr340"

password = [''] * 32
for i in range(32):
    if i < 8: password[i] = target[i]
    elif i < 16: password[23 - i] = target[i]
    elif i % 2 == 0: password[46 - i] = target[i]
    else: password[i] = target[i]

print(''.join(password))
```

In short the logic of the following program is 
After making an emptry string of 32 characters 
1) First 8 characters (i < 8): Directly copied characters
2) Next 8 characters (8 ≤ i < 16): Placed in reverse order
3) Last 16 characters (i ≥ 16): 

    Even indices: Mirrored to reverse positions.

    Odd indices: Directly copied.

On running the program we get a text, adding picoctf{} to the text gets you the flag

---
# Vault Door 4

## Flag: `picoCTF{jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e}`

### Steps to Extract flag 

The flag is given in the java source file 

```java
byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0146, 064 ,
            'a' , '8' , 'c' , 'd' , '8' , 'f' , '7' , 'e' ,
        };
```

These are different types of numbering systems such as Hex, Octal & Decimals
We can either use an automation to first convert each to characters and join them,
 or do manually

```
myBytes = [
    106, 85, 53, 116, 95, 52, 95, 98,
    0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
    0o142, 0o131, 0o164, 63, 0o163, 0o137, 0o146, 0o64,
    ord('a'), ord('8'), ord('c'), ord('d'), ord('8'), ord('f'), ord('7'), ord('e')
]

password = ''.join(chr(b) for b in myBytes)
print("picoctf{"+password+"}")
``` 
Directly gives the flag as `picoctf{jU5t_4_bUnCh_0f_bYt?s_f4a8cd8f7e}`

---

# Vault Door 5

## Flag : `picoCTF{c0nv3rt1ng_fr0m_ba5e_64_e3152bf4}`

### Solution

```java
 String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTY1JTMzJTMxJTM1JTMyJTYyJTY2JTM0";
```
- Use a base 64 decoder like https://www.dcode.fr/base-64-encoding to convert the 3 strings and join them
- This gives us `%63%30%6e%76%33%72%74%31%6e%67%5f%66%72%30%6d%5f%62%61%35%65%5f%36%34%5f%65%33%31%35%32%62%66%34` which is url encoded
- On decoding we get `c0nv3rt1ng_fr0m_ba5e_64_e3152bf4` which is the flag

---

# Vault Door 6

## Flag
```
n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc
```

### Solution

- We are given a Java File 
Here is the code snippet:
```java
myBytes = {
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36,
        };
        for (int i=0; i<32; i++) {
            if (((passBytes[i] ^ 0x55) - myBytes[i]) != 0) {
                return false;
            }
        }
```
The encryption key is 0x55 

We can write a program to reverse the encryption using the given hint [ X ^ Y = Z, then Z ^ Y = X]


Code Snippet :
```python

# Given encrypted bytes
myBytes = [
    0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
    0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
    0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
    0xa , 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36,
]

# The XOR key used in the C++ code
xor_key = 0x55

# Recover the original passBytes
passBytes = [(b ^ xor_key) for b in myBytes]

# Convert to bytes for readability
decrypted_key = bytes(passBytes)

# Print the result
print("Decrypted Key:", decrypted_key.decode(errors='ignore'))
```

- It gives the output as `n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc`
---

