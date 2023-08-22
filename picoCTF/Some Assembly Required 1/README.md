### Some Assembly Required 1

## Points: 70

The task here is a combination of simple web and reverse engineering.

We are given a website that looks like so:

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/d5089807-882e-4f5a-8b90-ce8544f3b394)

I open Inspect Element, and open the Network tab to see what is being posted.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/1c63db44-afa3-4900-b1fe-617e9cd4f1fe)

There's a suspiciously named file.

I open terminal, download the file using *wget http://mercury.picoctf.net:40226/JIFxzHyW8W*.

Using the *cat* command on the file reveals the flag.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/5688159a-af27-4284-853b-75405c71d140)

