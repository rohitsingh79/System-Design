- whatapp end to end encryption

how it works 

- - For each chat session a session key is exchangd between user A and user B 
- The session Is key created by applying Diffie-Hellman Math
- User A takes the public key of B and uses the private key of itself to compute a shared secret and is stored on device A , same shared secret Is also generated at user B with the same algorithm (public key of A + private key of B)
- The secret key is not transmitted on the server only the public key
- And the messages are encrypted and decrypted on each device end
- Ratchet algorithm helps in creating different key for each message that is sent
- The above uses the SIGNAL protocol
- The pre-keys are sent by each user to the server when they are online and the other user downloads the key from the server to create the session , public key are stored in the database
- Key exhanges is done using asymmetric encryption (using both the public and the private key) and message encryption and decryption are done using aes (symmetric encryption nd decryption 256 bits )

- Symmetric encryption (aes)- keys are shared and known to each sender and the receiver
- Asymmetric encryption (rsa) - use of private and public key - difficult to implement 
