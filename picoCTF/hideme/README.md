# hideme
## Points: 100

This challenge involves steganography.

Naturally, my first instinct is to use a tool called *Aperi'Solve*, which has useful tools for anything stego related.

I uploaded the image and get this info under Zsteg:

Although the file is a png, I noticed at the very top that it says it's "Zip archive data"...

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/a1b6b528-2625-4743-9202-66c75bc59c1f)

Curious about it, I use terminal to download the file onto my Linux VM, and then unzip it.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/d3337034-e5c7-4bb8-900b-ede3251bab99)

Well! Guess it worked. It seemed to create a new directory with ANOTHER png in it.

Navigating to the directory and opening the file reveals the flag.

### Flag:
picoCTF{Hiddinng_An_imag3_within_@n_ima9e_82101824}
