# She shells C shells

By statically analyzing the binary, we can see that there is a secret message being encoded using XOR between hardcoded values. The following Python script prints out the password needed to get the flag:

```python
m1 = bytearray.fromhex('6e3fc3b9d78d1558e50ffbac224d57dbdfcfedfc1c846ad81ca617c4c1bfa08587a143d4584f8da8b2f27ca3b98637dabf070a7e73df5c60aecacfb9e0deff0070b9e45fc89ab351f5aea87e8d')
m2 = bytearray.fromhex('641ef5e2c097441bf85ff9be185d488e91e4f6f15c8d269e2ba102f7c6f7e4b398fe57ed4a4bd1f6a1eb09c699f258facb6f6f5e1fbe2b138ea5a99993ab8f701cc0c43ea6fe933590c3c910e9')
t = bytearray.fromhex('2c4ab799a3e57078936e97d9476d38bdffbb85996fe14aab74c37ba8b29fd7ecebcd63b23923e184929609c699f258facb6f6f5e1fbe2b138ea5a99993ab8f701cc0c43ea6fe933590c3c910e9')

def byte_xor(ba1, ba2):
    return bytes([_a ^ _b for _a, _b in zip(ba1, ba2)])

password = byte_xor(m1, t)
flag = byte_xor(password, m2)

#password for the flag
print(password.decode('UTF-8'))
```

## HTB{cr4ck1ng_0p3n_sh3ll5_by_th3_s34_sh0r3}
