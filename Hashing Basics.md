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
-  
