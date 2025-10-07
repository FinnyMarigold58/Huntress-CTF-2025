---
title: Trust Me
category: Miscellaneous
points: 10
---

# Trust Me
**CTF:** Huntress CTF 2025
**Category:** Miscellaneous  
**Points:** 10  
**Challenge Description:**

```md
C'mon bro, trust me! Just trust me!! Trust me bro!!!

The TrustMe.exe program on this Windows desktop "doesn't trust me?"

It says it will give me the flag, but only if I "have the permissions of Trusted Installer"...?

If you are using the VPN, you can RDP to this challenge with:

Username: Administrator
Password: h$4#82PSK0BUBaf7
```

## Initial Attempt

As the description says, this challenge involves a exe that when ran says that you must have the permissions of Trusted Installer. The way this program prompts is through message box, which became a problem for me later. After watching John Hammond's video ([link](https://www.youtube.com/watch?v=Vj1uh89v-Sc)) on leveraging Trusted Installer, but in that video he mentions that the method will not work with GUI application such as notepad.exe or in this case TrustMe.exe.

After searching online I found a tool called "ExecTI", and after uploading it to the VM and running TrustMe.exe I was given a flag value.

Flag: `flag{c6065b1f12395d526595e62cf1f4d82a}`

I doubt this was the intended solution, and that you were suppose to actually leverage the attack yourself instead of using an application.