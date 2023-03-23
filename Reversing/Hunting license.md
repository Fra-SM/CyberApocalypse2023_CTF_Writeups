# Hunting license

Here the goal was to find the correct answers to the questions coming from the server, which basically asked for 3 passwords. These can be obtained via static analysis; in the following screenshot there is the decompiled function showing the various stages:

![HuntingLicense](/Screenshots/REVERSING_2.png)

This is a Python script that prints out all the required passwords:

```python
t2 = bytearray.fromhex('477b7a6177527d77557a7d727f32323213')
t3 = bytearray.fromhex('1313131313131313131313131313131313')

def byte_xor(ba1, ba2):
    return bytes([_a ^ _b for _a, _b in zip(ba1, ba2)])

password2 = bytearray.fromhex('307754647230777373345000')

password3 = byte_xor(t2, t3)

print('PasswordNumeroUno') #password 1
print(password2.decode('UTF-8')[::-1]) # password 2 in reverse order
print(password2.decode('UTF-8')) # password 2
print(password3.decode('UTF-8')) #password 3
```

## HTB{l1c3ns3_4cquir3d-hunt1ng_t1m3!}
