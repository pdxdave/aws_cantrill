# Encryption

|  Encryption At Rest (EAR)                |  Encryption At Transit  (EAT)      |
| ----------------------------------       | ------------------------------     |
| protects from physical theft/tampering.  | protects data transmitted b/t two  |
| comp encrypts to storage, decrypts when  | places. encrypted at location A,   |
| reading from storage. if hd taken, data  | decrypted at location B.           |
| is still encrypted. w/o the passcode to  | anyone from the outside would      |
| decrypt, theif gets encrypted data.      | just see encrypted data.           |
| EAR is common in cloud. data is stored   |                                    |
| on shared hardware & encrypted.          |                                    |
| generally used when only one party       |                                    |
| involed. only they know the encryption   |                                    |
| and key                                  |                                    |

## Encryption terms
1. plaintext: unencrypted data. can be images, data, and text.
2. algorithm: takes plaintext & encryption key and writes encrypted data.
    * Blowfish, AES, RC4, DES, etc.
3. key: a password.
4. ciphertext: when an algorithm takes plaintext and a key it outputs ciphertext.    
** Encryption: an algorithm takes plaintext and a key, and outputs ciphertext.     
** Decryption: an algorithm takes ciphertext and a key, and generates plaintext.

## Types of Encryption
1. Symmetric encryption
    * two parties agree upon an encryption algorithm (AES-256).
    * party A sends plaintext along w/a created symmetric key. It goes to AES-256, it creates ciphertext, and that is forwarded to party B.
    * !problem. How does party B get the key safely? They can't.
    * This type of encryption is better for local file encryption.
2. Asymmetric encryption
    * two parties agree upon an asymmetric algorithm to use, then create encryption keys for the algorithm.
    * asym keys have a public and private key. Both parties need public and private keys.
    * the public key is for encryption, the private for decryption.
    * party A d/l party B's public key. The public key and plaintext are sent to the algorithm which generates ciphertext.
    * the ciphertext is sent to party B, and only they can decrypt the data. No key exchange required.
    * party B sends the private key and ciphertext to the algorithm, it decrypts the plaintext and is sent back to party B.
    * This is used b/t parties that don't need to see each other. Also SSH to access servers using key based authentication. 

## Signing: another use of Asymmetric keys
1. Let's assume that the Asymmetric encryption was successful, but now party B wants to respond back to party A and confirm that they received the message.
2. The problem. How do we know the response is from party B?  If party B has a public key available in the cloud then anyone could get it and respond to party A.
3. Party B could create a message and sign it with their private key and send the message to Party A. Party A uses Party B's public key and verifies it using Party B's private key attached to the message. This is the inverse of the process above.

## Steganography
1. The problem with encryption is that one can tell that it has been used.