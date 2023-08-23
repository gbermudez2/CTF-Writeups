# findme
## Points: 100

Opening the website given to us, we are treated to a login screen.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/a8a2c01d-5189-4d41-a1c1-260af626d46a)

The challenge gave us the credentials *test* and *test!* for the username and password respectively.

Afterwards, we are treated to this page.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/49e09597-ea8b-4303-968a-3607a84875b3)

While the "Search for flags" field doesn't exactly return anything, it's best that we use Burp to examine any deeper network traffic.

If we navigate to the /login POST request, we can see a pretty interesting response.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/79e37b9f-cef4-456a-b6bf-21d7a90754f9)

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/4ea091e8-969a-4876-a972-7ce44010fc10)

Apparently, this is where the redirection takes us, before showing us the "Search for flags" page.

I tried putting in this URL into the address bar, and it immediately redirects me back to the same page.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/a5832062-cd8c-4cbc-9e88-4e40d3707ce5)

Nothing changed in the browser, however we do get another entry in Burp, showing a similarly formatted URL.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/067b9e08-513e-4fec-8699-03a531651421)

Turns out, these two URLs are actually Base64 encoded, and I didn't figure this out until I highlighted the text.

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/25ab0af7-0d6e-44dd-aba4-9729dda787aa)

![image](https://github.com/gbermudez2/CTF-Writeups/assets/32963758/29a3ebef-0cae-496d-bbc5-c7364eeb2002)

Combining these two gives the flag.

### Flag
picoCTF{proxies_all_the_way_d1c0b112}
