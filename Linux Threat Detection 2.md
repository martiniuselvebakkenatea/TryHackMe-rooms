[Link to TryHackMe Room](https://tryhackme.com/room/linuxthreatdetection2 "Link to room")

---

### Run systemd-detect-virt to detect the system's cloud.
### What is the command's output you discovered?

***Answer:*** ```Amazon```

---

### Now run ps aux and look for EDR or antivirus processes.
### What is the full path to the detected antimalware binary?

***Answer:*** ```/var/lib/ultrasec/malscan```

---

### What is the path of the script that initiated the "hostname" command?

***Answer:*** ```/home/itsupport/debug.sh```

---

### What was the last Discovery command launched by the script?

***Answer:*** ```ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu```

---

### Looking at the script content, what's the email of the script author?

***Answer:*** ```greg@tryhackme.thm```

