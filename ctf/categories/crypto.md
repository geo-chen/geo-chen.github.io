





https://docs.pwntools.com/en/stable/install.html

Decoding flag behind a 5-byte key
```from pwn import xor, unhex
t = unhex('2e313f2702184c5a0b1e321205550e03261b094d5c171f56011904')
print(xor(t, t[:5], 'CHTB{'))
```

OR CyberChef: https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')XOR(%7B'option':'UTF8','string':'.1?%5C'%5Cu0002'%7D,'Standard',false)XOR(%7B'option':'UTF8','string':'CHTB%7B'%7D,'Standard',false)&input=MmUzMTNmMjcwMjE4NGM1YTBiMWUzMjEyMDU1NTBlMDMyNjFiMDk0ZDVjMTcxZjU2MDExOTA0




Decoding text file which is XORed with a single-byte key
```
from pwn import *

for l in read("file.txt").decode().strip().splitlines():
    try:
        t = unhex(l)
        s = xor(t, t[0], 'C').decode()
        if s.startswith("CHTB"):
            print(s)
    except: pass
```


Given plaintext, encryption scheme, and output, find random key
```
from pwn import *
r, f = map(unhex, read("../release/output.txt").decode().split())
print(xor(f, r, b"No right of private conversation was enumerated in the Constitution. I don't suppose it occurred to anyone at the time that it could be prevented.")[:len(f)])
---
from pwn import xor

a = bytes.fromhex("08501b3dbd0fb2f7c87aeb3a224a9d568fa8ad83ff442548b5f4334f0fe1dd6b8f5d5e410be5af2d7ea642b12d8f459f2ab666d4f79a9115dc9cf22ed60e899769fd206c40819bbefe2b5a2ec592a387c6927d866b6343466d5effde0666dd3bb7f657ed651bfcf45fd5b264a36406c6b6dbb1a81272029c5e06da438a0281c19c1e10a0dc47d6ae994557e82663e9f59578")
b = bytes.fromhex("05776f0daf1ae9f6dd26e945390bad7fda889c97ff6036")

test = b"No right of private conversation was enumerated in the Constitution. I don't suppose it occurred to anyone at the time that it could be prevented."

key = xor(a, test)
print(xor(key, b))
```




References
https://github.com/cryptohack/Cyber-Apocalypse-CTF-2021
