# Ancient Encodings

We are presented with an encoded flag and the following code:

```python
from Crypto.Util.number import bytes_to_long
from base64 import b64encode

FLAG = b"HTB{??????????}"


def encode(message):
    return hex(bytes_to_long(b64encode(message)))


def main():
    encoded_flag = encode(FLAG)
    with open("output.txt", "w") as f:
        f.write(encoded_flag)


if __name__ == "__main__":
    main()
```

By simply applying the above steps in reverse order we obtain the original flag:

```python
from base64 import b64decode

enc_flag = '53465243657a467558336b7764584a66616a4231636d347a655639354d48566664326b786246397a5a544e66644767784e56396c626d4d775a4446755a334e665a58597a636e6c33614756794d33303d'

def decode(flag):
    print(b64decode(bytes.fromhex(flag).decode()).decode())

decode(enc_flag)
```

We can also use CyberChef to obtain the same result.

## HTB{1n_y0ur_j0urn3y_y0u_wi1l_se3_th15_enc0d1ngs_ev3rywher3}
