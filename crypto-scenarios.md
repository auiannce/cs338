Auiannce Euwing 

1.) Alice wants to send Bob a long message, and she doesn't want Eve to be able to read it
-
  - Alice and Bob run Diffie-Hellman to agree on a shared secret number, K.
  - Alice uses AES(K,M) to encrypt her message, M.
  - She sends the ciphertext to Bob
This works because only Alice and Bob know K, so Eve can't decrypt the message.

2.) Alice wants to send Bob a long message. She doesn't want Mal to be able to modify the message without Bob detecting the change.
 -
  - Alice takes message M and runs a hash on it like H(M) using SHA-256
  - She signs that hash message with her private key S_A so that it is E(S_A, H(M))
  - Send the M and E(S_A, H(M)) to Bob
  - Bob decrypts and computes H(M) and checks if E(P_A, (E(S_A, H(M)) equals H(M)
This works because if Mal changes a character of the message, the hash will be different, so they will not be equal

3.) Alice wants to send Bob a long message; she doesn't want Eve to be able to read it, and she wants Bob to have confidence that it was Alice who sent the message. 
- 
  - Alice and Bob do Diffie-Hellman to agree on a shared secret, K.
  - Alice takes the message M, and signs it with her private key E(S_A, M).
  - Then Alice encrypts everything with AES LIKE AES(K, M|| E(S_A, M)) and sends it to Bob.
  - Bob decrypts with K to get M|| E(S_A, M) and he varifies that E(P_A, E(S_A, M)) = H(M)
This works because AES keeps Eve from reading it, and the Signature proves it is really from Alice 

4.) Bob sues Alice 
- 
  - Her Private key was stolen and used to sign the fake documents as her. This is very plausible if Alice has bad private key storage.
  - Bob changed the contract after getting it and took the signature from the real contract and attached it to the end of the fake one. This isn't likely to happen since the signature is unique for every message.
  - Bob used the wrong public key, and this is believable because key change is not perfect and isn't verified.

5.) Bob's Certificate 
- 
  - Sig_CA consists of E(S_CA, H("bob.com"||P_B)

6.) Convince Alice that Bob has S_B for the cert
- 
  - Alice sends a random number N to Bob
  - Bob signs like E(S_B, H(N)) and sends that to Alice
  - Alice checks that the public key from the cert decrypts E(S_B, H(N)) and makes sure that it matches H(N).

7.) Mal tricks Alice
- 
  - Mal steals Bob's private key
  - There are weak identity checks at the CA, so Mal created a certificate for bob.com. 



