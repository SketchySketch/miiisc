---
title: Cryptography 1
excerpt: >-
  In today's world cryptography is used everywhere. I will explain it step-by-step.
date: '2020-07-14'
template: post
---

References: [CommonLounge](https://www.commonlounge.com/discussion/20f56c5cfff24d5d87f8a583505bb122)

# Cryptography 1: Introduction

> Cryptography is the essential building block of independence for organisations on the Internet, just like armies are the essential building blocks...

## What Is Cryptography

**TL;DR: Cryptography is important, and the algorithms must be secure and stable.**

**Cryptography deals with a set of methods which enable us to store and transmit information while _safeguarding_ it from intruders.** That is, we can use cryptography methods to keep information private (say documents, passwords, etc on your computer), and to communicate in a way such that only the intended recipient can read the message.

Cryptography achieves this by converting data into a different form which is incomprehensible (often called ciphertext or code). The process of converting data to ciphertext is called encryption, and the process of converting retrieving data from ciphertext is known as decryption. Performing encryption and decryption requires secret information such as passwords (or keys).

### Goals of Cryptographic Algorithms: The CIA Triad

Cryptography has three main goals, typically referred to as the "CIA triad". In this section, we will define these goals of confidentiality, integrity, and authentication.
Confidentiality

#### Confidentiality
means that cryptographic algorithms attempt to keep the contents of a message secret. If Alice is sending a message to Bob, it should be impossible or computationally infeasible for Eve to learn the contents of an encrypted message without knowledge of the secret key.
Integrity

#### Integrity
means that a cryptographic algorithm verifies that a message was not modified in transit. Some ciphers provide a means for calculating a Message Authentication Code (MAC), which verifies the integrity of a message. Other ciphers do not intrinsically provide integrity protection.

For example, assume that Alice encrypts a message to Bob by encoding each letter as its position in the alphabet (A=1, B=2, etc.). If Eve can intercept the message, she can modify the message without Bob knowing.

#### Authentication
The third member of the CIA triad is authentication.
If Bob receives a message, he wants to be sure that Alice (and not Eve) sent it.

## A Simple Example: Caesar Cipher
Caesar cipher is... pretty old, but it *IS* a cipher. This is how it works:

```
For each alphabet 'r' in the string, shift it with a constant 'c'. If it reaches the end of alphabet table, reset it to the firse alphabet.

For example, given string "hello world", c = 7 and alphabet set [a-z]. The output is "olssv dvysk".
```

### Disadvantages
1. The Caesar cipher is easy to decrypt by trying (brute-force).
2. Only the first is enough.

## Improving the Caesar Cipher

We want the cipher to be more secure. Think about *why* the Caesar cipher is easy to break: the alphabet set is __not large enough__. Since we can't invent extra alphabets, we would like to think of another way.

Another important thing about Caesar cipher is the shift constant `c`. Because `c` is a constant, so we can try all `c`s until we find a `c` that makes the text readable. So we don't want others get `c`. So we can change `c` to a variable.

```
For each alphabet 'r' in the string, get a random integer 'c' in range [0, card(Alphabet Set) - 1], and shift it with 'c'.

For example, for string "hello world", alphabet set [a-z], random sequence {1, 4, 2, 7, 3, 8, 4, 3, 2, 4, 1}.
The output is "ijnsr artpe".
```

### Advantages
1. The string is hard to break if you don't know the random sequence. If you try brute-force, you will have to try `S^l` times, where `S` is `card(Alphabet Set)`, and `l` is the length of string.

### Disadvantages
1. Imformation to transmit become larger.
2. Listeners can still steal both imformation and break it easily.

## What's next?
As far as we go is just a peek of cryptography. In the next post I will introduce some modern ciphers, and scenes behind them.
