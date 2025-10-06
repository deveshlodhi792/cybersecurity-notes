🔴 Introduction
- Cryptograhpy can provide solutions to the following requirements while communicating :-
  1. **Authentication**: YOu want to be sure you communicate with the right person, not someone else pretending.
  2.** Authenticity**:  You can verify that the information comes from the claimed source.
  3. **Integrity**: You must ensure that no changes the data you exchange.
  4. **Confidentiality**: You want to prevent an unauthorised party from eavesdropping on your conversations.

- Private key cryptography i.e symmetric encryption protects mainly confidentiality.
- Public Key Cryptography i.e., asymmetric crptography fullfil all requirements.

🔴 Common use of Asymmetric Encryption
- Asymmetric cryptography is used to exchange keys for symmetric encryption.
- Asymmetric cryptography is relatively slower than symmetric encryption.
- Asymmetric cryptography only used once to get the symmetric encryption cipher and key and then one can communicate privately using symmetric encryption.

🔴 RSA (Rivest Shamir Adleman)
- RSA is a public-key encryption alogrithm that enables secure data transmission over insecure channels.
- The Math That Makes RSA Secure
  1. RSA is based on the mathematically difficult problem of factoring a large number.
  2. Multiplying two large prime numbers is a straightforward operation, but finding the factors of huge number takes much more time and computing power.
  3. A computer cannot factorise a number with more than 600 digits.
  4. Multiplication of two huge prime numbers, each around 300 digits, would be easier than the factorisation of their product.
- Numerical Example
  1. Here are two person Aice and Bob trying to communicatie and with help of RSA they generate keys and share public key to each other for further communication.
  2. Here Bob choses two prime numbers : p = 157 and q = 199.
  3. He then calculates n = p x q = 31243.
  4. Then he use euler's totient function to get :
     φ(n) = (p-1) (q-1)
          =  31243 - 157 - 199 + 1
           = 30888
   5. He selects e = 163 ('e' should be co-prime (relatively prime) to φ(n).
   6. He then selects d= 379, using e x d = 1 mod φ(n), e x d = 163 x 379 = 61777, and 61777 mod 30888 = 1.
   7. Public keys of bob is (n,e), i.e., (31243,163) and the private key is $(n,d), i.e., (31243,379).
   8. Let’s say that the value they want to encrypt is x = 13, then Alice would calculate and send y = x^e mod n = 13163 mod 31243 = 16341.
   9. Bob will decrypt the received value by calculating x = y^d mod n = 16341379 mod 31243 = 13. This way, Bob recovers the value that Alice sent. 
- RSA in CTFs
  1. There are many articles online which can explain RSA.
  2. Articles will give almost all information to complete the challenges.
  3. <a href="https://github.com/Ganapati/RsaCtfTool">RsaCtfTool</a> and <a href="https://github.com/ius/rsatool">rsatool</a> are both good tools for defeating RSA challenge in CTFs.
  4. Main variables in RSA in CTFs:-
     - p and q are large prime numbers
     - n is the product of p and q
     - The public key is n and e
     - The private key is n and d
     - m is used to represent the original message, i.e. plaintext
     - c represents the encrypted text, i.e., ciphertext.

🔴 Diffie-Hellman Key Exchange
- Key exchange aims to establish a shared secret between two parties.
- This method allows two parties to establish a shared secret (secret keys) over an insecure communication channel without requiring a pre-existing shared secret.
- If there is an observer in communication channel he will not able to get this key, while establishing the shared secret.
- After generating and establishing the shared key it can be used for symmetric encryption in subsequent communications.
- Here is the scenario where Alice and Bob want to talk securely, so they decided to establish a shared key for symmetric cryptography but they don't want to use asymmetric cryptography for key exchange. So here they will use Diffie-Hellman key Exchange.
  1. Alice and Bob decides the public variables: a large prime number 'p' and a generator or base 'g', where 0 < g < p.
  2. The public variables are the values that will be share publicly over communication channel despite the presence of adversaries.
  3. Suppose, both parties chose the value of p = 29 and g = 3, although in real case values would be far more greater than these values but here we took these values for simplify the calculations. 
  4. After this each party chooses a private number or integer. Let say Alic chooses a = 13 and Bob Choses b = 15. These numbers or integers are private keys and they must not be disclosed.
  5. After chosing the private keys, they calculates their public keys using their private keys:-
     - Alice Calucate A (public key) = g^a mod p
                                     = 3^13 mod 29 = 19
     - Bob calcuate B = g^b mod p = 3^15 mod 29 = 26
  These are their public keys.
  6. Alice and Bob send their keys to each other. Bob receives A = 19 and Alice receives B = 26. Here this step is called Key exchange.
  7. After getting each others public keys they can finally calculate the shared secret or secret key using the received public key and their own private key.
  8. Alice calculates - B^a mod p = 26^13 mod 29 = 10 and Bob calculates A^b mod p = 19^15 mod 29 = 10.
  9. Both get the shared secret key = 10 (g^ab mod p = 10).

<img width="1560" height="1180" alt="image" src="https://github.com/user-attachments/assets/c06b9d20-5b83-42a0-8121-afea1afe5c32" />

- Diffie-Hellman key exchange often used alongise RSA public key cryptography.
- Diffie-Hellman used for key agreement, RSA used for digital signatures, key transport, and authentication.
- RSA helps prove the identity of the person via digital signing.
