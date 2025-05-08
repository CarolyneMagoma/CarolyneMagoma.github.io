---
title: "Silent Supernova 1"
date:2025-05-05 10:00: +0800
tags: [forensics]
category: [ctf writeups]
---
# Silent Supernova1 Challenge Writeup – BitCTF.   

<b>challenge description<b>

![supernova](/assets/images/supernova.png)

The challenge came as a ZIP file, which I extracted using 7-Zip. The command I used in the terminal was:

7z x filename.zip

Upon extraction, the file revealed a Microsoft Word document named
kakwa.doc

![zip file unzipping](/assets/images/zip_zile_dowload.png)
This immediately raised suspicion, as .doc files are commonly used to deliver macro-based malware in phishing campaigns.

VirusTotal Scan
Before opening the document, I uploaded kakwa.doc to VirusTotal for an initial threat scan.

VirusTotal flagged the file as malicious. Most importantly, the page revealed a SHA-256 hash value  for the file.   

The SHA-256 hash was clearly visible on the scan results page — and this was the answer to the challenge question, which asked for the file's hash.      

![virus total scan](/assets/images/virus_total_1.png)

Happy hacking, Happy hunting.






