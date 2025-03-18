## Secret of the Polyglot

**Flag**: `picoctf{f1u3n7_1n_pn9_&_pdf_90974127}`

### Steps to extract the flag
1. Download the file which is a pdf, it gives us the second half of the flag: `1n_pn9_&_pdf_90974127`
2. The hint is open the pdf in multiple ways, the second half of the flag gives us the clue to open the file as a png.
3. Open the file in the terminal and give the following commands to rename the pdf to a png file, display the png file
```──(kali㉿vbox)-[~]
└─$ cd /home/kali/Downloads/

┌──(kali㉿vbox)-[~/Downloads]
└─$ mv flag2of2-final.pdf flag2of2-final.png                                                                                                  
┌──(kali㉿vbox)-[~/Downloads]
└─$ display flag2of2-final.png
```
---
# Scan Surprise

### Flag: `picoCTF{p33k_@_b00_7843f77c}`

## Steps to extract the flag
1. **Download the file**
2. **Extract the contents** 
3. **Use Google Lens** 
4. The QR code reveals hidden text, which contains the flag.
