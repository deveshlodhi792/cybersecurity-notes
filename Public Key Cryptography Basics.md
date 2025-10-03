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
   5. He selects e = 163 (e should be co-prime (relatively prime) to φ(n).
   6. He then selects d= 379, using e x d = 1 mod φ(n), e x d = 163 x 379 = 61777, and 61777 mod 30888 = 1.
   7. Public keys of bob is (n,e), i.e., (31243,163) and the private key is $(n,d), i.e., (31243,379).
   8. Let’s say that the value they want to encrypt is x = 13, then Alice would calculate and send y = xe mod n = 13163 mod 31243 = 16341.
   9. Bob will decrypt the received value by calculating x = yd mod n = 16341379 mod 31243 = 13. This way, Bob recovers the value that Alice sent. 
