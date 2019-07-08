---
tags: RWOT, KERI,
phone: 1-801-592-8230
email: sam@samuelsmith.org
---

# KERI for a Universal DKMI
 
[Samuel M. Smith Ph.D.](mailto:sam@samuelsmith.org)

version 0.2

## Abstract

The Key Event Receipt Infrastructure (KERI) provides a minimally sufficient means for managing signing authority and tracking events for a crypto-graphic key-pair based decentralized identifier such as a W3C DID [[1]][[2]]. This includes inception, rotation, interaction, and delegation. It includes single and multi-signature schemes. Both simple K of L and fractional weighted multi-signature schemes are supported. KERI uses a best practices one-time use rotation key with pre-rotation to minimize exploit due to key usage exposure. KERI's event streaming architecture is designed to be compatible with event streaming or decentralized autonomic data (DAD) applications such as IoT, Web 3.0, supply chain and analytics. The KERI core state verification engine is identifier agnostic (also DID method agnostic) so it may be used for any W3C DID as well as any crypto-graphic key-pair based identifier not merely a W3C DID. KERI does not require a distributed consensus ledger but may be augmented with such a ledger. As a result KERI is a candidate component of a universal decentralized key management infrastructure (DKMI). The goal of this paper is too explore how to foster KERI as an open standard component for a universal DKMI.

A more in depth technical description of KERI is provided here [[1]].
This paper extends the work of two earlier RWOT final papers [[3]][[4]].




## Introduction

Herein we define an identity for an entity simply as an identifier and attributes that may be used to describe the entity. Entities are not limited to natural persons but may include groups, organizations, software agents, things, and even data items. With a centralized identity system one entity controls all the identifiers. With a decentralized identity system, in contrast, disparate entities each control some of the identifiers but in an interoperable way. To restate, each entity may have a set of identifiers that it controls but are still recognized by the other entities. Each entity may control or be sovereign over a set of identifiers. In the case where an identifier refers to its controlling entity then that entity is self-sovereign over its own identifier and hence the identity associated with that identifier. This property of decentralized identity systems has given rise to the term self-sovereign identity (SSI). 

The typical approach to establishing or proving control over an identifier is to use a universally unique cryptographic digital signature based a key pair comprised of a public key and a private key. The identifier includes the public key or a unique fingerprint of the public key. The private key is used to digitally sign attestations that may be cryptographically verified using the public key. The holder of the private key is in control of the identifier because only that holder can sign attestations that may be cryptographically verified with the public key bound to that identifier. This makes the identifier self-certifying. 

### Source of Truth

The fundamental assumption is that the (public, private) key pair is universally unique and may be established using a random seed of sufficient size such that the likelihood of duplication (collision) is negligible. A typical method for generating the random seed is to use a cryptographic strength pseudo-random number generator with sufficient entropy. Currently 128 bits of entropy is considered sufficient. Other self-certifying identifier systems may use different means to generate and prove control over a universally unique identifier but this work is limited to systems where control is proven via cryptographic (public, private) key pair based digital signatures. In this sense there is one primary source of truth for the identifier and hence any key management operations applied to the associated (public, private) key pair. This source of truth is the set of signed attestations made with the private key and verifiable with the public key.
Although this work may be generally applied to any decentralized identity system that uses self-certifying identifiers, its primary focus is on decentralized identity systems that are interoperable with the emerging DID (Decentralized ID) standard 
.
### Minimally Sufficient Means

For decentralized identity systems based on self-certifying identifiers, management of the associated private keys is essential. Because the controlling entity holds their own private key(s) the primary burden of management falls on that entity or its assigns. The security of the identity is a function of the security of the management infrastructure. As mentioned above, unlike a centralized or administrative identity system where a central administrative entity controls all the identifiers, a decentralized identity system may have a multitude of controlling entities each controlling one or more identifiers. Some of these entities may not have the resources or the expertise to design, build, and maintain secure key management infrastructure. Consequently there is a need for open interoperable decentralized key management infrastructure (DKMI). Moreover, some applications of decentralized identity may benefit from DKMI that is scalable and performant. Example applications include data streaming, supply chain, IoT (internet of things), and other applications where data provenance among multiple controlling entities is important and data processing is demanding. One design approach to composing scalable and performant infrastructure is to find minimally sufficient means for each of the key management tasks. This is a primary motivation for this work, that is, to identify the minimally sufficient means for essential key management tasks. This does not imply that other means might not be beneficial or best for a given application but that by first understanding minimally sufficient means an implementor might have at hand more design options that might be customized to better fit a broader class of applications. 

### Distributed Ledgers

The primary alternative for decentralized key management infrastructure is a distributed ledger based on a distributed consensus algorithm that provides an additional source of truth for key management operations. There are many types of distributed consensus algorithms with various properties. One useful property of many distributed consensus algorithms is a total (global) ordering of events from multiple sources. This allows all transactions on the associated ledger to have a unique ordering with respect to one another. In the case of key management, for example, the total ordering property makes it easy to establish the ordering of key inception and rotation events. In addition to the aforementioned signed attestations with the private key, a distributed consensus ledger may be used as a source of truth in a DKMI. This may be as a primary (essential) source of truth this coupled to signed attestations or may be merely a secondary (non-essential) source of truth that provides complementary security. A distributed consensus ledger, however, may require a significant amount of infrastructure that must be setup, operated, and maintained. Typically infrastructure that depends on distributed consensus ledgers must tradeoff cost, throughput, and latency and as a result may not be as scalable or performant as infrastructure that does not depend on a distributed consensus ledger or that minimizes that dependency such as minimizing the number of operations that must be performed on the distributed consensus ledger. 

This work explores more scalable and performant DKMI that either minimizes the number of primary operations required on a distributed consensus ledger or merely uses a distributed consensus ledger as a secondary source of truth if at all. One way to avoid or minimize the use of a distributed consensus ledger is to leverage the fact that only the holder of the private key may create events that produce verifiable operations to the keys including the ordering of associated events. Thus a secondary source of truth merely needs to witness events and their ordering not provide the ordering.

### Key Management

The three main key management tasks are key reproduction, key recovery, and key rotation. We call these the three Rs of key management. The focus of this work is key rotation which may be the most difficult. 

#### Reproduction

Key reproduction includes the creation and derivation of (public, private) key pairs and the associated tracking and storage of the private keys. A discussion of key reproduction is provided elsewhere. But in summary one method that simplifies key reproduction tasks is the use of hierarchically deterministic key derivation algorithms that produce ((HD keys) or keychains. An HD key pair is usually derived from a root private key and some deterministic key path. The key path may be public. This means that there is no need to store the derived HD private key which is a security risk because the private key may be rederived on demand from the root key and the public derivation path. 

#### Recovery

Key recovery involves methods for securely backing up or distributing private keys such that they may be recovered in the event that the device holding the private key is lost or damaged. Key recovery approaches are also discussed elsewhere. 

#### Rotation

Key rotation involves methods for securely revoking a key pair and replacing it with a new key pair. Revoke without replace may be accomplished by merely rotating to a null key. Thus rotation may be implemented as a primary operation and revocation (without replace) may be implemented as a special case of rotation. The primary motivation for key rotation is to prevent, mitigate, or recover from an exploit of the private key due to exposure. The primary risk of exposure comes from use of the private key to sign attestations. Creating a signature typically requires loading the private onto a computing device in order to create the signature. Should an attacker exploit or capture the computing device they may gain access to the private key. In addition continued use of the private key to sign attestations may over time reduce the effort to cryptographically break the key. Finally over time cryptographic exploits of a given (public, private) key crypto-system may be discovered thereby rendering the key insecure. Best practice, therefore, is to enable the rotation of a given (public, private) key pair to a new (public, private) key pair either to the same crypto-system or to a stronger crypto-system. In decentralized identity systems, key rotation is useful when the controller of a self-certifying identifier needs to maintain persistent control over that identifier indefinitely despite exploits of the private key(s). Otherwise in the event of exploit, the controller could just abandon the exploited identifier and create a new identifier with a new (public, private) key pair. 

Periodically rotating the key bounds the risk of compromise resulting from exposure over time. This can be used proactively to upgrade the digital signature crypto-system to keep up with advances in computing.  The more difficult problem to solve is rotation after a specific exploit may have already occurred. In this case, the exploiter may create a valid signed rotation operation to a key pair under the exploiter’s control prior to the original controller detecting the exploit and they rotating to a new key pair under its own control. The exploiter could thereby either “capture” the identifier or create a conflict or race condition where two inconsistent but verifiable rotation events have been created. This work provides a scalable performant protocol  using pre-rotation or equivalently one-time rotation keys that solves the problem of secure rotation after an exploit may have occurred.

With self-certifying identifiers special semantics are applied to rotation. The public key associated with the identifier is not changed, but merely the private key that is authoritative for signing attestations is changed. Otherwise the identifier loses its value as an identifier. Consequently in order to verify an attestation belonging to a self-certifying identifier the verifier must know the key rotation history for that identifier. To clarify, the original public key from the initial (public, private) key pair is used to create the identifier. The identifier includes a reference to the public key. The original private key is used to cryptographically sign attestations that prove control over the identifier. The original public key is used to cryptographically verify the signatures. Each rotation operation creates a new (public, private) key pair. A valid rotation operation must be signed at the very least with the original private key. Rotation does not change the identifier. It still references the original public key. After rotation, however, attestations are now signed with the new private key and verified with the new public key. The original private key has been revoked and replaced with the new private key specified in the rotation operation. The new public key is included in the identifier’s key rotation history. Validation of an attestation first requires lookup and validation of  the key rotation history. The final rotation entry provides the current key pair used to sign and verify attestations.

The key rotation history of digital signing keys used to control an identifier, provides the basis for managing any other data affiliated with the identifier. In general, changes to the value of attributes associated with or under the control of a digital signing key pair may be managed by verifiable signed assertions using the signing key. Thus management of the signing key pair enables management of affiliated data including other keys such as encryption keys.

This work describes a protocol that provides secure verifiable rotation that solves the problem of successful exploit of a given private key due to exposure when that exploit happens sometime after creation and use of the key. It is assumed, however, that the private key remains private for some meaningful time after its creation. This protocol does not address the cryptographic security of a private key in the face of side channel attacks that capture the private key at the time of creation and/or first use nor brute force or other attacks that may break a private key given only the public key and signed attestations. Side channel attacks, however, may be prevented or mitigated in other ways.


## References

[1]. Smith, Samuel M., Key Event Receipt Infrastructure (KERI): Design and Build, http://arxiv.org/abs/1907.02143

[1]: http://arxiv.org/abs/1907.02143

[2]. W3C, “Decentralized Identifiers (DIDs),” W3C Draft Community Group Report, https://w3c-ccg.github.io/did-spec/

[2]: https://w3c-ccg.github.io/did-spec/

[3]. Smith, Samuel M., Decentralized Autonomic Data (DAD) and the three R's of Key Management. RWOT6 https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/DecentralizedAutonomicData.pdf

[3]: https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/DecentralizedAutonomicData.pdf

[4]. Conway, et al, A DID for Everything. RWOT7. https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/A_DID_for_everything.pdf

[4]: https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/A_DID_for_everything.pdf