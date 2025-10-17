---
title: Trashcan
category: Forensics
points: 10
---

# Trashcan
**CTF:** Huntress CTF 2025
**Category:** Forensics
**Points:** 10  
**Challenge Description:**

```md
Have you ever done forensics on the Recycle Bin? It's... a bit of a mess. Looks like the threat actor pulled some tricks to hide data here though.

The metadata might not be what it should be. Can you find a flag?
```

## Research
Based off the challenge description and the contents of trashcan.zip, I started by researching how to do Recycle Bin forensics. I found a [article](https://medium.com/@thismanera/windows-recycle-bin-forensics-a2998c9a4d3e) which nicely describes how $I files are metadata, while $R is the actual data files.

## $R files
Since all the $R files were the same and simply say: "When did I throw this out!?!?". I assumed that was a hint that Deletion Date had some importance.

## $I parser
I used Eric Zimmerman's [RBCmd](https://ericzimmerman.github.io/#!index.md) program to extract out the metadata from the $I files. In these files I found all the items had a similar date, but identical version and file names.

Using the hint from the $R files I filtered by Deleted Date. From there I noticed a pattern in file size. Turning the file size into a character turned the first letter into f and I could make out the word flag. Form there I used ChatGPT to generate a powershell script and returned the flag.

```ps
(
    Import-Csv -Path "data.tsv" -Delimiter "`t" |
    Sort-Object { [datetime]($_.'Deleted Date' -replace ' UTC','') } |
    Select-Object -Unique 'Deleted Date', 'File Name', 'File Size (bytes)' |
    ForEach-Object { [char][int]$_.'File Size (bytes)' }
) -join ''
```

Flag: `flag{1d2b2b05671ed1ee5812678850d5e329}`
