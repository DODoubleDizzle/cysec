# 1 Symmetric Encryption and Key Exchange
## 1.1 When to use encryption
- DB records
- Cloud storage
- Password storage
- Network communication
- Authentication data
- Payment and money transfers
## 1.2 Cryptography concepts
### 1.2.1 Cipher
An encryption algorithm is also called a cipher, it consists of a set of mathematical rules to encrypt and decrypt data.
### 1.2.2 Cryptographic key
A key is nothing more than a number.
Keys are used to encrypt data before it's sent over a network and decrypt it upon arrival. The key ensures that only someone with the correct key can decrypt and read the data. Basically the ciphered text is locked and this is the key.
### 1.2.3 One-Way Functions
A one-way function is a mathematical operation that easily produces output values for each possible combination of inputs but makes it impossible to retrieve the input values.
- There is no known true one-way function.
- Cryptographers rely on them
### 1.2.4 Reversability
Important because we should be able to decrypt which is basically reversing encryption

### 1.2.5 Number only used once (Nonce)
A nonce is a unique number or string used only once, countermeasure for replay attacks.

### 1.2.6 Initialization vector (IV)
- An IV is a random bit string 
- It is the same length as the block size and is XORed (⊕) with the message resulting in a new message which is then encrypted with the same key resulting in a different ciphertext for the same message
- The IV is typically sent alongside the encrypted message, often as a prefix to the ciphertext or in a separate data field, but not encrypted itself.
### 1.2.7 Confusion 
- Confusion occurs when the relationship between the plaintext and the key is so complicated that an attacker cant continue altering the plaintext and analyzing the resulting ciphertext to determine the key
- Substitution of bytes
### 1.2.8 Diffusion 
- Diffusion occurs when a change in the plaintext results in multiple changes spread throughout the ciphertext thus a small change in the input leads to a big change in the output
- [[###Permutation| Permutation]] of bytes
### 1.2.9 Permutation
Permutation of bytes refers to rearranging the order of bytes in a data block, according to a specific pattern or rule

## 1.3 Kerckhoffs' Principles
### 1.3.1 Security through Obscurity
- The security of a system or process is reliant on the confidentiality of how it operates.
### 1.3.2 The security of an encryption method is based on the secrecy of the key and not on the secrecy of the encryption algorithm

### 1.3.3 The enemy knows the system
- A cryptographic system should be secure even if everything about the system, except the key, is public knowledge
- This principle makes algorithms known and public, allowing anyone to examine and test them 
- Public exposure may expose weaknesses more quickly, leading to the abandonment of insufficiently strong algorithms and quicker adoption of suitable ones  
- Some believe that better overall security can be maintained by keeping both the algorithm and the key private.


## 1.4 Substitution Permutation Network
As mentioned above
Substitution: Replacing bytes with others 
Permutation: Swapping bytes around 
The substitutions and permutations are combined into a round. 
Rounds are then repeated many times

## 1.5 Caesar cipher
Notation ROTn
Rot stands for rotate, n for the amount of times, ROT3 means shift every letter by3.

## 1.6 XOR
Is like the OR operator but it returns false if both are true.
Applying XOR twice will result in the original message.

## 1.7 One time pad
We can design a cipher that uses XOR to encrypt and decrypt a message
• Use a key that’s the same length as the message
• XOR each message bit with each key bit
This is not practical and will need a giant key for big data.

## 1.8 Symmetric cryptography


## 1.9 Diffie-Hellman