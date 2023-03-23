# Remote computation

The objective of this challenge was to answer to a series of requests coming from the given docker instance in such a way to respect certain constraints. The following is a possible solution script using the pwntools Python library for managing the client-server communication:

```python
from pwn import *

IP = '104.248.169.117'
PORT = 32355

r = remote(IP, PORT)

r.recvuntil('> ')
r.sendline('1')

def compute_result(comp):
    print('trying to execute computation...')
    try:
        result = eval(comp)
    except SyntaxError:
        return 'SYNTAX_ERR'
    except ZeroDivisionError:
        return 'DIV0_ERR'
    
    if round(result, 2) >= 1337.00 or round(result, 2) < -1337.00:
        return 'MEM_ERR'
    
    return str(round(result, 2))

while True:
    try:
        computation = r.recvuntil('?')
    except EOFError:
        break
    comp = computation.decode().split(': ')[1].split(' =')[0]
    
    print(comp)
    print(r.recvuntil('> ').decode())
    result = compute_result(comp)
    print(result)
    r.sendline(result)

print(r.recvrepeat(2000).decode())
```

## HTB{d1v1d3_bY_Z3r0_3rr0r}
