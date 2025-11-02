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

- 



