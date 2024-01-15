# repeat

![Alt text](<Web capture_15-1-2024_182549_play.uoftctf.org.jpeg>)

this challenge was straight forward we were given this two files 

```python
import os
import secrets

flag = "REDACATED"
xor_key = secrets.token_bytes(8)

def xor(message, key):
    return bytes([message[i] ^ key[i % len(key)] for i in range(len(message))])

encrypted_flag = xor(flag.encode(), xor_key).hex()

with open("flag.enc", "w") as f:
    f.write("Flag: "+encrypted_flag)
```

and

```
Flag: 982a9290d6d4bf88957586bbdcda8681de33c796c691bb9fde1a83d582c886988375838aead0e8c7dc2bc3d7cd97a4
```

it is basic xor operation on the flag and the 8 bytes xor_key in line 5

we also know that the flag starts with `UofCTF{` so we have the first 8 bytes of flag.

as you know The XOR operation is reversible, so key  = first 8 bytes of the encrypted flag ⊕ `UofCTF{` bytes

using tools like [cyberchef](https://gchq.github.io/CyberChef/) you can find the flag : `UofTCTF{X0r_IZ_r3v3RS1Bl3_w17H_kN0wN_P141n73X7}`
