
**• Define security services and name cryptographic systems that can**
**provide these services.**

• Security services are the specific security goals that we may want to
achieve.

• Confidentiality: Data cannot be viewed by unauthorized entities.

• Data integrity: Data cannot be altered in an unauthorized manner. (Hash function only does this)

• Data origin authentication: The identity of the entity that created the
data can be verified.

• Non-repudiation: An entity cannot deny a previous action. (Asymmetric Systems)

MAC = Data Integrity, Data Origin Authentication
signatures = all 3 

neither provide confidentiality

***Confidentiality** is only achieved through **encryption**—either symmetric (e.g., AES) or asymmetric (e.g., RSA).


**• Understand potential attacks against these generic systems, and**
**understand what level of security is usually required in practice.**

• Birthday attacks are often used to find collisions in hash functions: how many messages do
we need to randomly select before there is a greater than 50% chance of a collision


**• Define a cryptographic hash function and the properties required of**
**hash functions.**

A cryptographic hash function should provide the following properties:

• Preimage resistance: given a hash 𝑦, it should be computationally difficult to
find a message 𝑚 such that ℎ 𝑚 = 𝑦.

• Second preimage resistance: given a message 𝑚 and hash ℎ 𝑚 , it should be
computationally difficult to find a message 𝑚′ such that 𝑚 ≠ 𝑚′ and ℎ 𝑚 =
ℎ(𝑚′).

• Collision resistance: it should be difficult to find two messages 𝑚 and 𝑚′ such
that 𝑚 ≠ 𝑚′ and ℎ 𝑚 = ℎ(𝑚′).