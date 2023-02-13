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
** The upshot: 
