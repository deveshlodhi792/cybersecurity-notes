🔴 Introducation
-  If we want to know that if the file whe have downloaded is identical to the original file, bit for bit, then we have to compare the hash values of both files.
-  If the hash values are equal of both files then with high certainity we can say these both files are identical.
-  Hash value is a fixed-size string or characters that is computed by a hash function.
-  A hash function helps to generate the hash value.
-  Hash function takes an input of any size and returns an output of fixed length,i.e. hash value.

🔴 Hash Function
-  Hash functions generate hash values and they are different from encryption.
-  It is impossible or computationally impractical to go from the output back to the input, as there is no key included in this process.
-  A hash function takes some input data of any size and creates a summary or digest of that data. The output has a fixed size.
-  One cannot predict the ouput for any input and vice-versa.
-  Good hashing algorithms are those which compute hash values fast and are nearly impossible to reverse, i.e., go from the ouptut and determine the input.
-  Any slight change in the input data, even a single bit, can result in significant change in output.
-  The output of a hash function is in raw bytes and then it encoded into base64 or hexaecimal.
-  md5sum, sha1sum, sha256sum and sha512sum produce their output in hexadecimal format.
-  Each raw byte = two hexadecimal digits.
-  **hexdump -C file1.txt**- to see text file into hexadecimal format.
-  md5sum *.txt - to encode with md5 (Message-Digest Algorithm 5)
-  sha1sum *.txt - to encode with sha1 (Secure Hash Algorithm 1)
-  sha256sum *.txt - to encode with sha-256 (Secure Hash Algorithm 256)

-  **Why is Hashing Important?**
  1.  Hashing helps protect data's integrity and ensure password confientiality.
  2.  When we log into a website, the server uses hashing to verfiy our password.
  3.  Server records the hash value of our passwords only.

-  **What's a Hash Collision?**
  1.  When two different inputs gives the same output (hash value), then it is called a hash collision.
  2.  Hash functions are designed to avoid collisions and prevent an attacker from being able to create a collision intentionally.
The number of inputs is unlimited and the number of possible outputs is limited, this leads to a pigeonhole effect.
If a hash function produces 4-bit hash value then we have 16, i.e 2^4 = 16, different hash values and therefore there is high probability of hash collision.
However, a good hash function ensure that the probability of a collision is neglibile.
MD5 and SHA1 are considered insecure due to the ability to engineer hash collisions.
MD5 and SHA1 are based on two different algorithm so there is no attack has yet given a collision in both algorithms simultaneously.

🔴 Insecure Password Storage for Authentication
-  Hashing has many uses in Cyber security.
-  Two of them are Password storage and Data integrity.
-  Password storage here mean to store password (usually in hashed form) for authentication purpose.
-  Password managers does not store passwords in hash form, they used encryption to store them as we have to retrieve them in clear text to apply on the website for authentication.
-  Storing passwords in plaintext is a very insecure secruity practice for any web applications or website.
-  These are three insecure practices for security of passwords:-
    1.  Storing passwords in plaintext
    2.  Storing passwords using a deprecated encryption.
    3.  Storing passwords using an insecure hashing algorithm like SHA-1, MD5.

🔴 Using Hashing for Secure Password Storage
-  A Rainbow Table is a lookup table of hashes to plaintexts, so one can quickly find out what password a user had just from the hash.
-  Websites like Crackstation and Hashes.com internally use massive rainbow tables to provide fast password cracking for hashes wihtout salts.
-  To protect against rainbow tables salt is added to the passwords.
-  The salt is a randomly generated value store in the database and should be unique to each user.
-  The salt is added to either the start or the end of the password before it's hashed.
-  Adding salt to passwords means that every user will have a different password hash even if they have the same password.
-  Hash functions like Bcrypt and Scrypt handle this automatically.
-  Salts don't need to be kept private.

-  Example of Securely Storing Passwords

You can find many good guides online that promote best security practices when storing passwords. Please check if there are any standards you need to follow when storing passwords before adopting one. Consider this example following good security practices when storing user passwords:
    1. We select a secure hashing function, such as Argon2, Scrypt, Bcrypt, or PBKDF2.
    2. We add a unique salt to the password, such as Y4UV*^(=go_!
    3. Concatenate the password with the unique salt. For example, if the password is AL4RMc10k, the result string would be AL4RMc10kY4UV*^(=go_!
    4. Calculate the hash value of the combined password and salt. In this example, using the chosen algorithm, you need to calculate the hash value of AL4RMc10kY4UV*^(=go_!.
    5. Store the hash value and the unique salt used (Y4UV*^(=go_!).

-  We don't use encryption to store password because the keys are involved and if someone get the key he can easily decrypt the passwords. Passwords are meant to store in that way so that cannot get decrypted.

🔴 Recognising Password Hashes
-  There are automated hash recognition tools such as hashID exists, but they are unreliable for many formats. These tools are only reliable when Hashes have a prefix.
-  Web Application database more likely have hash that are MD5 than NTLM (NT LAN Manager).
-  It is important to learn yourself to recognize the hash type.
-  On Linux Password hashes are stored in /etc/shadow, which is readable by root. The password are used to be stored in /etc/passwd, which was readable by everyone.
-  The shadow file contains the password information.
-  Each line contains nine fields. Lines are separated by colons (:).
-  The first field is the login name or username. The Second field is the encrypted password.
-  Other fields info can be found by executing "man 5 shadow" command on Linux system.
-  The encrypted password field contains hashed passphrase with four components: prefix (algorithm id), option (parameters), salt and hash.
-  Its format looks like "$prefix$options$salt$hash".
-  Following are the most common Unix/Linux-style password prefixes one might encounter:-
  1.  $y$    -  yescrypt is a scalable hashing scheme and is the default and recommended choice in new system.
  2.  $gy$   -  gost-yescrypt uses the GOST R 34.11-2012 hash function and the yescrypt hashing method.
  3.  $7$    -  scrypt is a password-based key derivation function.
  4.  $2b$, $2y$, $2a$, $2x$  -  bcrypt is a hash based on the Blowfish block cipher originally developed for OpenBSD but supported on a recent version of FreeBSD, NetBSD, Solaris 10 and newer, and several Linux distribution.
  5.  $6$  -  sha512crypt is a hash based on SHA-2 with 512-bit output orignially develped for GNU libc and commonly used on (older) Linux system.
  6.  $md5  -  SunMD5 is a hash based on the MD5 algorithm originally developed for Solaris.
  7.  $1$  -  md5crypt is a hash based on the MD5 algorithm originally developed for FreeBSD.
  8.  More info about these prefixes - "man 5 crypt".
  9.  Example
      - strategos:$y$j9T$76UzfgEM5PnymhQ7TlJey1$/00Sg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4:19965:0:99999:7:::
      - The fields are separated by colons. The important ones are the username and the hash algorithm, salt, and hash value. The second field has the format $prefix$options$salt$hash.

In the example above, we have four parts separated by $:
      1.  y indicates the hash algorithm used, yescrypt
      2.  j9T is a parameter passed to the algorithm
      3.  76UzfgEM5PnymhQ7TlJey1 is the salt used
      4.  /OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4 is the hash value

-  MS Windows passwords are hashed using NTLM.
-  NTLM (New Technology LAN Manager) is a suite of security protocols offered by Microsoft for Windows for the authentication of users' identity and their protection.
-  NTLM is a variant of MD4.
-  NTLM is visually identical to MD4 and MD5. To determine the hash type one must have knowledge of context.
-  Passwords are stored in the file named SAM (Security Accounts Manager) the path is C:\Windows\System32\config\SAM.
-  MS Windows prevent normal users from dumping (extract or copy) from this file.
-  Tools like mimikatz circumvent MS Windows security.
-  The hashes foun there are split into NT hashes and LM hashes.

- A great place to find more hash formats and password prefixes is the Hashcat Example Hashes page. For other hash types, you’ll typically need to check the length or encoding or even conduct some research into the application that generated them. Never underestimate the power of research.

🔴 Password Cracking
-  Hashes can't be decrypted as they are not encrypted, They can only be cracked by hashing many different inputs (rockyou.txt covers many passwords), potentially adding the salt and comparing it to the target hash.
-  Tools like Hashcat and John the Ripper are used for hash cracking.
-   GPU (Graphics Processing Units) have thousands of cores and they are very good at some mathematical calculations involved in hash functions.
-   GPU's can be used to crack many hash types quickly.
-   Some hashing algorithm like Bcrypt, are designed so that hashing on a GPU does not provide any speed improvement over using a CPU; this helps them resist cracking.
-  VMs (Virtual Machines) don't have access to the host's graphics card(s). You can set up it on software to take gpu in use but it is complicated. 
-  Performance degradation occurs if we use CPU from a virtualised OS, if we try to crack a hash it needs every extra CPU cycle.
-  To make the most of your GPU it is best to run Hashcat on your local physical machine.
-  Hashcat for Windows is available on the websites and it can be run from Powershell.
-  Hashcat works with OpenCL in a VM, but the speeds will likely be worse than cracking on your host.
-  John the Ripper uses CPU by default and works in a VM out of the box, although you may get better speeds running it on the host OS to avoid any virtualisation overhead and make the most of your CPU cores and threads.

-  Time to Crack Some Hashes
    1.  To crack hash using hashcat - "hashcat -m <hash_type> -a <attack_mode> hashfile wordlist.
    2.  -m <hash_type> - Here we have to specify the hash-type in numeric format. For example, -m 1000 is for NTLM. Check man hashcat and   <a href="https://hashcat.net/wiki/doku.php?id=example_hashes">Hash code Page</a> to find the hash type code to use.
    3.  -a <attack_mode> - It specifies the attack-mode. For example -a 0 is for straight, i.e., trying one password from the wordlist after the other.
    4.  hashfile is the file containing the hash you want to crack.
    5.  wordlist is the security word list you want to use in your attack.
    6.  For example - **hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt**
    7.  You can choose how to crack hashes. You’ll need to use online tools (Crackstation, Hashes.com), Hashcat, or John the Ripper. Although you can use online rainbow tables to solve, we strongly advise against doing that as this will restrict your learning experience.
  
🔴 Hashing for Integrity Checking
-  Hashing can be used to check that files haven't been changed.
-  If you put same data as input, you always get the same data as output. Even if a single bit changes, the hash value will change significantly.
-  Therefore the hash value can be used to check that files haven't been modified or to ensure that the file you downloaded is identical to the file on the web server.
-  Hashing is also used to find duplicate files. If two documents have the same hash, they are the same document. This is very convenient for finding and deleting duplicate files.
- HMACs
  1.  HMAC (Keyed-Hash Message Authentication Code) is a type of Message Authentication Code (MAC).
  2.  It uses a cryptographic hash function in combination with a secret key to verify the authenticity and integrity of data.
  3.  Firstly HMAC can be used to ensure that the person who created the HMAC is who they say they are, i.e. authenticity is confirmed.
  4.  Second it proves that the message hasn't been modified or corrupted, i.e., integrity is maintained.
  5.  Secret key used - Proved authencity
      Hashing Alogrithm - Proved integrity
  6.  The following steps give you a fair idea of how HMAC works-
      a.  The secret key is padded (extend using zeros) to the block size of the hash function.
      b.  The padded key is XORed (exclusive OR) with a constant (usually a block of zeros and ones).
      c.  The message is hashed using the hash function with the XORed key.
      d.  The result from step c is then hashed again with the same hash function but using the padded key XORed with another constant.
      e.  The final output is the HMAC value, typically a fixed-size string.
      f.  Technically speaking, the HMAC function is calculated using the following expression:

HMAC(K,M) = H((K⊕opad)||H((K⊕ipad)||M))

Note that M and K represent the message and the key, respectively.

🔴 Conclusion
-   base64 -d filename - to decode from base64 format.
-   Hashing:
    1.  It is a process that takes input data and produces a hash value.
    2.  It is a fixed-size string of characters, also referred to digest.
    3.  Hash value represents the data and any change in the data leads to change in the hash value.
    4.  Hashing is one-way, unlike encryption or encoding.
    5.  One can't reverse the process to get the original data.             
-   Encoding:
    1.  Encoding converts data from one form to another to make it compatible (comfirtable) with a specific system.
    2.  ASCII, UTF-8, UTF-16, UTF-32, ISO-8859-1, and Windows-1252 are valid encoding methods for the English Langauge.
    3.  Base32 and Base64 encoding commonly used when sending and saving data and it is not for any specific language.
    4.  Encoding is reversible thats why it does not protect the confientiality of the message.

-  Encryption can protects data confidentiality using a cryptographic cipher and a key. It is also reversible, provided we know the cipher and can access the key.
    
