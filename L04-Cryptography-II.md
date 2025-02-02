# Basic Cryptographic Primitives: SHA-256 and Hashing Patterns

## Introduction
This lecture continues the discussion on basic cryptographic primitives, focusing on cryptographic hash functions, specifically SHA-256. We will explore the details of SHA-256, its importance in blockchain applications, and various methods for hashing multiple data items.

## Overview of SHA-256
- **SHA-256**: Stands for Secure Hash Algorithm 256-bit. It generates a fixed-size output of 256 bits, regardless of the input size.
- **Importance**: SHA-256 is widely used in Bitcoin mining and is a fundamental component of the Bitcoin blockchain.

## Steps in Creating Hashes Using SHA-256
1. **Preprocessing**:
   - The input message must be padded to ensure its length is a multiple of 512 bits.
   - If the length \( l \) of the message is not a multiple of 512, append a '1' bit followed by \( k \) zero bits, where \( k \) is the smallest non-negative solution to the equation:
     $$ l + 1 + k \equiv 448 \mod 512 $$
   - Finally, append a 64-bit block representing the original length of the message in binary.

2. **Partitioning**:
   - The preprocessed message is divided into \( n \) blocks of 512 bits each (e.g., \( m_1, m_2, \ldots, m_n \)).
   - Each 512-bit block is further divided into 16 sub-blocks of 32 bits each (e.g., \( m_{i0}, m_{i1}, \ldots, m_{i15} \)).

3. **Hash Computation**:
   - Start with a fixed initial hash value \( h_0 \).
   - Sequentially compute the hash values using the formula:
     $$ h_i = h_{i-1} + C(m_i, h_{i-1}) $$
   - Here, \( C \) is the SHA-256 compression function, and the addition is performed modulo \( 2^{32} \).
   - The final output \( h_n \) is the hash of the original message.

## Properties of SHA-256
- **Deterministic**: The same input will always produce the same output.
- **Collision Resistance**: It is computationally infeasible to find two different inputs that produce the same hash.
- **Pre-image Resistance**: Given a hash, it is difficult to find the original input.

## Patterns of Hashing Data
We can combine multiple data items using different hashing patterns:

1. **Independent Hashing**:
   - Hash each piece of data separately.
   - Example: Hash "hello" and "world!" independently.

2. **Repeated Hashing**:
   - Hash the output of a hash function.
   - Example: Hash "hello world!" to get a hash, then hash that hash.

3. **Combined Hashing**:
   - Concatenate the data before hashing.
   - Example: Hash the concatenated string "hello world!".

4. **Sequential Hashing**:
   - Hash one piece of data, then concatenate the hash with another piece before hashing again.
   - Example: Hash "hello", then concatenate with "world!" and hash the result.

5. **Hierarchical Hashing**:
   - Hash each piece of data independently, then hash the resulting hashes.
   - Example: Hash "hello" and "world!" separately, then hash the two resulting hashes.

## Practical Examples
- **Independent Hashing**: Hash "hello" and "world!" separately to get their respective hashes.
- **Repeated Hashing**: Hash "hello world!" to get a hash, then hash that hash.
- **Combined Hashing**: Concatenate "hello" and "world!" and hash the result.
- **Sequential Hashing**: Hash "hello", concatenate with "world!", and hash again.
- **Hierarchical Hashing**: Hash "hello" and "world!" separately, then hash the two hashes.

## Conclusion
In this lecture, we discussed the implementation of SHA-256 and various patterns for combining hashes. Understanding these concepts is crucial for constructing blockchain systems, particularly in the context of creating Merkle trees, which will be covered in the next lecture.

## References
1. "Blockchain Basics: A Non-Technical Introduction in 25 Steps" by Daniel Drescher.
2. "Cryptography and Network Security: Principles and Practice" by William Stallings.

Thank you for your attention!
