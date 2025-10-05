**First encrypt** the plaintext using your encryption standard, and symmetric encryption scheme such as a stream cipher or a block cipher. block ciphers like CBC and CFB modes are a little weird though because they propagate errors, so maybe use a ECB or CTR encryption scheme to produce a ciphertext with error localizing, so only the corrupted block is affected. then compute the MAC over the cipher text, so that attacks where an adversary manipulates ciphertext before MAC verification cannot occur. 
If the MAC came before the encryption, the MAC wouldn't protect the ciphertext directly, but the plaintext

![[Pasted image 20250526194911.png]]


encrypt IV using key k. then XOR the result with m1 to obtain the first ciphertext block c1. Then, encrypt c1 using key k. XOR the result with m2 to obtain the second ciphertext block c2. Continue to construct the ciphertext the same way


RSA

valid for e if p = 7 and q = 11


(p - 1) (q - 1)

= 60


find a number e, that does not divide 60 (anything that doesn't divide 60)


# Asymmetric Cryptography

diffie hellman secure key exchange


RSA - public key encryption systems

Security depends on hardness of integer factorisation:
given an integer 𝑁 = 𝑝 ⋅ 𝑞, find 𝑝 and 𝑞, where 𝑝 and 𝑞 are primes