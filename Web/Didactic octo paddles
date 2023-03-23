# Didactic octo paddles

The code of this challenge has two different kinds of vulnerabilities. The first one allows us to perform a missing signature JWT (Json Web Token) attack and access the /admin endpoint by tampering with a user's JWT. The second one is a SSTI (Server Side Template Injection) in the admin page, which shows the names of all the registered users of the website. So, the idea is to register a user with a username containing the following payload:

```js
{{:"pwnd".toString.constructor.call({},"return global.process.mainModule.constructor._load('child_process').execSync('cat /flag.txt').toString()")()}}
```

and then exploit the JWT attack to visit the admin page, achieving RCE and retrieving the flag as follows:

![DidacticOctoPaddles](/Screenshots/WEB_6.png)

## HTB{Pr3_C0MP111N6_W17H0U7_P4DD13804rD1N6_5K1115}
