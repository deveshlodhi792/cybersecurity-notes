🔴 Introduction
-  John the Ripper is a well-known, well-loved and versatile hash-cracking tool.
-  It combines a fast cracking speed with an extraordinary range of compatible hash types.

🔴 Basics Terms
-  Hash: Hash (or hash value, digest) is the representation of arbitrary size of data in a fixed-length form. The hash value is obtained by running the original data through a hashing algorithm like MD4, MD5, SHA1 and NTLM.
-  Hash values are nearly irreversible because hashing functions designed as one-way. Thats why It is hard to find the original input if we given the hash value only.
-  John the Ripper (John)
  1.  If we have the hashed verison of password and also know the hashing algorithm it is possible to crack the hash value.
  2.  We can use the hashing algorithm to hash a large number of words, called a dictionary.
  3.  We can compare these hashes to the one we are trying to crack to see if they match.
  4.  If one of the hashes match with the hash value you are trying to crack then you have cracked it.
  5.  This way the John the Ripper or John (shortened) tool conduct fast brute force attacks on various hash types.
  6.  This process is called a dictionary attack.

🔴 Setting Up Your System
-  To crack passwords, we use
  1.  The "Jumbo John" version of John the Ripper
  2.  The RockYou password list
-  Other version of John does not have tools such as zip2john an rar2john.
-  sudo apt install john - for Ubuntu and Kali distribution. You will get "John the Ripper 1.9.0-jumbo-1" on Kali but for Ubuntu you have to build from the source to access all the tools available via Jumbo John.
-  For windows one can download and install zipped binary binary.
-  You can get the rockyou.txt wordlist from the <a href="https://github.com/danielmiessler/SecLists">SecLists</a> repository under the /Passwords/Leaked-Databases subsection. 
- You may need to extract it from the '.tar.gz' format using 'tar xvzf rockyou.txt.tar.gz.'.

🔴 Cracking Basic Hashes
-  Basic syntax of John the Ripper :- 
john [options] [file path]
-  john: invokes the John the Ripper program
   [Options] : Specifies the options you want to use
   [file path] : The file containing the hash we are trying to crack, if we are in the same directory we don't need to specify the whole path to file.
-  John has buit-in feature to detect what type of hash its being given and it crack the hash using appropriate rules and formats but this approach is unreliable.
-  We should identify the hash type first before cracking it.
- For automatic cracking -
  * john --wordlist=[path to wordlist] [path to file]

  --wordlist= : specify using wordlist mode, reading from the file that you supply in the provided path.
- example usage:

  john --wordlist=/usr/share/wordlists/rockyou.txt **hash_to_crack.txt**

-  To identify the hash algorithm one can use **hash-identifier**, a python tool that is super easy to use and will tell you what different types of hashes the one you enter is likely to be, giving you more options if the first one fails, or simply we can use <a href="https://hashes.com/en/tools/hash_identifier">Hashes.com</a>.
-  To download hash-id package use <a href="https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py">Hash-id tool</a> link.
-  Download it using **wget** or **curl** command on linux.
-  Then launch it using **python3 hash-id.py**.

-  Format-Specific Cracking
  1. * john --format=[format] --wordlist=[path to wordlist] [path to file]
       --format=: this is the flag to tell john that you're giving it a hash of a specific format and to use the following format to crack it.
       [format] : The format (algorithm) that the hash is in
     
     * Example:
       john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt

- Note on Formats:
  1. To check if you need to add raw- prefix or not, you can list all John's formats using **john --list=formats**.
  2. To check manually or grep for your hash type using something like **john --list=formats | grep -iF "md5"**. 

🔴 Cracking Windows Authentication Hashes
- NThash is a hash format which modern Windows operating system machines use to store user and service passwords.
- The previous version of Windows format for hashing passwords known as LM.
- Thats why NThash commonly referred as NTLM, coz NT/LM.
- SAM (Security Account Manager) in Windows is a database file in which user account information are stored, it includes usernames and hash passwords.
- Mimikatz tool or Active Directory database: NTDS.dit can help to acquire NThash/NTLM hashes by dumping the SAM database on a Windows Machine.
- One may not have to crack the hash to continue priviledge escalation, as one can often conduct a "pass the hash" attack.
- Note:- to access the SAM database file one should be a priviledge user.
- NT is used as --format= for NTLM hashes.
    
🔴 Cracking/etc/shadow Hashes
- Passwords hashes are stored in /etc/shadow file on Linux machines.
- It also store other information, such as the date of last password change and password expiration information.
- This file is only accessible by the root user.
- To crack /etc/shadow password, the file should be combine with /etc/passwd file for John to understand the data it's being given.
- For this process unshadow tool of John suite is used.
- **unshadow [path to passwd] [path to shadow]**
    * unshadow : invokes the unshadow tool
    * [path to passwd]: The file that contains the copy of the /etc/passwd file you've taken from the target machine.
    * [path to shadow] : The file that contains the copy of the /etc/shadow file you've taken from the target machine.
- **unshadow /etc/passwd /etc/shadow > unshadowed.txt**
    * This will merge both files into one file named unshadowed.txt.
    * Later this file will be used to crack password using john.
      
- **unshadow local_passwd local_shadow > unshadowed.txt**
    * local_passwd file contains the relevant line we want to use while cracking the password. This file was saved by the user or tester so he doesn't have to feed the whole /etc/passwd file. In this case this file have line for the root user - root:x:0:0::/root:/bin/bash.
    * local_shadow file contains the hashed password line for the root user :root:$6$2nwjN454g.dv4HN/$m9Z/r2xVfweYVkrr.v5Ft8Ws3/YYksfNwq96UL1FX0OJjY1L6l.DS3KEVsZ9rOVLB/ldTeEL/OIhJZ4GMFMGA0:18576::::::.

- **john --format=sha512crypt --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt/path to file**
    * We can fee the output file unshadowed.txt to John for cracking.
    * We don't need to specify hash mode but for reliablity we can use here. 

🔴 Single Crack Mode
-  dfd
  
  
