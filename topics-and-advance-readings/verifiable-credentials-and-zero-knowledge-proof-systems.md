# Combining Verifiable Credentials and Zero Knowledge Proof Systems

Authors: [Yancy Ribbens](mailto://yancy.ribbens@gmail.com)

## Abstract
Anonymous credentials enable a holder (prover) to reveal select information to a verifier during the verification process [[1]](#1).  In order to build anonymous credential systems, ZKPs can be combined with Verifiable Credentials to enhance user privacy.  This is a proposal to develop library support for Verifiable Credentials and recommend ZKP formats for different use cases and credential attributes.

## Introduction
Alice wishes to verify she meets the age requirement to vote.   In order to do so, she transmits her Verifiable Presentation (credential) to a verifier.  There are many ways to provide the verifier with information needed to decide if Alice meets the age requirements.  Consideration of varying levels of complexity and privacy need to be taken into account when implementing supporting libraries.

## Implementation
In a naive implementation, a verifier receives a credential from a prover in plain text.  The verifier examines the public key and hashes the credential, comparing the results of the hash against a blockchain which the issuer previously committed.  The verifier easily validates the age provided in the credential.  However, the verifier also learns all associated values of the credential as well.  While this solves the problem of validating Alice's age, there is no privacy preserving features of this implementation.

A slightly more complex implementation may provide only the attributes to the verifier which the verifier requires.  For example, the issuer commits a hash of the credential to a blockchain which is the composition of many hashed attributes.  When Alice wishes to prove only her age, she submits the age to the validator along with every other hashed attribute.  The validator then hashes Alice's age attribute along with the other hashes she submitted.  If the resulting hash matches the issuer committed value, the verifier can confirm the age attribute is the same value the issuer committed.  This offers Alice the ability to disclose attributes on a need to know basis, enabling other credential attributes to be private.  However, the validator will learn Alice's true age in the process of validation.

A more complex and privacy preserving implementation allows Alice to transmit a proof to the validator that her age is within an interval without revealing her true age.  The proof (range proof/bullet proof for example) validates if a committed number (her age) lies in an interval [[2]](#2).  If her age is within the interval the validator can confirm she meets an age requirement.  This method is the most privacy preserving but is a more complex implementation and may also be limited to select attributes types, such as age.

## Existing Libraries
Developing ZKP libraries that are specific to the Verifiable Credential use case may include examining general existing ZKP libraries.  Existing libraries that may be of interest are Daleks Bulletproofs using Rust [[3]](#3),  and the Camenisch-Lysyanskaya Signatures library in Java [[4]](#4). 

## Conclusion
There are a number of considerations when developing privacy preserving credential systems.  Developing libraries and formalizing recommendations for combining Verifiable Credentials with ZKPs will reduce the work required to implement privacy preserving Verifiable Credentials and provide a valuable service to the community.

### Notes
<a id="1"/>
[^1]:
     “Decentralized Anonymous Credentials”, The Johns Hopkins University Department of Computer Science, October 2013, https://eprint.iacr.org/2013/622.pdf
<br>
<br>
<a id="2"/>
[^2]:
     “Efficient Proofs that a Committed Number Lies in an Interval”, France Telecom - CNET, https://www.iacr.org/archive/eurocrypt2000/1807/18070437-new.pdf
<br>
<br>
<a id="3"/>
[^3]:
     “Camenisch-Lysyanskaya Signatures“, https://github.com/gijsvl/camenisch-lysyanskaya
<a id="4"/>
<br>
<br>
[^4]:
     “Bulletproofs“, https://github.com/dalek-cryptography/bulletproofs 
