# Restricted

Here we are dealing with an SSH server which we can log into using the command `ssh restricted@\<IP> -p \<PORT>`. This is because from the SSH config file we are given we see that the following options are specified at the end of the file:

- Match user restricted
- PermitEmptyPasswords yes

Once logged in, however, we can notice most of the commands can't be executed and the PATH variable is read-only so we can't change that. The solution I came up with is using the -t option of the ssh command: `ssh restricted@188.166.152.84 -p 30535 -t "bash"`
This gives us access to an unrestricted shell through which we can explore the remote machine and find out the flag in the root directory:

![Restricted](/Screenshots/MISC_3.png)

## HTB{r35tr1ct10n5_4r3_p0w3r1355}
