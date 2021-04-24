





https://docs.pwntools.com/en/stable/install.html

```from pwn import xor, unhex
t = unhex('2e313f2702184c5a0b1e321205550e03261b094d5c171f56011904')
print(xor(t, t[:5], 'CHTB{'))
```

OR CyberChef: https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')XOR(%7B'option':'UTF8','string':'.1?%5C'%5Cu0002'%7D,'Standard',false)XOR(%7B'option':'UTF8','string':'CHTB%7B'%7D,'Standard',false)&input=MmUzMTNmMjcwMjE4NGM1YTBiMWUzMjEyMDU1NTBlMDMyNjFiMDk0ZDVjMTcxZjU2MDExOTA0
