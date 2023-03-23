# Persistence

The goal of this challenge was to automate the sending of about a thousand requests to a /flag endpoint, which would at some point answer with the correct flag. Below is the script we can use:

```python
import requests

IP = '188.166.152.84'
PORT = '31565'
target = f'http://{IP}:{PORT}/flag'

N = 1500

for i in range(0, N):
    r = requests.get(target)
    print(r.text)
```

We can then `grep` the results for "HTB{" to find the flag.

## HTB{y0u_h4v3_p0w3rfuL_sCr1pt1ng_ab1lit13S!}
