| Category          | Challenges                                   | Status          |
|-|-|-|
| Cryptography        | 1. Substitution0                              | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 2. Substitution1                               | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 3. Substitution2                             | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 4. La Cifra De                                |![Not Done](https://img.shields.io/badge/Status-Not%20Done-red) |
|                            | 5. Waves over Lambda                              | ![Not Done](https://img.shields.io/badge/Status-Not%20Done-red) |
|                            | 6. Pixelated                           | ![Done](https://img.shields.io/badge/Status-Done-brightgreen)  |
|                            | 7. C3                          | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |


---
# Substitution0


## Soln
```
ZGSOCXPQUYHMILERVTBWNAFJDK

Qctcnrel Mcptzlo ztebc, fuwq z ptzac zlo bwzwcmd zut, zlo gtenpqw ic wqc gccwmc
xtei z pmzbb szbc ul fqusq uw fzb clsmebco. Uw fzb z gcznwuxnm bsztzgzcnb, zlo, zw
wqzw wuic, nlhlefl we lzwntzmubwb—ex sentbc z ptczw rtukc ul z bsuclwuxus reulw
ex aucf. Wqctc fctc wfe tenlo gmzsh brewb lczt elc cjwtciuwd ex wqc gzsh, zlo z
melp elc lczt wqc ewqct. Wqc bszmcb fctc cjsccoulpmd qzto zlo pmebbd, fuwq zmm wqc
zrrcztzlsc ex gntlubqco pemo. Wqc fcupqw ex wqc ulbcsw fzb actd tcizthzgmc, zlo,
wzhulp zmm wqulpb ulwe selbuoctzwuel, U senmo qztomd gmzic Ynruwct xet qub eruluel
tcbrcswulp uw.

Wqc xmzp ub: ruseSWX{5NG5717N710L_3A0MN710L_357GX9XX}
```
- The given file.txt we're given, ruseSWX{...} suggests its a flag where ruseSWX == picoCTF
- Pasting the given text in dcode.en or https://quipqiup.com/ and then give the hint characters, we get the flag

## Flag
```
picoCTF{5UB5717U710N_3V0LU710N_357BF9FF}
```

---
# Substitution1

## Given Ciphertext
```
LKOb (bwvek ove lgqkhej kwj osgx) gej g kyqj vo lvrqhkje bjlhetky lvrqjktktvu. Lvukjbkgukb gej qejbjukjz dtkw g bjk vo lwgssjuxjb dwtlw kjbk kwjte lejgktftky, kjlwutlgs (guz xvvxstux) bitssb, guz qevmsjr-bvsftux gmtstky. Lwgssjuxjb hbhgssy lvfje g uhrmje vo lgkjxvetjb, guz dwju bvsfjz, jglw ytjszb g bketux (lgssjz g osgx) dwtlw tb bhmrtkkjz kv gu vustuj blvetux bjeftlj. LKOb gej g xejgk dgy kv sjgeu g dtzj geegy vo lvrqhkje bjlhetky bitssb tu g bgoj, sjxgs juftevurjuk, guz gej wvbkjz guz qsgyjz my rguy bjlhetky xevhqb gevhuz kwj dvesz ove ohu guz qeglktlj. Ove kwtb qevmsjr, kwj osgx tb: qtlvLKO{OE3AH3ULY_4774LI5_4E3_L001_6J0659OM}
```

## Soln
- We used **quipqiup**,an automated cryptogram solver to decipher the text.
- We equated `qtlvLKO = picoCTF` to extract the correct flag.

## Flag
```
picoCTF{FR3QU3NCY_4774CK5_4R3_C001_6E0659FB}
```

---

# Substitution2

## Given Ciphertext
```
LKOb (bwvek ove lgqkhej kwj osgx) gej g kyqj vo lvrqhkje bjlhetky lvrqjktktvu. Lvukjbkgukb gej qejbjukjz dtkw g bjk vo lwgssjuxjb dwtlw kjbk kwjte lejgktftky, kjlwutlgs (guz xvvxstux) bitssb, guz qevmsjr-bvsftux gmtstky. Lwgssjuxjb hbhgssy lvfje g uhrmje vo lgkjxvetjb, guz dwju bvsfjz, jglw ytjszb g bketux (lgssjz g osgx) dwtlw tb bhmrtkkjz kv gu vustuj blvetux bjeftlj. LKOb gej g xejgk dgy kv sjgeu g dtzj geegy vo lvrqhkje bjlhetky bitssb tu g bgoj, sjxgs juftevurjuk, guz gej wvbkjz guz qsgyjz my rguy bjlhetky xevhqb gevhuz kwj dvesz ove ohu guz qeglktlj. Ove kwtb qevmsjr, kwj osgx tb: qtlvLKO{OE3AH3ULY_4774LI5_4E3_L001_6J0659OM}
```

## Soln
-  We used **quipqiup** to decipher the text.
- We equated vqkmKFL{=picoCTF{  but  didnt get the flag
- I changed the solving mode to "solve (statistics)" which gave me the flag

## Flag
```
picoCTF{N6R4M_4N41Y515_15_73D10U5_42EA1770}
```

---


# Pixelated 

**Flag**: `picoctf{d562333d}`


Two scrambled PNG images and a hint to "try stacking them." After downloading the two PNG files, I attempted to solve the challenge by stacking the images in various ways.

## Soln

1. **Initial Attempt:**
   - I tried reducing the opacity of one image and stacking it with the other, as well as rotating the images, but this didn’t reveal any clear results.

2. **Python Solution:**
   - I  used a Python program using **PIL (Python Imaging Library)** to stack the images and attempt to extract the hidden flag.

   Here's the Python code I used:

   ```python
   from PIL import Image

   # Open images and convert to "RGBA" for transparency handling
   img1 = Image.open("scrambled1.png").convert("RGBA")
   img2 = Image.open("scrambled2.png").convert("RGBA")

   # Blend images (change alpha if needed)
   stacked = Image.blend(img1, img2, alpha=0.5)

   # Show and save the output
   stacked.show()
   stacked.save("output.png")

*Changing contrast/saturation etc revealed flag
![image](https://github.com/user-attachments/assets/7a7935ea-0bea-44bd-b097-eae9994987c9)

---




# C3

**Flag:** `picoctf{adlibs}`

# How you approached the challenge:

- We are given 2 files,

 *ciphertext*: `DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl`
  
and

_convert.py_ file:
```
import sys
chars = ""
from fileinput import input
for line in input():
  chars += line

lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""

prev = 0
for char in chars:
  cur = lookup1.index(char)
  out += lookup2[(cur - prev) % 40]
  prev = cur

sys.stdout.write(out)
```

We can figure out the ciphertext using the following program:
```
import sys

# Cipher lookup strings
lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

# Prompt for input
chars = input("Enter the ciphertext: ")

# Output variable
out = ""

# Decrypting the ciphertext
prev = 0
for char in chars:
    if char in lookup2:
        cur = (lookup2.index(char) + prev) % 40  # Reverse the calculation
        out += lookup1[cur]  # Map back to lookup1
        prev = cur  # Update prev for the next iteration
    else:
        out += char   

# Print the decrypted text
print("Decrypted text:", out)
```
### Terminal Output

```
Enter the ciphertext: DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl
Decrypted text: #asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():       
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print chars[i] #prints
        b += 1 / 1
```
![image](https://github.com/user-attachments/assets/bbe47300-e2ab-4245-9495-4777c0caefcf)



Running the output obviously doesn't give the flag, nor does it output anything at all so I figured out this must have been a text that needed to be 

```
chars =  """#asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print chars[i] #prints
        b += 1 / 1 
"""

b = 1
output = ""
for i in range(len(chars)):
    if i == b ** 3:  # Process characters at cube indices
        print(chars[i], end="")  # Print without newlines
        b += 1
print("\t is the Flag " , output)
```

```
adlibs   is the Flag  
```
---
I used `print("\t is the Flag " , output)`( for better readability/aesthetic purpose, the output was getting printed before the  string for some reason)
