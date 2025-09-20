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
  1. DES - it was adopted as standard in 1977 and uses a 56-bit key. In 1999, it was successfully broken in less than 24 hours then we shifts to 3DES.
  2. 3DES - It is applied three times, here the key size is 168 bits
