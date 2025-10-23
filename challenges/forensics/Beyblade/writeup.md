---
title: Beyblade
category: Forensics
points: 10
---

# Beyblade
**CTF:** Huntress CTF 2025
**Category:** Forensics
**Author:** John Hammond
**Points:** 10  
**Challenge Description:**

```md
Sheesh! Some threat actor sure did let it rip on this host! We've been able to uncover a file that may help with incident response.
```

The password for the zip artifact is: `beyblade`

## Background
Opening up the artifact in a hex editor, I seen that this file is a registry file. I turned to another one of Eric Zimmerman's tools ([Registry Explorer](https://ericzimmerman.github.io/#!index.md)). Using this tool I was able to go through the "bookmarks", common registry places for malware. I found many of the flag pieces this way.

## Missing pieces
For the missing pieces I used Registry Explorer's find feature to search for the known formats: #of8, #/8, etc. Using this I was able to find the remaining pieces and combine them to make the flag.

## Summary

The .zip file is a registry file which contains pieces to the flag. The pieces are stored in the following locations:

1) Run (Runs every User login)
2) RunOnce (NTUser Logon Script | Run on login then deletes)
3) TypedURLs (URLs entered by a user into windows explorer)
4) RunMRU (Win+R | Run Dialouge Commands)
5) TypedPaths (Paths manually typed into Start Menu or Explorer Bar)
6) wmiprvse.exe App Path (yeah no idea what this is, found it through the find feature)
7) ShellNoRoam\MUICache (Program Execution)
8) Terminal Server Client\Servers\fileshare.local (RDP remanent)

Final flag: `flag{47cb5cd46d7bb34a0d9c315a99bb58de}`
