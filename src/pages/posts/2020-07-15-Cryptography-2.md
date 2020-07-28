---
title: Cryptography 2
date: "2020-07-15"
excerpt: >-
  In today's world cryptography is used everywhere. I will explain it step-by-step.
layout: post
---

[Portal to **Cryptography 1**](https://sketchy-sketch-code.netlify.app/posts/cryptography-1/)

# Cryptography 2: Asymmetric Ciphers and Mathematical Background

## Symmetic and Asymmetric Ciphers

**TL;DR: Symmetric ciphers are fast but hard to put in large use.**

Reference: 
1. [Brilliant, "Symmetric Ciphers"](https://brilliant.org/wiki/symmetric-ciphers/)
2. [The GNU Privacy Handbook, Chapter 2, "Public-key ciphers"](https://www.gnupg.org/gph/en/manual/x195.html)

**Symmetric ciphers** use symmetric algorithms to encrypt and decrypt data. These ciphers are used in symmetric key cryptography. A symmetric algorithm uses *the same key to encrypt data as it does to decrypt data*. For example, a symmetric algorithm will use key `kkk` to encrypt some plaintext information like a password into a **ciphertext**. Then, it uses `kkk` again to take that ciphertext and turn it back into the password.<sup>[1](https://brilliant.org/wiki/symmetric-ciphers/)</sup>

The primary problem with symmetric ciphers is not their security but with key exchange. Once the sender and receiver have exchanged keys, that key can be used to securely communicate, but what secure communication channel was used to communicate the key itself? In particular, it would probably be much easier for an attacker to work to intercept the key than it is to try all the keys in the key space. Another problem is the number of keys needed. If there are `n` people who need to communicate, then `n(n-1)/2` keys are needed for each pair of people to communicate privately. This may be ok for a small number of people but quickly becomes unwieldly for large groups of people.<sup>[2](https://www.gnupg.org/gph/en/manual/x195.html)</sup>

Symmetric ciphers are the opposite of asymmetric ciphers, like those used in public-key cryptography. These ciphers use asymmetric algorithms which use one key to encrypt data and a different key to decrypt ciphers. Typically, those two keys are called public and private keys, as is the case with RSA encryption. The public key is used to encrypt data, and the private key is used to decrypt data.<sup>[1](https://brilliant.org/wiki/symmetric-ciphers/)</sup>

## Public-Key Ciphers

Reference:
1. [The GNU Privacy Handbook, Chapter 2, "Public-key ciphers"](https://www.gnupg.org/gph/en/manual/x195.html)

Public-key ciphers were invented to avoid the key-exchange problem entirely. A public-key cipher uses a pair of keys for sending messages. The two keys belong to the person receiving the message. One key is a public key and may be given to anybody. The other key is a private key and is kept secret by the owner. A sender encrypts a message using the public key and once encrypted, only the private key may be used to decrypt it.<sup>[1](https://www.gnupg.org/gph/en/manual/x195.html)</sup>

### Mathematical Background


#### One-way trapdoor
Think of an easy (maybe) problem.
```
Multiply the prime numbers 67,867,979 and 179,424,673.
```
You should complete it if you will; then look at the next one:
```
Factorize 1,217,718,993,245,867 to m and n where m > n > 1.
```
OK... as you see, multiplying is easy, and in comparison factoring is _**extrmely hard**_. Actually the only answer is `67,867,979 * 179,424,673`.

The multiplying of *two big primes* is called a **one-way function**, for it's easy to compute, but hard to inverse.

A one-way trapdoor function is similar, but it has a trapdoor. That is, if some piece of information is known, it becomes easy to compute the inverse. For example, if you have a number made of two prime factors, then knowing one of the factors makes it easy to compute the second.<sup>[1](https://www.gnupg.org/gph/en/manual/x195.html)</sup>

#### Discrete Logarithm Problem

##### Modular Arithmetics
Modular arithmetics is an operation to compute the module of a division. For example, for **modulus** 13, we say `46 mod 13 is congruent to 7`. Easy.

For a prime modulus, say 17, we find the *primitive root* of the modulus, 3, which has an important property:
```
3^1  mod 17 = 3
3^2  mod 17 = 9
3^3  mod 17 = 10
3^4  mod 17 = 13
3^5  mod 17 = 5
3^6  mod 17 = 15
3^7  mod 17 = 11
3^8  mod 17 = 16
3^9  mod 17 = 14
3^10 mod 17 = 8
3^11 mod 17 = 7
3^12 mod 17 = 4
3^13 mod 17 = 12
3^14 mod 17 = 2
3^15 mod 17 = 6
3^16 mod 17 = 1

All the modules: {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16}
```
If we raise `3` to any exponent `x`, the frequecy of module `m` is equally likely between 0 and 16. So the reverse procedure is hard, because there are **infinite solutions**:
```
Solve 3^x mod 17 = 4
Answer:
x = 12, 29, ... , 17k + 12.
```
And this is called **discrete logarithm problem**. This is also a one-way trapdoor.
