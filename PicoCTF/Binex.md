| Category          | Challenges                                   | Status          |
|-|-|-|
| Binary Exp        | 1. Hijacking                             | ![Not Done](https://img.shields.io/badge/Status-Not%20Done-red) |
|                            | 2. Format String 0                               | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 3. Format String 1                           | ![Not Done](https://img.shields.io/badge/Status-Not%20Done-red) |
|                            | 4. Buffer Overflow 0                              |![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                            | 5. Buffer Overflow 1                           | ![Not Done](https://img.shields.io/badge/Status-Not%20Done-red) |
|                            | 6. babygame01                         | ![Not Done](https://img.shields.io/badge/Status-Not%20Done-red) |


# Buffer Overflow 0

**Flag:** `picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}`

## How you approached the challenge:

- We are given 2 files, on opening *vuln.c* we can inspect the code. We see that the program has used strcpy and gets functions which are not safe, meaning they do not have "boundary checks", which means we can do buffer overflow.
- char buf2[16] in line 17 means 16 bytes is allocated to buf2 (buffer size of 16), meaning the program might overflow if the input exceed 16 bytes.
- Hint 2 : If you try to do the math by hand, maybe try and add a few more characters. Sometimes there are things you aren't expecting.
- After connecting using netcat `nc  saturn.picoctf.net 52504` we have to input the a number of characters, in order to get the flag we try to do buffer overflow
- Using the hint we can try adding a few more characters, by trial and error method I found out that 19 characters is the breaking point/buffer overflow point.
- Cmd 1 has 19 characters. Cmd 2 has 20 characters which was the breaking point/buffer overflow.
- This meant that at 20 characters input I got the flag as seen in the screenshot below
![image](https://github.com/user-attachments/assets/55e3673a-0ee2-4497-ab48-71eed1e9e24c)


---
# format string 0

**Flag:** `picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_dc0f36c4}`

## How you approached the challenge:


- We are given 2 hints: This is an introduction of format string vulnerabilities. "Look up "format specifiers" if you have never seen them before." 
& "Just try out the different options". We can try out the second hint to obtain the flag in 2 steps 


```
Welcome to our newly-opened burger place Pico 'n Patty! Can you help the picky customers find their favorite burger?
Here comes the first customer Patrick who wants a giant bite.
Please choose from the following burgers: Breakf@st_Burger, Gr%114d_Cheese, Bac0n_D3luxe
```

- For the above you had to enter the name of correct "burger", which we can guess as `Gr%114d_Cheese`

```
Gr                                                                                                           4202954_Cheese
Good job! Patrick is happy! Now can you serve the second customer?
Sponge Bob wants something outrageous that would break the shop (better be served quick before the shop owner kicks you out!)
Please choose from the following burgers: Pe%to_Portobello, $outhwest_Burger, Cla%sic_Che%s%steak
```

- Out of Breakf@st_Burger, Gr%114d_Cheese and Bac0n_D3luxe, `Gr%114d_Cheese` is the only string containing a format specifier `%`. In this context it is known as a width specifier (`%114`)

- Out of Pe%to_Portobello, $outhwest_Burger and Cla%sic_Che%s%steak, `Cla%sic_Che%s%steak` worked as it contains `%s`, a format specifier 
 

![image](https://github.com/user-attachments/assets/c257fe0c-111d-410e-97c7-e399ed863da5)



