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
