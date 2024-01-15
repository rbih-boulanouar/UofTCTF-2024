![ ](https://raw.githubusercontent.com/rbih-boulanouar/UofTCTF-2024/bc936247ff3bb9f9e7a88df44af38a428454f6cc/Cryptography/repeat/Web%20capture_15-1-2024_182549_play.uoftctf.org.jpeg)

# repeat

this challenge was straight forward we were given this two files 

https://github.com/rbih-boulanouar/UofTCTF-2024/blob/70857a57b423e572f0f1c61693362c3717c487c2/Cryptography/repeat/gen.py#L1-L13

and

https://github.com/rbih-boulanouar/UofTCTF-2024/blob/70857a57b423e572f0f1c61693362c3717c487c2/Cryptography/repeat/flag.enc#L1

it is basic xor operation on the flag and the 8 bytes xor_key in line 5

we also know that the flag starts with `UofCTF{` so we have the first 8 bytes of flag.

as you know The XOR operation is reversible, so key  = first 8 bytes of the encrypted flag ⊕ `UofCTF{` bytes

using tools like [cyberchef](https://gchq.github.io/CyberChef/) you can find the flag : `UofTCTF{X0r_IZ_r3v3RS1Bl3_w17H_kN0wN_P141n73X7}`
