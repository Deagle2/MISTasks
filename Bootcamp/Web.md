## Index

- [SOAP](#soap)


# Challenge: SOAP

**Flag:** ` picoCTF{XML_3xtern@l_3nt1t1ty_540f4f1e} `

## Solution

- We are tasked with finding the hidden file in /etc/passwd. A hint is given pointing to `XML external entity Injection`, also known as XXE attack.
- The only interactive elements on the website are 3 buttons ` Details `, we can normally exploite XXE vulnerability to  retrieve the /etc/passwd file by submitting the following XXE payload:
- Go to Dev Tools > Network Tab, I clicked on the first "Details" button
- Send a new request by adding a new XXE attack payload in the body and click on the response to get the flag
 
 ```
  <!--?xml version="1.0" ?-->
<!DOCTYPE foo [<!ENTITY example SYSTEM "/etc/passwd"> ]>
<data>&example;</data>

 ```
- [This helped a lot!](https://book.hacktricks.wiki/)

- Explanation of payload:
  1. <!DOCTYPE> allows us to define an external entity, in this case `&example`, foo is placeholder
  2. `[<!ENTITY example SYSTEM "/etc/passwd"> ]>`, gives example as the contents inside /etc/passwd
  3. The XXE payload defines an external entity, a placeholder `&example`, whose value is the contents of the /etc/passwd file. When the XML is read by the             program, it may automatically replace `&example`, with the actual data from that file. 
![image](https://github.com/user-attachments/assets/6a3dee48-850f-43dd-b887-30536dce69e8)

***
