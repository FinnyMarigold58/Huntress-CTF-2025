# Huntress CTF 2025 Writeups

Welcome to my collection of writeups from Huntress CTF 2025.  

⚠️ **Warning:** Some of these writeups include **malware samples** from the CTF challenges.  
Do **not** run or open challenge artifacts outside of a controlled environment (VM, sandbox).  

---

## Challenges

{% for challenge in site.challenges %}
- [{{ challenge.title }}]({{ challenge.url }}) — {{ challenge.category }} ({{ challenge.points }} pts)
{% endfor %}
