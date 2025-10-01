# Easy Frequency Analysis question

## Flag: Author - James Joyce; Book - Ulysses

```

—👂🥴🤡😉🥶👂🤪🥶 😙🥳 😙🙀🤡😙😉😍 🥳😍👂. 
Decodes to the Latin opening of a religious service, as chanted by Buck Mulligan in Ulysses:

—Introibo ad altare Dei.

```

# Spiral cipher

## Flag: taskphase{4r73m1s_n0_fOWL_PL4YPL5y}

```
Solution:
Spiral 7x7 grid, read clockwise. You get taskphase{4r73m1s_n0_fOWL_PL4YPL5y}paddingpadding but the last bit can dumped

t a s k p h a
W L _ P L 4 s
O i n g p Y e
f d n g a P {
_ d i d d L 4
0 a p } y 5 r
n _ s 1 m 3 7
```
# Averages 3 letters to make cipher
cipher: GGGIIIFFFIIIGGGDDDGGGAAABBB

```
I tried splitting the string into triplets and finding the average, which gave me G I F I G D G A B but I couldn't make sense of it.
I also tried finding the average of all occurrences of each letter using its numerical value and dividing by 3, but this also produced gibberish:
U R F D A B
For example, for G: (7*9)/3 = 21 ==> U
```


# Hill Cipher Development

The Hill Cipher works using matrix multiplication and modular arithmetic (mod 26) to encrypt text.
It groups them the plain text in pairs or sometimes triplets to later multiply with the Key matrix
### Encryption
1. Convert letters to numbers (A1Z26 cipher)
2. Choose a nxn key matrix. Eg:- For pairs use 2x2 matrix
3. Multiply the key matrix with the plaintext matrix vector then reduce to `mod 26`.
4. Convert numbers back to letters to get ciphertext.
### Decryption
   Find the inverse of the key matrix mod 26
