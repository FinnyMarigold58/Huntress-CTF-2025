---
title: Flag Checker
category: Web
points: 10
---


# Flag Checker
**CTF:** Huntress CTF 2025
**Category:** Warmups  
**Points:** 10  
**Challenge Description:**

```md
Don't be shy, show your emotions! Get emotional if you have to! Uncover the flag.
```

## Inital Observations

First checking the client side code, we can see that the only thing we have access to is a form without any other javascript. When checking the flag, we send a GET request to the `/submission` endpoint.

## IP Block

After 10 tries, the website would block your ip out. I was unable to find a bypass for this and thus resorted to constant VM resets ever 10 tries.

## Long Awaited Solution

After a day of thinking, the only logical thing was something to do with how the server responds to us. Otherwise, there was no way we could guess or bruteforce the flag. After experimenting some with Burp Suite, and the flag `flag{00000000000000000000000000000000}`, only increasing one digit at a time.

Ex. `flag{00000000000000000000000000000000}` -> `flag{10000000000000000000000000000000}` -> `flag{20000000000000000000000000000000}`

I stumbled upon the fact that the server took longer to respond on certain numbers, thus we are able to do a timing attack. After I hit the high number, I would go on to the next digit and repeat the process. Not a very elegant solution, but because I couldn't figure out how to bypass the ip block I was stuck with just manual burp attacks.

Flag: `flag{77ba0346d9565e77344b9fe40ecf1369}`
