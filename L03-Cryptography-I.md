# Basic Cryptographic Primitives: Hash Functions

## Introduction
Cryptographic primitives are fundamental concepts and techniques essential for implementing blockchain technology. This lecture focuses on hash functions, their properties, and their applications in blockchain.

## What is a Hash Function?
A hash function is a function that takes an input (message) and produces a fixed-size output, known as the message digest. The key characteristics of cryptographic hash functions include:

- **Input Size**: Can take an arbitrarily sized string as input.
- **Output Size**: Produces a fixed-size output (commonly 256 bits).
- **Efficiency**: The hash function should be efficiently computable.

## Important Properties of Cryptographic Hash Functions
1. **Deterministic**: For a given input, the output (digest) is always the same.
2. **Collision-Free**: It should be infeasible to find two different inputs that produce the same output.
3. **Hiding**: Given a digest, it should be computationally difficult to determine the original input. Using **avalanche effect**.
4. **Puzzle Friendliness**: Given a message and a hash output, it should be difficult to find a value that, when concatenated with the message, produces the hash output.

## One-Way Function
Hash functions are one-way functions, meaning:
- It is easy to compute the hash from the input.
- It is difficult to retrieve the original input from the hash.

## Collision Resistance
- Finding two different inputs that produce the same hash (collision) is computationally difficult.
- The birthday paradox illustrates that the probability of collisions increases with the number of inputs, but with sufficiently large hash outputs (e.g., 256 bits needs 2^128 hashing computations), finding collisions remains impractical.

## Message Digest
Hash functions can be used as message digests, allowing for efficient comparison of messages:
- Instead of comparing entire messages, one can compare their hashes.
- If two hashes are the same, the original messages are assumed to be the same.

## Example of Hash Function Usage
- Generate hash values for given inputs (e.g., "hello world").
- Changing even a small part of the input (e.g., adding a space) results in a completely different hash, demonstrating the sensitivity of hash functions.

## Information Hiding through Hashing
- Hashing allows for committing a value and verifying it later.
- If a hash of a message is stored, it can be checked against a claimed message to confirm authenticity.

## Puzzle Friendliness in Mining
- Say M is chosen from a widely spread distribution, it is computationally difficult to find a k, such that Z = H(M||k), M and Z known a priori. (Z need not be a single value, but a set of values)
- In blockchain mining (e.g., Bitcoin), solving a puzzle involves finding a value that, when hashed with a message, produces a specific output.
- This property implies that random searching is often the best strategy for solving such puzzles.

## Conclusion
Hash functions are crucial in blockchain technology for ensuring data integrity, authenticity, and security. Understanding their properties and applications is essential for leveraging blockchain effectively.

## References
- "Blockchain Basics: A Non-Technical Introduction in 25 Steps" by Daniel Drescher.
- "Cryptography and Network Security: Principles and Practice" by William Stallings.
- Additional literature on cryptography and network security for further reading.
