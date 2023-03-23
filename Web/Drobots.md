# Drobots

This was simply a login portal bypass via a basic SQL injection. We can enter any password and the following payload inside the username field to login as admin: `admin" OR 1=1-- `

Since neither input sanitization and parameterized queries are used, the login is successful:

![Drobots](/Screenshots/WEB_3.png)

## HTB{p4r4m3t3r1z4t10n_1s_1mp0rt4nt!!!}
