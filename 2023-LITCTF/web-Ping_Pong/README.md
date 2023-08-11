# web/Ping Pong Challenge
## Points: 114

In this challenge, we are given a website that contains a field where we can input an IP, and that IP would be pinged.


We are also given a file download containing the elements of this host website.
![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/be3bb26a-7524-4014-868f-1f9c0410c8d4)


Based on this, we can deduce that flag.txt is located in the host directory, so we simply need a method to access it.


I looked up methods to do field manipulation, when I stumbled upon the **CRLF Injection** vulnerability.
- In summary, CRLF *(Carriage Return Line Feed)* signifies the end of a line.
- Attackers can use this exploit to add their own code to the file being read, simply by terminating their input.
- CRLF is typically noted by the characters **\r\n**.


Knowing this, let's apply it to the problem by using **Burp Suite**.
After sending the webpage traffic through the repeater, we find a field named *hostname*. Let's change this and add our own command, ls, to list all the files.
![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/e5274585-b668-4c6a-9d4e-b023688dd507)
(In URL encoding, \r\n = %0d%0a)


As expected, this lists all the files in the webpage.
![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/11ff7679-cffd-4643-a02a-6e1b138d15ae)


Since we know it works, we can now replace ls with the cat command to read **flag.txt**.
![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/76b89b18-402e-4c10-a6c1-cf7d88e6f058)


### Flag
LITCTF{I_sh0uld_b3_m0r3_c4r3ful}


## Notes
I later figured out that Burp isn't even needed for this. You can simply add a double ampersand (&&) to the website field and your command after, and achieve the same effect.
Sometimes the problem is solved with methods simpler than you would assume, so don't overthink it.
