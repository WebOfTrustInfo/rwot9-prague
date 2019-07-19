# Addressing DID Connection Man in the Middle Attacks

Author: Kyle Den Hartog
Date: 07/02/2019

## Summary

There's two options for addressing Man-in-the-middle (MITM) that are created by the Trust On First Use (TOFU) problem.

* Passing a hash of a key or DID Document through a trusted out of band channel. This is also called fingerprinting.
* Adding a key as a self-attested attribute to a credential.

## Overview of TOFU problem

The essensce of the the trust on first use problem, is best highlighted by it's [wikipedia article](https://en.wikipedia.org/wiki/Trust_on_first_use). In summary, the TOFU problem is created because it's not possible to verify with only a public key, who is the owner of the private key. This lack of knowledge gives rise to the introduction of MITM attacks. 

Put another way, if Alice were to generate a private key, essentially a secret number, and send the associated public key to Bob in an untrusted way (say a plaintext message), Bob would not have any guarantees that a Malicious actor, Mallory, didn't replace the public key in the message. This is because Bob isn't able to link the possession of the key to the identity he trusts. Rather, he must rely on additional mechanisms to "trust" that a private key is owned by who he believes to own it.

Additionally, even with the use of a traditional digital signature schemes like ECDSA and edDSA, these cryptographic mechanism don't provide guarantees of ***WHO*** owns the public key. It however does resolve the problem that someone possesses the private key. In many cryptographic systems (like Bitcoin) this is the only guarantee that is needed which is why they're so prevelant today.

By the nature of DIDs and DID method specifications and their use of a public key cryptography we then need to rely on external mechanisms to bootstrap trust, and find out who owns the private key. With the advent of DID methods, we've seen two classes of DID methods become common place. One is the use of DIDs that are anchored to a ledger, also known as an "***anchored DID***", and the other is based on the concept of a DID that can exist independent of a ledger. This is also known as an "***unanchored DID***". One of the most well known DID methods that support off-ledger functionality is the [DID:peer method](https://dhh1128.github.io/peer-did-method-spec/index.html).

With Anchored DIDs, the common solution for solving this problem relys on a single point of trust in order to bootstrap trust. The first point of trust is within the ledger itself. It relies on being able to trust that nodes within the network are properly validating signatures and not tampering with the DID Doc. Given that ledgers are being run on open source code, this is possible to be validated by someone who can read code or by trusting someone else who is able to read the code. With just this amount of information, it's possible to be certain that a DID doc hasn't been tampered with which alleviates the concerns of a MITM attack. 

To verify ***WHO*** owns an anchored DID an identity owner can rely on trust from either an out of band trusted channel or a verifiable credential. In either case, we don't have to worry about MITM attack vectors because the Ledger is validating that the signatures and associated keys haven't been tampered with.

However, with unanchored DIDs, we have a new set of problems that rely on bootstrapping trust through one of two methods. Either using an out of band channel like passing a DID in person (e.g. sharing QR code or NFC communication) or with a new method using Verifiable Credentials.

## Out-of-Band Channel Based Solutions

The core premise of using an out of band channel based solution is to be able to bootstrap the new channel of communication from an old channel of communication. In many cases this is an adequette solution, and in others it may require additional pieces of information in order to establish trust. 

This method has been used in previous systems is to rely on in person interactions to verify some piece of information. For example, in Wire message app, they rely on key fingerprinting which would be verified in person or another trusted channel. This [verification process](https://wire.com/en/blog/key-verification-secure-conversations/) allows wire message app users to verify the connection hasn't been MITM attacked.  

There's more approachable ways to adjust this method as well, but the core security properities would remain the same. For example, a [randomart](https://superuser.com/questions/22535/what-is-randomart-produced-by-ssh-keygen) image could be embedded into a QR code and then the randomart image could be displayed on the users device as well. The user would then be required to verify the image displayed on the user's device is the same as the one embedded in the QR code. This is a great way to handle short-lived, ephemeral connections such as unlocking a door while being sure the connection has not been MITM attacked.

## Verifiable Credentials Based Solutions

A verifiable credential method is a new approach to bootstrapping trust entirely within the connection. The idea behind this is that a third-party credential can be combined with a self-attested attribute in a credential proof to link the possession of the key to ***WHO*** is being interacted with. 

The general protocol would operate in this way:

1. Alice generates a DID Document and signs it with a private key that is associated with a public key listed in the DID Document.
2. Alice sends the signed, plaintext DID Document and signature to Bob.
3. Bob verifies the signature of the key and then stores Alice's DID Document.
4. Bob then uses Pack() to Anoncrypt his DID Document for the key Alice provided in the DID Document sent in step 2.
5. Bob sends his DID Document to Alice.
6. Bob then Authcrypts a proof request to Alice for a credential (e.g. a name from a passport) and a self attested attribute which contains Alice's public key she sent in step 2.
7. Alice generates the proof and sends it to Bob
8. Bob then verifies that the key that is attested in the credential is the same as the key listed in the DID Document of step 3.

The reason this works is because the blinded secret acts as a coupling mechanism to prove that the owner of the credential is the same as the owner of the public key. If bob detects that the key that Alice provides in the DID Document is different than the key he received in the Credential Proof, than he's able to detect that some aspect of the setup was done incorrectly or was tampered with. This is good enough indication that Bob should not trust this connection and should scrap it and reset it up.

One thing of particular importance to note in this method is that if a malicious actor, Mallory, possesses the same credential as Alice, she'll be able to provide that credential after tampering with the plaintext DID Document in step 2. In this case, what Bob should do is request a more unique credential. For example, Bob could request a name from a Driver's license and from a passport credential as well as the ZIP Code from the post office. This increase in correlateable information raises the assurance to Bob that Alice is the only person uniquely capable of providing all 3 credentials. As such this increase in correlation acts as an enhancement to the probablistic security guarantees that he's speaking with Alice and only Alice.