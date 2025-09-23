🔴 Cryptography 
- Cryptography's ultimate purpose is to ensure secure communication in the presence of adversaries.
- It is used to protect confidentiality, integrity and authencity.
- To handle credit cards information and process related transactions the credit card companies follows and enforce Payment Card Industry Data Security Standard (PCI DSS).
- According to PCI DSS the data should be encrypted both while being stored (at rest) and while being transmitted (in motion).

🔴 Plaintext to Ciphertext
- Plaintext is the original, readable message or data before it's encrypted. It can be a document, an image or any other binary data.
- Ciphertext is the scrambled, unreadable version of the message after the encryption.
- Cipher is an algorithm or method to convert plaintext into ciphertext and back again.
- Key is a string of bits the cipher uses to encrypt or decrypt data.
- Encryption is the process of converting plaintext into ciphertext using a cipher and a key.
- Decryption is the reverse process of encryption, converting ciphertext back into plaintext using a cipher and a key.
- While communication the sender sends the plaintext then the plaintext is passed throught the encryption function along with a proper key.
- The encryption function returns a ciphertext. The encryption funtion is a part of cipher.

🔴 Historical Ciphers
- Caesar Cipher - from the first Centry BCE.
- The Vigenere Cipher from the 16th century.
- The Enigma machine from World War II.
- The one-time pad from the Cold War.
- There are many more other.

🔴 Types of Encryption
- There are two types of encryption
  1. Symmetric
  2. Asymmetric
- "Symmetric" encryption (symmetric cryptography) uses the same key to encrypt and decrpyt the data.
- It is also called as private key cryptography because here the key kept secretly.
- Here communicating the key to the intended parties can be challenging.
- Examples of symmetric encryption:-
  1. DES (Data Encryption Standard) - it was adopted as standard in 1977 and uses a 56-bit key. In 1999, it was successfully broken in less than 24 hours then we shifts to 3DES.
  2. 3DES (Triple DES) - It is applied three times, here the key size is 168 bits, though the effective security is 112 bits. 3DES was more of an ad-hoc solution when DES was no longer considered secure. 3DES was deprecated in 2019 and replaced by AES (Advanced Encryption Standard).
  3. AES (Advanced Encryption Standard) was adopted as a standard in 2001. Its key size can be 128, 192, or 256 bits.
- There are many more symmetric encryption ciphers used in various applications, but they are not been adopted as standards.
- "Asymmetric Encryption" - This encryption uses a pair of keys for encryption.
- One key (public key) is used to encrypt and the other key(private key) is used to decrypt data.
- Asymmetric encryption or asymmetric cryptography encrypts the data using public keys, thats why it is called as public key cryptography.
- Examples are RSA, Diffie-Hellman, and Elliptic Curve Cryptograhphy (ECC).
- Asymmetric encryption is relatively slower than symmetric encryption.
- Asymmetric encryption use larger keys than symmetric encryption. For example, RSA uses 2048-bit, 3072-bit, and 4096-bit keys. 2048-bit is the recommended minimum key size.
- Diffie-Hellman uses 3072-bit and 4096-bit keys for enhanced secuity, however their recommended minimum key size is 2048 bits.
- ECC uses 256-bit key and it provides 3072-bit RSA key level security in encryption.
- Asymmetric encryption is based on a particular group of mathematical problems that are easy to compute in one direction but extremely difficult to reverse.
