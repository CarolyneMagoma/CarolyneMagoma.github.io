---
title: "Message from heaven(BitCTF)"
date:2025-05-05 10:00: +0800
tags: [cloud security]
category: [cloud computing]

---
# Message from heaven 

Challenge Description
![s3 challenge description](/assets/images/description.png)

<b>Goal<b>

Recover the hidden flag without directly connecting to any services. This is a reconnaissance and cloud misconfiguration challenge.

<b>Analyzing the Clue<b>

The key hint provided was:  <b>vuln4ppcl0uds3c</b>

This looked like a reference to a cloud-related resource. Interpreting the leetspeak gives:

vuln – likely "vulnerable"
4pp – "app"
cl0ud – "cloud"
s3c – "sec" for "security"

This suggested a possibly misconfigured Amazon S3 bucket.

<b>Bucket Reconnaissance<b>

Using the standard S3 bucket URL pattern:

http://<bucket-name>.s3.amazonaws.com/

I visited
http://vuln4ppcl0uds3c.s3.amazonaws.com/

Initially, this returned an XML PermanentRedirect, confirming the bucket exists but must be accessed via the correct endpoint.

![S3 Bucket Redirect](/assets/images/s3_redirect.png)

<b>Accessing the Bucket<b>

Trying the corrected regional endpoint:
http://vuln4ppcl0uds3c.s3.amazonaws.com/

This time, the bucket returned an XML directory listing with one file:

<Key>The_flag_from_heaven.txt</Key>

![s3 directory listing](/assets/images/2025-05-04%2015_58_34-vuln4ppcl0uds3c.s3.amazonaws.com%20-%20Brave.png)

<b>Retrieving the Flag<b>

Visiting the full path:
http://vuln4ppcl0uds3c.s3.amazonaws.com/The_flag_from_heaven.txt
Revealed the flag content:

![s3 flag discovered](/assets/images/flag.png)

Happy hacking, happy hunting


