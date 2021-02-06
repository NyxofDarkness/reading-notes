# Readings: Cryptography

## Encryption, Decryption & Hacking
## Ceasar Cipher

> The Caesar Cipher is a simple substitution cipher which replaces each original letter with a different letter in the alphabet by shifting the alphabet by a certain amount.

> Encryption: scrambling the data according to a secret key (in this case, the alphabet shift).
> Decryption: recovering the original data from scrambled data by using the secret key.
> Code cracking: uncovering the original data without knowing the secret, by using a variety of clever techniques.

## Cryptography Crash Course

cipher = is the algorithum of turning plain text into ciphertext. 

Data encription Standard.

AES chops data up into 16 byte blocks, and applies a series of substitution and permeations based on the key value, plus some other operations to obscure the message

## Introduction to Cryptography

> Hashing is a type of cryptography that changes a message into an unreadable string of text for the purpose of verifying the message’s contents, not hiding the message itself.

> Symmetric Cryptography, likely the most traditional form of cryptography, is also the system with which you are probably most familiar.  

> the following VPN services use AES encryption:

- NordVPN
- ExpressVPN
- Surfshark

> Asymmetric cryptography (as the name suggests) uses two different keys for encryption and decryption, as opposed to the single key used in symmetric cryptography.

> A key exchange algorithm, like Diffie-Hellman, is used to safely exchange encryption keys with an unknown party.

> The 4 Types of Cryptographic Functions

- Authentication
When we use the right cryptographic system, we can establish the identity of a remote user or system quite easily. The go-to example of this is the SSL certificate of a web server which provides proof to the user that they are connected to the right server.  

- Nonrepudiation: ensure that each unique user had indeed made a transaction request that would be irrefutable at a later time.

- Confidentiality

-  Integrity

> A VPN or Virtual Private Network allows you to create a secure connection to another network over the public Internet.

> HTTPS pages typically use either SSL (Secure Sockets Layer) or TLS (Transport Layer Security) to increase the security of your browsing experience with an asymmetric Public Key Infrastructure.

## How Computers Generate Random Numbers 