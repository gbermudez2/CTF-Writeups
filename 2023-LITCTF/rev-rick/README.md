# rev/rick
## Points: 116

This challenge involves simple reverse engineering, if any at all.
I had no prior knowledge about it until this CTF, and I had to do a bit of research into other writeups regarding this.

In this challenge, we are given a file named rick.
Using a Linux VM, I did *cat rick* to read the file context, which returned a bunch of weird text and a rickroll in plaintext.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/7196a318-d6b3-4a3b-9273-c0a5864f8bde)

Since we're doing reverse engineering, it's always best to **find out how the program works**.
Let's run the file:

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/40ec186e-4f2c-42da-b5c5-7745823a693d)

This program asks for a string, then tries to verify if it matches the flag. Therefore, we can deduce that the flag is in fact within the code, and it compares it to the user input somewhere.

For this, I installed a program called **IDA Disassembler** to look at the assembly code.
In IDA View, the window shows everything we need. After some scrolling, we can see the "wat is flag" text in the comments.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/89e7a940-33b7-4dda-8b22-203117d9e3dd)

When we inputted a random string earlier, it said "ur wrong", so I assumed there would be a field where it would return "ur right".
Luckily, this field was only a few lines down:

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/fc1e4315-bc19-47ad-aaca-858732941c73)

Well, that's a weird string..

I was definitely confused by it, but I later realized that it's backwards! It says "chatgpt gonna make the next rickroll" in alphanumeric characters.
I double clicked the commented text, and it took me to the full variable.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/e40b1772-4cf1-45d8-a2b1-7838a010d7ce)

Reversing this reveals the flag.

### Flag
LITCTF{ch4tgp7_g0nn4_m4k3_th3_nex7_r1ckr0l1}
