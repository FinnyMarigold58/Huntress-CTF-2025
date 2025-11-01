---
title: Maximum Sound
category: WarmUps
points: 10
---

# Maximum Sound
**CTF:** Huntress CTF 2025
**Category:** Warmups  
**Author:** John Hammond
**Points:** 10  
**Challenge Description:**

```md
Dang, this track really hits the target! It sure does get loud though, headphone users be warned!!
```
(Writeup from a teammate)

> Knew that stegonography was banned in this CTF so I didn't want to dig in the file too much, it had to be the audio somehow. 

Originally thought it was DMTF codes so I tried decoding with https://dtmf.netlify.app/, but got nowhere. Pipl decoded the image in a spectogram viewer, and I noticed the repetitiveness of the peaks and valleys in it.

I was stuck for a while before remembering that Slow Scan Television Audio is a thing to encode images in audio, so I put the audio file into https://sstv-decoder.mathieurenaud.fr/ and got a MaxiCode image, which scanned to reveal the flag `flag{d60ea9faec46c2de1c72533ae3ad11d7}`

![Maxicode](images/maxicode.png)