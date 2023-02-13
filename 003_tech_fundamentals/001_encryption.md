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
    * party A sends plaintext along w/a created symetric key. It goes to AES-256, it creates ciphertext, and that is forwarded to party B.
    * !problem. How does party B get the key safely? They can't.
    * This type of encryption is better for local file encryption.
2. Asymmetric encryption
    * two parties agree upon an asymmetric algorithm to use, then create encryption keys for the algorithm.
    * asym keys have a public and private key.