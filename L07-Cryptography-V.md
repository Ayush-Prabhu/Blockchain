## ✅ **Detailed Notes: RSA, Digital Signatures & Blockchain**

---

### 🔐 RSA Encryption & Decryption

#### **Public Key Encryption Process**
- Public key: Tuple `(e, n)`
- Message `M` is first converted to an integer `m`
- Ciphertext `c` is computed as:  
  `c = m^e mod n`
- `c` is sent to the recipient

#### **Private Key Decryption Process**
- Private key: Tuple `(d, n)`
- Decryption done by:  
  `m = c^d mod n`
- The result is converted back to the original message `M`
- Ensures confidentiality; only the intended recipient (who has the private key) can decrypt

---

### 🧮 **RSA Example**
- Choose primes: `p = 17`, `q = 11`
- Compute `n = p * q = 187`
- Euler's totient function: `φ(n) = (p-1)(q-1) = 160`
- Choose encryption key `e = 7` (relatively prime to 160)
- Compute decryption key `d = 23` such that `d * e ≡ 1 mod 160`

#### Example Message: `m = 88`
- **Encryption**:  
  `c = 88^7 mod 187 = 11`
- **Decryption**:  
  `m = 11^23 mod 187 = 88`

This confirms successful encryption and decryption using RSA.

---

### ✍️ **Digital Signatures Using RSA**

#### Basic Concept:
- Purpose: Ensure message authenticity, integrity, and non-repudiation
- Process:
  - Sender (Alice) signs the message using her **private key**
  - Receiver (Bob) verifies it using Alice's **public key**

#### Verification Logic:
- Alice sends: message `m` and its signed version `s = Encrypt(h(m), private_key)`
- Bob receives both
  - Computes hash of `m`: `h(m)`
  - Decrypts `s` with Alice’s public key to get `h'`
  - Verifies if `h(m) == h'`
  - If equal: signature is valid; message is from Alice

---

### 🔗 **Hashing + Digital Signatures in Blockchain**

#### Why Combine?
- Encrypting whole messages with private key is inefficient
- Instead, sign the **hash (digest)** of the message
- Reduces computational cost and signature size

#### Signature Generation:
1. Alice generates hash `h(m)`
2. Signs it: `s = Encrypt(h(m), private_key)`
3. Sends message `m` and signature `s`

#### Signature Verification:
1. Bob hashes received message: `h'(m)`
2. Decrypts `s` with Alice’s public key to get `h(m)`
3. Compares: if `h(m) == h'(m)`, signature is valid

---

### 🧾 **Use in Blockchain**

#### Role of Digital Signatures:
- Verify origin of a transaction
- Prevent **non-repudiation**: sender can’t deny initiating the transaction
- Prevent **impersonation**: signatures can’t be verified with anyone else’s public key

#### Example:
- Alice generates 10 coins → signs it: `(gen: 10, sig_A)`
- Then sends 5 coins to Bob → signs again: `(A → B: 5, sig_A)`
- Later verification ensures:
  - Only Alice could have signed these
  - Alice can't deny her transaction
  - Others (e.g., Carol) can’t claim ownership

---

### 🧰 Tools and Practice

- Public/private key pairs can be generated using online tools
- Example:
  - Alice encrypts “hello world” using Bob’s **public key**
  - Bob decrypts it using his **private key**
- For digital signatures:
  - Alice signs “hello world” with her **private key**
  - Bob verifies using Alice’s **public key**
- Hash functions (SHA256 etc.) are used to sign digests instead of full messages

---

### 🔑 Summary

- RSA provides secure communication via public key encryption
- Digital signatures ensure message authenticity and non-repudiation
- In blockchain:
  - Signatures validate transactions
  - Ensure that only rightful owners can initiate or claim transactions
- Bitcoin uses ECDSA (Elliptic Curve Digital Signature Algorithm)
- Cryptographic primitives: **RSA, hash functions, digital signatures**

---

## 🧠 Markdown Mindmap

```markdown
# Cryptographic Foundations
## RSA Algorithm
### Key Components
- Public Key: (e, n)
- Private Key: (d, n)
### Encryption
- c = m^e mod n
### Decryption
- m = c^d mod n
### Example
- p = 17, q = 11 → n = 187
- φ(n) = 160
- e = 7, d = 23
- Encrypt: 88^7 mod 187 = 11
- Decrypt: 11^23 mod 187 = 88

## Digital Signatures
### Purpose
- Authenticity
- Integrity
- Non-repudiation
### Process
- Sign with private key
- Verify with public key
### Optimization
- Use hash of message instead of full message
### Steps
1. Generate digest h(m)
2. Encrypt h(m) with private key → signature s
3. Send m and s
4. Receiver:
   - Hash m: h'(m)
   - Decrypt s → h(m)
   - Verify h'(m) == h(m)

## Applications in Blockchain
### Transaction Validation
- Sign transaction with sender's private key
- Verify with sender's public key
### Non-repudiation
- Sender can’t deny action
### Anti-Impersonation
- Others can’t claim someone else’s transaction
### Example
- Alice creates 10 coins → signs
- Alice sends 5 to Bob → signs
- Only verifiable using Alice's public key

## Cryptographic Tools
### Key Generation
- Online or programming libraries
### Encrypt/Decrypt
- Public key: anyone can encrypt
- Private key: only owner can decrypt
### Signature Example
- Alice signs "hello world"
- Bob verifies using Alice's public key

## Algorithms Used
- RSA (taught example)
- ECDSA (used in Bitcoin)
- Elliptic Curve Cryptography
- SHA-256 (common hash function)
```
