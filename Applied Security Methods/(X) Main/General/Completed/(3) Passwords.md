## **What is a password, and what is authentication**

- gain access to a system 
- authentication - verifying an actors identify

A password's strength is proportional to the **minimal** amount
of time it takes an adversary to correctly guess it. 

## **How do you measure uncertainty with entropy? assumption, intuition, mathematical formula, and calculation**

entropy is a measure of **uncertainty**

we want high entropy, so strong passwords that take a long time to guess

n bits of entropy means 2^n combinations for the adversary to search **N BITS = 2 TO THE N COMBINATIONS**

more combinations means => more checks required => longer time for adversary to crack password

## **what are the limitations of entropy**

Humans will not generate a password where the probability of choosing each symbol is uniform
different languages will use some symbols more than others
the probability of a symbol occurring will depend on the previous symbols

## **what are the new password guidelines**

verifiers shall require subscriber-chosen memorized secrets to be at least 8 characters in length
no other composition rules should be imposed
no random changes in memorized secrets
## **how are passwords stored? what are the benefits and limitations to each method***

hashed passwords - for safety if the password file is taken

## **How and why do hash functions work**

taking an input of any length and producing a fixed length hash. difficult to reverse the process

## **What is a dictionary attack?**

using a list of many common passwords to brute force guess a password

##  **What is meant by "adding salt"**

hash (salt + password) to prevent attackers from building a list of cryptographic hashes that work - and cant use precomputed tables
## **what is meant by using a "slow" hash function**

use hash functions that are designed to be slow like bcrypt or scrypt
	WHAT IS MEANT: intentionally meant to take an extremely long time to compute

