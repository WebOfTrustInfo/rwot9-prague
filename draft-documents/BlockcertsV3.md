# Blockcerts V3.0

[Anthony Ronning](aronning@learningmachine.com) (Learning Machine), [Wong Wai Chung](waichung@nextid.com) (NextID)

## Abstract

As the standards around verifiable credentials are starting to take form, different flavors of ‘verifiable credentials-like` data structures need to make necessary changes to leverage on the rulesets outlined and constantly reviewed by a knowledgeable community like RWOT and W3C. The purpose of this paper is to identify all of the changes needed for Blockcerts to comply with the Verifiable Credentials (VCs) & Decentralized Identifiers standards, and the additional benefits by using a blockchain in combination with Verifiable Credentials. 

## VC Schema & Examples
Verifiable Credentials are a data schema that is defined and published as a Proposed Recommendation to W3C. It seeks to represent the same information that a physical credential represents that are also tamper-evident and more trustworthy while also addressing future considerations in our societies that are becoming increasingly digitalized. Some of these concerns include but are not limited to privacy-preserving goals.

An example of a minimally viable Verifiable Credential can be seen below: 

```
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://w3id.org/openbadges/v2"
  ],
  "id": "https://example.org/beths-robotics-badge.json",
  "type": ["VerifiableCredential", "OpenBadgesV2"],
  "issuer": "https://example.org/organization.json",
  "issuanceDate": "2016-12-31T23:59:59Z",
  "credentialSubject": {
    "id": "https://example.org/recipient-id.json",
    "roboticsForBeginners": {
      "id": "https://example.org/organization.json",
      "name": [{
        "value": "Awesome Robotics Badge",
        "lang": "en",
        "description": "For doing awesome things with robots that people think is pretty great.",
      }]
    }
  },
  
  "proof": {
    "type": "RsaSignature2018",
    "created": "2017-06-18T21:19:10Z",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "https://example.edu/issuers/keys/1",
    "jws": "eyJhbGciOiJSUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..TCYt5X
      sITJX1CxPCT8yAV-TVkIEq_PbChOMqsLfRoPsnsgw5WEuts01mq-pQy7UJiN5mgRxD-WUc
      X16dUEMGlv50aqzpqh4Qktb3rk-BuQy72IFLOqV0G_zS245-kronKb78cPN25DGlcTwLtj
      PAYuNzVBAh4vGHSrQyHUdBBPM"
  }
}
```


## BC V2 Schema & Examples

Currently, Blockcerts is an Extension to Open Badges, which is a specification and open technical standard originally developed by the Mozilla Foundation [https://openbadges.org/]. Open Badges is widely adopted by Universities and Microcredential platforms as a way to issue achievements and allows recipients to hold and collect them into "backpacks". The benefit of using a blockchain as an extension to Open Badges is to provide immutability and proof of existence.

An example standard Open Badge can be seen below:

```json
{
  "@context": "https://w3id.org/openbadges/v2",
  "type": "Assertion",
  "id": "https://example.org/beths-robotics-badge.json",
  "recipient": {
    "type": "email",
    "hashed": true,
    "salt": "deadsea",
    "identity": "sha256$c7ef86405ba71b85acd8e2e95166c4b111448089f2e1599f42fe1bba46e865c5"
  },
  "issuedOn": "2016-12-31T23:59:59Z",
  "badge": {
    "id": "https://example.org/robotics-badge.json",
    "type": "BadgeClass",
    "name": "Awesome Robotics Badge",
    "description": "For doing awesome things with robots that people think is pretty great.",
    "image": "https://example.org/robotics-badge.png",
    "criteria": "https://example.org/robotics-badge.html",
    "issuer": {
      "type": "Profile",
      "id": "https://example.org/organization.json",
      "name": "An Example Badge Issuer",
      "image": "https://example.org/logo.png",
      "url": "https://example.org",
      "email": "steved@example.org",
    }
  },
  "verification": {
    "type": "hosted"
  }
}
```

It can be separated into 3 parts, the assertion, the badge, and the issuer. 


Assertion

```json
{
  "@context": "https://w3id.org/openbadges/v2",
  "type": "Assertion",
  "id": "https://example.org/beths-robotics-badge.json",
  "recipient": {
    "type": "email",
    "hashed": true,
    "salt": "deadsea",
    "identity": "sha256$c7ef86405ba71b85acd8e2e95166c4b111448089f2e1599f42fe1bba46e865c5"
  },
  "image": "https://example.org/beths-robot-badge.png",
  "evidence": "https://example.org/beths-robot-work.html",
  "issuedOn": "2016-12-31T23:59:59Z",
  "badge": "https://example.org/robotics-badge.json",
  "verification": {
    "type": "hosted"
  }
}
```

`Assertion.badge` resolves into the below:

Badge

```json
{
    "@context": "https://w3id.org/openbadges/v2",
    "type": "BadgeClass",
    "id": "https://example.org/robotics-badge.json",
    "type": "BadgeClass",
    "name": "Awesome Robotics Badge",
    "description": "For doing awesome things with robots that people think is pretty great.",
    "image": "https://example.org/robotics-badge.png",
    "criteria": "https://example.org/robotics-badge.html",
    "issuer": "https://example.org/organization.json",
}
```

`Assertion.badge.issuer` resolves into the below:

Issuer

```json
{
    "@context": "https://w3id.org/openbadges/v2",
    "type": "Profile",
    "id": "https://example.org/organization.json",
    "name": "An Example Badge Issuer",
    "image": "https://example.org/logo.png",
    "url": "https://example.org",
    "email": "steved@example.org",
}
```



Blockcerts follows this model as well but with additional fields that allow it to be anchored by a blockchain. 

An example of a Blockcerts can be seen below:

```json
{
  "@context": [
    "https://w3id.org/openbadges/v2",
    "https://w3id.org/blockcerts/v2.1"
  ],
  "type": "Assertion",
  "id": "urn:uuid:bbba8553-8ec1-445f-82c9-a57251dd731c",
  "badge": {
    "id": "urn:uuid:82a4c9f2-3588-457b-80ea-da695571b8fc",
    "type": "BadgeClass",
    "name": "Certificate of Accomplishment",
    "image": "data:image/png;base64,...",
    "description": "Lorem ipsum dolor sit amet, mei docendi concludaturque ad, cu nec partem graece. Est aperiam consetetur cu, expetenda moderatius neglegentur ei nam, suas dolor laudem eam an.",
    "criteria": {
      "narrative": "Nibh iriure ei nam, modo ridens neglegentur mel eu. At his cibo mucius."
    },
    "issuer": {
      "id": "https://www.blockcerts.org/samples/2.0/issuer-testnet.json",
      "type": "Profile",
      "name": "University of Learning",
      "url": "https://www.issuer.org",
      "email": "contact@issuer.org",
      "revocationList": "https://www.blockcerts.org/samples/2.0/revocation-list-testnet.json",
      "image": "data:image/png;..."
    }
  },
  "recipient": {
    "hashed": false,
    "identity": "eularia@landroth.org",
    "type": "email"
  },
  "recipientProfile": {
    "type": [
      "RecipientProfile",
      "Extension"
    ],
    "publicKey": "ecdsa-koblitz-pubkey:mtr98kany9G1XYNU74pRnfBQmaCg2FZLmc",
    "name": "Eularia Landroth"
  },
  "issuedOn": "2017-06-29T14:58:57.461422+00:00",
  "verification": {
    "publicKey": "ecdsa-koblitz-pubkey:msBCHdwaQ7N2ypBYupkp6uNxtr9Pg76imj",
    "type": [
      "MerkleProofVerification2017",
      "Extension"
    ]
  },
  "signature": {
    "type": [
      "MerkleProof2017",
      "Extension"
    ],
    "targetHash": "637ec732fa4b7b56f4c15a6a12680519a17a9e9eade09f5b424a48eb0e6f5ad0",
    "merkleRoot": "f029b45bb1a7b1f0b970f6de35344b73cccd16177b4c037acbc2541c7fc27078",
    "anchors": [
      {
        "sourceId": "d75b7a5bdb3d5244b753e6b84e987267cfa4ffa7a532a2ed49ad3848be1d82f8",
        "type": "BTCOpReturn",
        "chain": "bitcoinMainnet"
      }
    ],
    "proof": [
      {
        "right": "11174e220fe74de907d1107e2a357e41434123f2948fc6b946fbfd7e3e3eecd1"
      }
    ]
  }
}
```

Besides some of the minor differences in layout/metadata between the example Blockcerts and example Open Badge, the main differences in schema (ie, the Blockcerts extensions), are below.

**RecipientProfile** (https://www.blockcerts.org/schema/2.0/recipientSchema.json)

```json
"recipientProfile": {
    "type": [
      "RecipientProfile",
      "Extension"
    ],
    "publicKey": "ecdsa-koblitz-pubkey:mtr98kany9G1XYNU74pRnfBQmaCg2FZLmc",
    "name": "Eularia Landroth"
  }
```

This allows for additional recipient information that can be used to make a strong claim of ownership over the credential. In addition to the `name` and `publicKey` properties in this example, there is an `id` field in this schema that is reserved for future uses of DIDs. 


**Verification** (https://github.com/IMSGlobal/cert-schema/blob/master/docs/open_badge_v2_extensions.md)

```json
"verification": {
    "publicKey": "ecdsa-koblitz-pubkey:msBCHdwaQ7N2ypBYupkp6uNxtr9Pg76imj",
    "type": [
      "MerkleProofVerification2017",
      "Extension"
    ]
  }
```

In this case, Verification is an Open Badge `VerificationObject` with a `MerkleProofVerification2017` extension to allow for the `publicKey` of the issuer. It is used during the verification step of Blockcerts to ensure that the issuer public key matches the public key creating the blockchain transaction with this credential.

One of the last major differences is `Signature` with the MerkleProof2017 extension

**Signature** (https://www.blockcerts.org/schema/2.0/merkleProof2017Schema.json)

```json
"signature": {
    "type": [
      "MerkleProof2017",
      "Extension"
    ],
    "targetHash": "637ec732fa4b7b56f4c15a6a12680519a17a9e9eade09f5b424a48eb0e6f5ad0",
    "merkleRoot": "f029b45bb1a7b1f0b970f6de35344b73cccd16177b4c037acbc2541c7fc27078",
    "anchors": [
      {
        "sourceId": "d75b7a5bdb3d5244b753e6b84e987267cfa4ffa7a532a2ed49ad3848be1d82f8",
        "type": "BTCOpReturn",
        "chain": "bitcoinMainnet"
      }
    ],
    "proof": [
      {
        "right": "11174e220fe74de907d1107e2a357e41434123f2948fc6b946fbfd7e3e3eecd1"
      }
    ]
}
```

In this property, we go through all of the Merkle proofs required to validate a hash against a Merkle root hash on a blockchain. For more information on this procedure, visit the spec (https://w3c-dvcg.github.io/lds-merkleproof2017/).



**Issuer** 

Most of the properties in `issuer` come directly from the Open Badges spec, an example of a Blockcerts' "Issuer Profile" can be seen below:

```json
{
  "@context": [
    "https://w3id.org/openbadges/v2",
    "https://w3id.org/blockcerts/v2"
  ],
  "type": "Profile",
  "id": "https://www.blockcerts.org/samples/2.0/issuer-testnet.json",
  "name": "University of Learning",
  "url": "https://www.issuer.org",
  "introductionURL": "https://www.issuer.org/intro/",
  "publicKey": [
    {
      "id": "ecdsa-koblitz-pubkey:msBCHdwaQ7N2ypBYupkp6uNxtr9Pg76imj",
      "created": "2017-06-29T14:48:03.814936+00:00"
    }
  ],
  "revocationList": "https://www.blockcerts.org/samples/2.0/revocation-list-testnet.json",
  "image": "data:image/png;base64,iVBORw0KGgo...",
  "email": "contact@issuer.org"
}
```

When verifying a Blockcert, the Issuer is checked to ensure that its public key anchored the Blockcert to the blockchain. After this check, the `revocationList` is checked to ensure that the issuer has not revoked their credential.

One field added to this is the `IntroductionURL`: 

**IntroductionURL**

This is used for a client (ie, Blockcerts Wallet) to do a POST API call to transmit their public key to the issuer for the issuer to include their key in the `RecipientProfile` of a Blockcerts.


More information about the exact schema being used for Blockcerts can be found here (https://www.blockcerts.org/schema/2.0/context.json) & general information here (https://github.com/blockchain-certificates/cert-schema/blob/master/docs/schema-2.md).


This URL-based "Issuer Profile" will be improved by using DID's for issuers. More on this later. 

## Blockcerts as VC Implementation

Focusing on the Blockcerts specific additions to Open Badges (`recipientProfile`, `verification`, and `signature`) we can make the following mappings over to a VC.

### `recipientProfile`
This part could essentially go away and be replaced with `credentialSubject.id` and `credentialSubject.name`. 

TODO figure out if putting `ecdsa-koblitz-pubkey:mtr98kany9G1XYNU74pRnfBQmaCg2FZLmc` in to `credentialSubject.id` is okay. Ideally, this is a DID, but wondering how agnostic the `id` field is. 

```json
"recipientProfile": {
    "type": [
      "RecipientProfile",
      "Extension"
    ],
    "publicKey": "ecdsa-koblitz-pubkey:mtr98kany9G1XYNU74pRnfBQmaCg2FZLmc",
    "name": "Eularia Landroth"
  }
```

becomes 

```json
  "credentialSubject": {
    "id": "ecdsa-koblitz-pubkey:mtr98kany9G1XYNU74pRnfBQmaCg2FZLmc", // can use DID
    "name": "Eularia Landroth"
    // example claim
    "alumniOf": {
      "id": "did:example:c276e12ec21ebfeb1f712ebc6f1",
      "name": [{
        "value": "Example University",
        "lang": "en"
      }, {
        "value": "Exemple d'Université",
        "lang": "fr"
      }]
    }
  }
```

### `verification` 

As specified in "BC V2 Schema & Examples" above, `verification` is used to verify the public key of the issuer matches the public key used to issue the transaction to a blockchain. 

It may seem as though we could get away with putting the `verification` public key in the issuer DID instead, but, depending on the DID method, that could be changed. For Blockcerts issued to a blockchain, we may want to leave `verification` inside the document to verify the blockchain public key the issuer was wanting to issue the certificate from.

This could be considered a redundant property since the Verifiable Credential will have a proof property that verifies immutability as well, and the "issuer profile" already specifies their keys used for issuing. The VC & DID spec allows for referencing these keys directly already. 


#### Signature / Proof Proposal

Verifiable Credentials require a `proof` property that is used for verifying the immutability of a VC as well as proving that a certain issuer is the one that signed the VC. Before VC, Blockcerts used `signature` to prove immutability. What role does `signature` provide if we are already required to implement `proof`? 

One important property that all `proof` methods do not provide alone with typical signing keys is the aspect of time stamping. A `created` date can be applied to `proof`, but since that can be created with any date, we cannot prove it existed at a certain time. Using a blockchain can be beneficial here, as it proves that the document existed with a high degree of certainty at the time of the transaction (collisions technically can still occur due to hashing, though improvable). 

We should continue making a blockchain `signature` required in some capacity so that we can provide the value of life long credentials through this Proof of Verifiable Existence method. 


**Blockchain proof option 1** - Anchor and then sign

Due to possible interoperable concerns, in the beginning, one proposal is that we write `signature` inside of the certificate, which hashes & anchors the certificate data, and then the issuer signs the cert data & `signature` (anchor proof) with any of their keys listed in their DID/"Issuer Profile" to have a strong claim over the certificate data and the blockchain anchoring.

```json
...
[Cert Data]
...
"signature": {
    "type": [
      "MerkleProof2017",
      "Extension"
    ],
    "merkleRoot": "b2ceea1d52627b6ed8d919ad1039eca32f6e099ef4a357cbb7f7361c471ea6c8",
    "targetHash": "552f01d4fab7da1bce4315c134a1d46e9ef5968f49edf6f5de5d3a2776eea4fb", //Cert Data Hash
    "proof": [
      {
        "right": "776aca4dc61d70480fb05e4d95aaedc719fedd752eab7d517e04af2f481f92af"
      },
      {
        "left": "6613ea6c78b0d93a45c725f3fcc9f2312181ffad0a6833299663d6aa1d7806a9"
      },
      {
        "right": "e780cd2fe41df361fa7c047191533fe6252ea20bcd0fc8b226da3656d1133e56"
      }
    ],
    "anchors": [
      {
        "sourceId": "2378076e8e140012814e98a2b2cb1af07ec760b239c1d6d93ba54d658a010ecd",
        "type": "BTCOpReturn",
        "chain": "bitcoinMainnet"
      }
    ]
  },
  "proof": {
    "type": "RsaSignature2018",
    "created": "2017-06-18T21:19:10Z",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "did:example:ebfeb1f712ebc6f1c276e12ec21#key1",
    "jws": "eyJhbGciOiJSUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..TCYt5XsITJX1CxPCT8yAV-TVkIEq_PbChOMqsLfRoPsnsgw5WEuts01mq-pQy7UJiN5mgRxD-WUcX16dUEMGlv50aqzpqh4Qktb3rk-BuQy72IFLOqV0G_zS245-kronKb78cPN25DGlcTwLtjPAYuNzVBAh4vGHSrQyHUdBBPM" // verifies Cert Data + Signature
  }
```

Other Verifiable Credential wallets besides Blockcerts would not need to check `signature` for blockchain anchoring to verify the integrity of the certificate. Not checking `signature` would mean that they cannot guarantee proof of existence during a time in which a key was valid (in the case of key revocation by the issuer).

This may provide better interoperability amongst VC wallets in the beginning.


**Blockchain proof option 2** Both Anchor and Sign inside `proof`

It may be possible to create a new (or reuse existing `signature` extension) `proof` that supports the structure/purpose defined in `signature` previously as an extension to `ld-proofs`. This would allow us to add multiple proofs (such as RSA signing key AND blockchain anchoring proof) to a Blockcerts VC. `proof` can be an array that allows multiple proofs, but the main reason to have a traditional signing proof and a blockchain proof is so that VC verifiers do not have to support blockchain-based verification in order for a Blockcerts VC to verify. If a recipient has a Blockcerts VC-based credential, they may take the credential to any VC standard wallet, but suggested to use an Open Source Blockcerts verifier to take advantage of the Proof of Verifiable Existance scheme that a traditional VC can not guarentee unless they can understand and check the blockchain proof.  

Alternatively, we write both `signature` proof and more common proof (such as `RsaSignature2018`) in the `proof` section of a certificate. This would assume that Verifiable Credential wallets will attempt to check multiple proofs and safely ignore proofs that they do not understand.  

```json
...
[Cert Data Hash]
...
  "proof": [{
    "type": "RsaSignature2018",
    "created": "2017-06-18T21:19:10Z",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "did:example:ebfeb1f712ebc6f1c276e12ec21#key1",
    "jws": "eyJhbGciOiJSUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..TCYt5XsITJX1CxPCT8yAV-TVkIEq_PbChOMqsLfRoPsnsgw5WEuts01mq-pQy7UJiN5mgRxD-WUcX16dUEMGlv50aqzpqh4Qktb3rk-BuQy72IFLOqV0G_zS245-kronKb78cPN25DGlcTwLtjPAYuNzVBAh4vGHSrQyHUdBBPM" // verifies Cert Data
  },
  {
    "type": [
      "MerkleProof2017",
      "Extension"
    ],
    "merkleRoot": "b2ceea1d52627b6ed8d919ad1039eca32f6e099ef4a357cbb7f7361c471ea6c8",
    "targetHash": "552f01d4fab7da1bce4315c134a1d46e9ef5968f49edf6f5de5d3a2776eea4fb", // Cert Data Hash
    "proof": [
      {
        "right": "776aca4dc61d70480fb05e4d95aaedc719fedd752eab7d517e04af2f481f92af"
      },
      {
        "left": "6613ea6c78b0d93a45c725f3fcc9f2312181ffad0a6833299663d6aa1d7806a9"
      },
      {
        "right": "e780cd2fe41df361fa7c047191533fe6252ea20bcd0fc8b226da3656d1133e56"
      }
    ],
    "anchors": [
      {
        "sourceId": "2378076e8e140012814e98a2b2cb1af07ec760b239c1d6d93ba54d658a010ecd",
        "type": "BTCOpReturn",
        "chain": "bitcoinMainnet"
      }
    ]
  }]
```

There are some papers & proposals already written for going down this path. (https://github.com/WebOfTrustInfo/rwot3-sf/blob/master/topics-and-advance-readings/blockchain-extensions-for-linked-data-signatures.md) & (https://web-payments.org/specs/source/pop2016/).

**Blockchain proof option 3** Only use blockchain proof

The first two options allow for better interoperability with other verifiable credential verifiers/wallets as they get developed. Alternatively we only specify that a blockchain proof is required and leave it up to implementers to decide whether or not they want to add other proof types. 

The following example is much like option 2, but instead of a RSA proof and a blockchain proof, it is just a blockchain proof. 

```json
...
[Cert Data Hash]
...
  "proof": 
  {
    "type": [
      "MerkleProof2017",
      "Extension"
    ],
    "merkleRoot": "b2ceea1d52627b6ed8d919ad1039eca32f6e099ef4a357cbb7f7361c471ea6c8",
    "targetHash": "552f01d4fab7da1bce4315c134a1d46e9ef5968f49edf6f5de5d3a2776eea4fb", // Cert Data Hash
    "proof": [
      {
        "right": "776aca4dc61d70480fb05e4d95aaedc719fedd752eab7d517e04af2f481f92af"
      },
      {
        "left": "6613ea6c78b0d93a45c725f3fcc9f2312181ffad0a6833299663d6aa1d7806a9"
      },
      {
        "right": "e780cd2fe41df361fa7c047191533fe6252ea20bcd0fc8b226da3656d1133e56"
      }
    ],
    "anchors": [
      {
        "sourceId": "2378076e8e140012814e98a2b2cb1af07ec760b239c1d6d93ba54d658a010ecd",
        "type": "BTCOpReturn",
        "chain": "bitcoinMainnet"
      }
    ]
  }
```

#### Issuer Key Revocations 

In addition to proof of existence, using a Blockchain can get additional benefits when factoring in revocation use cases. Say a non-blockchain based VC was signed with an RSA key. The Signature Proof has a `createdDate` associated with the signature, but we cannot prove that date is correct in actuality. Simply that the person/process signing the key claimed that as the time they signed. 

In most cases, the issuer signing with keys they own should be signing with the correct time. However, in situations where the signing key was stolen, the thief might want to issue a credential in the past to make it appear as though they, for instance, graduated with a degree at a college when they first started issuing VC's. 

The college realizes their key was stolen, compromised, or simply they practice good key rotation hygiene. In any of these cases, the true issuer now revokes that key with an expiration date set to a day before the known theft. 

Since credential dates can not be trusted, we can not determine which credentials fall within the `createdDate` & `revocationDate` (TODO or is it called the `expirationDate` still?) range for a given key. Every single credential issued with a key that was stolen NEEDS to fail (or at least warn) for signing key verification problems during the credential verification process. One bad credential issued with a stolen key can affect the status of every single recipient that received a credential from that issuer with that specific signing key. This is not satisfactory when it comes to life-long credentials. 

Therefore, by utilizing the trusted timestamps of a blockchain, we can calculate the true issuance date and determine that if an issuer revoked/expired a signing key for a specific date, every credential that has an anchor on a blockchain before that date is unaffected by key revocations. Instead of just providing Proof of Existence, we can then coin the term Proof of Verifiable Existence with Blockchain-based VCs. Not only did the document exist, but it existed and will always verify as long as the individual credential does not get revoked, or there is a question as to if the signing key was stolen around the same time as a bad issuance.

### Additional Fields

In addition to the existing fields specified above, there are several fields in Blockcerts V2 that have had non-standard support in the ecosystem that could benefit from being standardized. 

#### `display`

In Blockcerts V2, we've been building a lot of support for `displayHtml` unofficially. In mobile wallets, verifiers, etc. As well as 3rd party libraries built for it as well. 

Proposing for V3, it would be great if we can throw in official support for displays. Extending past `displayHtml`, we should allow support for any type of display. Some may not want to use `html` but instead use `pdf`, an `image`, etc. 

**Option 1**
For the schema, it can simply be `type` and `data` properties.

Example:

```json
"display": {
    "type": "html",
    "data": "<p>hello world</p>"
    }
```


**Option  2**

Alternatively, we can use DATA URLs (https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs) instead. 

```json
"display": "data:text/html,%3Ch1%3EHello%2C%20World!%3C%2Fh1%3E"
```

#### `metadata`

Similar to the above `display`/`displayHtml` section, we similarily do not have an official standard around the use of the `metadatajson` property we have. We have unofficial support in both the mobile app & verifier to display some metadata information to the viewer. 

**Option 1**
We could add this to the standard, but allow for different types of metadata format, maybe `XSD` for example, it would allow issuers to take advantage of that, and continue to support it officially in some of the Blockcerts ecosystems. 

Could be similar to `display`, adding `type` & `data`. 

```json
"metadata": {
    "type": "json",
    "data": "{\"test\": true"
}
```

**Option 2**

Remove completely. Metadata could be grabbed by the `credentialSubject` field. The VC spec does not have requirements over the types of information that could be mentioned `credentialSubject`, but because this is where the "holder" and "subject" properties live, it makes sense that any sort of additional metadata lives here. This will be consistent and interoperable with other verifiable credentials that are not Blockcerts, and other verifiable credential wallets. 

## Badge Claim
Going off of the paper written from a previous RWoT over open badges as a VC (https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/open-badges-are-verifiable-credentials.md), an example badge claim we can create for those that want a similar badge-like experience could look like below. 

```json
"credentialSubject": {
        "id": "https://example.com/profiles/bob",
        "bc:holds": {
            "id": "https://example.com/badgeclasses/123",
            "type": "BadgeClass",
            "name": "Certificate of Accomplishment",
            "image": "data:image/png;base64,...",
            "description": "A badge describing great accomplishments",
            "criteria": {
                "narrative": "Perform tasks of valor and wit."
            },
            "issuer": {
                "type": "Profile",
                "id": "https://example.com/profiles/alice",
                "name": "Example Issuer",
                "url": "http://example.com",
                "email": "test@example.com"
            }
        }
    }
```

`bc:holds` can be used instead of `obi:holds` since Open Badges has not moved to VC or created this type of claim yet. 


This type of claim is not required as part of the Blockcerts V3 standard. Any type of claim can be made.


## Example Blockcerts V3
Credential:

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://w3id.org/blockcerts/v3"
  ],
  "id": "urn:uuid:bbba8553-8ec1-445f-82c9-a57251dd731c",
  "type": ["VerifiableCredential", "BlockcertsCredential"],
  "issuer": "did:example:23adb1f712ebc6f1c276eba4dfa",
  "issuanceDate": "2010-01-01T19:73:24Z",
  "credentialSubject": {
      "id": "did:example:ebfeb1f712ebc6f1c276e12ec21",
      "holds": {
           "id": "https://example.com/badgeclasses/123",
          "type": "BadgeClass",
          "name": "Certificate of Accomplishment",
          "image": "data:image/png;base64,...",
          "description": "A badge describing great accomplishments",
          "criteria": {
              "narrative": "Perform tasks of valor and wit."
          },
          "issuer": {
              "type": "Profile",
              "id": "did:example:23adb1f712ebc6f1c276eba4dfa",
              "name": "Example Issuer",
              "url": "http://example.com",
              "email": "test@example.com"
          }
      }
  },
  "metadata": {
    "type": "json",
    "data": "{\"class\": \"2019\""
  },
  "display": {
    "type": "html",
    "data": "<p>This subject has received this Certificate of Accomplishment</p>"
  },
  "verification": {
    "type": [
      "MerkleProofVerification2017",
      "Extension"
    ],
    "publicKey": "ecdsa-koblitz-pubkey:1AwdUWQzJgfDDjeKtpPzMfYMHejFBrxZfo"
  },
  "signature": { // could put this in proof section as well
    "type": [
      "MerkleProof2017",
      "Extension"
    ],
    "merkleRoot": "b2ceea1d52627b6ed8d919ad1039eca32f6e099ef4a357cbb7f7361c471ea6c8",
    "targetHash": "552f01d4fab7da1bce4315c134a1d46e9ef5968f49edf6f5de5d3a2776eea4fb",
    "proof": [
      {
        "right": "776aca4dc61d70480fb05e4d95aaedc719fedd752eab7d517e04af2f481f92af"
      },
      {
        "left": "6613ea6c78b0d93a45c725f3fcc9f2312181ffad0a6833299663d6aa1d7806a9"
      },
      {
        "right": "e780cd2fe41df361fa7c047191533fe6252ea20bcd0fc8b226da3656d1133e56"
      }
    ],
    "anchors": [
      {
        "sourceId": "2378076e8e140012814e98a2b2cb1af07ec760b239c1d6d93ba54d658a010ecd",
        "type": "BTCOpReturn",
        "chain": "bitcoinMainnet"
      }
    ]
  },
  "proof": {
    "type": "RsaSignature2018",
    "created": "2017-06-18T21:19:10Z",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "did:example:ebfeb1f712ebc6f1c276e12ec21#key1",
    "jws": "eyJhbGciOiJSUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..TCYt5XsITJX1CxPCT8yAV-TVkIEq_PbChOMqsLfRoPsnsgw5WEuts01mq-pQy7UJiN5mgRxD-WUcX16dUEMGlv50aqzpqh4Qktb3rk-BuQy72IFLOqV0G_zS245-kronKb78cPN25DGlcTwLtjPAYuNzVBAh4vGHSrQyHUdBBPM"
  }
}
```

## Issuer Profile

By moving to a Verifiable Credential standard that is capable of utilizing Decentralized Identifiers, we are now removing the reliance of URLs inside certificates. 

As an Open Badge extension (and while VC's &  DIDs were still getting standardized), we had a requirement that Issuer Profiles had to be resolvable via https for information such as public key, revocation lists, and even metadata such as name & image to be gathered when verifying a certificate. 

DIDs give us the capability to do this in a decentralized way (note: some DIDs are not very decentralized or suggested due to having different properties, no VC/DID spec has many requirements around some of these properties, but one can consult the DID rubric for further information [TODO link]). 

The Verifiable Credential spec does not require that VCs are issued using DIDs, so it's proposed that we do not make this requirement as well. We may want to continue supporting URL based issuer profiles as well, though we might need to make some changes to support specific key links. 


### Issuer Profile as a DID

There are a few things we may need outside of a normal DID resolution to provide the same UX we have today in Blockcerts V2.

Here's an example of a DID when resolved: 

```json
{
  "@context": "https://www.w3.org/2019/did/v1",
  "id": "did:example:123456789abcdefghi",
  "authentication": [{
    // used to authenticate as did:...fghi
    "id": "did:example:123456789abcdefghi#keys-1",
    "type": "RsaVerificationKey2018",
    "controller": "did:example:123456789abcdefghi",
    "publicKeyPem": "-----BEGIN PUBLIC KEY...END PUBLIC KEY-----\r\n"
  }],
  "service": [{
    // used to retrieve Verifiable Credentials associated with the DID
    "id":"did:example:123456789abcdefghi#vcs",
    "type": "VerifiableCredentialService",
    "serviceEndpoint": "https://example.com/vc/"
  }]
}
```

One of the main requirements to verify the integrity of a certificate and proof that a certain issuer did indeed issue it is the `#key` field in the `authentication` property of a DID. 

One would be able to link a signing key by referencing the DID and property: `did:example:123456789abcdefghi#keys-1`. 


However, there are a few other things we need to carry over to a DID profile. 

Name, URL, introductionURL, revocationList, image, & email

I'm proposing a service endpoint for BlockcertsIssuer that contains some of this metadata, as well as a BlockcertsRevocation URL to handle certificate revocations. 

#### BlockcertsIssuerService

```json
"service": [{
  "id": "did:example:123456789abcdefghi#BlockcertsIssuer",
  "type": "BlockcertsIssuerService",
  "name": "University of Example,
  "URL", "https://example.com", 
  "imageURL": "https://example.com/img.png", //some DIDs may have size limitations
  "email": "test@example.com",
  "serviceEndpoint": "https://example.com/introductionURL" // in place of introductionURL
}]
```

When resolving the issuer DID `did:example:123456789abcdefghi`, we can then look for types that related to `BlockcertsIssuerService` to check for metadata and allow recipients to post their own DIDs/public keys to the issuer, much like we do today for URL based Issuer Profiles.


#### BlockcertsRevocationService


**Option 1**

```json
"service": [{
  "id": "did:example:123456789abcdefghi#BlockcertsRevocation",
  "type": "BlockcertsRevocationService",
  "serviceEndpoint": "https://example.com/revocationEndpoint"
}]
```

If an issuer wants the ability to revoke any of their issued certificates, they can add `BlockcertsRevocationService` to their list of DID services. 

This will allow a Blockcerts verifier to check the revocation status of a certificate by making a `GET` call to `https://example.com/revocationEndpoint/{certId}`. 


**Option 2**

An alternative method of making this `BlockcertsRevocationService` would be to make it a `BlockcertsRevocationListService` instead, similar to how we do `revocationList` today.  

```json
"service": [{
  "id": "did:example:123456789abcdefghi#BlockcertsRevocationList",
  "type": "BlockcertsRevocationListService",
  "serviceEndpoint": "https://example.com/revocationListEndpoint"
}]
```

There are pros and cons to both. 

Option 1 allows a verifier to only obtain and see the revocation status of a single certificate. A verifier would not be able to see the revocation status of certificates in which they do not have possession of. A standard practice of making UUID-based certificate IDs should prohibit verifiers from guessing another certificate ID. 

However, option 1 allows the issuer to see, log, monitor (etc.) against a specific certificate. They would be able to see what IP address, origin, etc. was trying to verify a specific individual's certificate and then infer certain things. 

Since option 2 is pulling an entire list of revocation events, it is not revealed to the issuer who is getting verified, but it does reveal to verifiers every revocation event they have ever made and why. In the case of a large revocation list, the verifier may have to wait for all of the revocations to get processed and retrieved. 


There has not been a very good consensus yet on what method of revocation/status lists should be used for Verifiable Credentials, and thus no standards yet. Ideally, there is a generic `RevocationServiceEndpoint` not specific to Blockcerts revocation lists, but to not conflict with other methods that might be created, I'm suggesting we label this as a Blockcerts-specific revocation endpoint. 

Instead of the Blockcerts standard picking one of these two methods, we may support both and allow issuers to decide for themselves which makes better sense for their organization. 


#### Example

Here is an example of what an issuer DID might look like when resolved, picking option 2 as an example: 

```json
{
  "@context": "https://www.w3.org/2019/did/v1",
  "id": "did:example:123456789abcdefghi",
  "authentication": [{
    "id": "did:example:123456789abcdefghi#keys-1",
    "type": "RsaVerificationKey2018",
    "controller": "did:example:123456789abcdefghi",
    "publicKeyPem": "-----BEGIN PUBLIC KEY...END PUBLIC KEY-----\r\n"
  }],
  "service": [{
    "id": "did:example:123456789abcdefghi#BlockcertsIssuer",
    "type": "BlockcertsIssuerService",
    "name": "University of Example,
    "URL", "https://example.com", 
    "imageURL": "https://example.com/img.png",
    "email": "test@example.com",
    "serviceEndpoint": "https://example.com/introductionURL"
  }, {
    "id": "did:example:123456789abcdefghi#BlockcertsRevocationList",
    "type": "BlockcertsRevocationListService",
    "serviceEndpoint": "https://example.com/revocationListEndpoint"
  }]
}
```


### Issuer Profile as a URL in V3

Here is an example of an Issuer Profile in Blockcerts v2: 

```json
{
  "@context": [
    "https://w3id.org/openbadges/v2",
    "https://w3id.org/blockcerts/v2"
  ],
  "type": "Profile",
  "id": "https://www.blockcerts.org/samples/2.0/issuer-testnet.json",
  "name": "University of Learning",
  "url": "https://www.issuer.org",
  "introductionURL": "https://www.issuer.org/intro/",
  "publicKey": [
    {
      "id": "ecdsa-koblitz-pubkey:msBCHdwaQ7N2ypBYupkp6uNxtr9Pg76imj",
      "created": "2017-06-29T14:48:03.814936+00:00"
    }
  ],
  "revocationList": "https://www.blockcerts.org/samples/2.0/revocation-list-testnet.json",
  "image": "data:image/png;base64,iVBORw0KGgo...",
  "email": "contact@issuer.org"
}
```

Comparing that to the example issuer DID above, the only thing needed to change is mapping `publicKeys` to `authentication`. 


```json
{
  "@context": [
    "https://w3id.org/openbadges/v2",
    "https://w3id.org/blockcerts/v2"
  ],
  "type": "Profile",
  "id": "https://www.blockcerts.org/samples/2.0/issuer-testnet.json",
  "name": "University of Learning",
  "url": "https://www.issuer.org",
  "introductionURL": "https://www.issuer.org/intro/",
  "authentication": [{
    "id": "https://www.blockcerts.org/samples/2.0/issuer-testnet.json#keys-1",
    "type": "RsaVerificationKey2018",
    "controller": "https://www.blockcerts.org/samples/2.0/issuer-testnet.json",
    "publicKeyPem": "-----BEGIN PUBLIC KEY...END PUBLIC KEY-----\r\n"
  }],
  "revocationList": "https://www.blockcerts.org/samples/2.0/revocation-list-testnet.json",
  "image": "data:image/png;base64,iVBORw0KGgo...",
  "email": "contact@issuer.org"
}
```

This will allow us to link directly to a specific key used for signing a Verifiable Credential, which is a standard way of finding the key, instead of in the current Blockcerts model of checking the blockchain issuing key against all public keys that an issuer has claimed ownership of.


## Summary

The current Blockcerts v2 standard and the Verifiable Credentials standard has a lot of similarities that easily map to each other in many ways. Blockcerts can achieve much of the same functionality and more by utilizing the Verifiable Credential standard instead of being an Open Badge Extension. There are many options for how to map specific properties, but in the end Blockchain Proofs, Issuer Profiles/Identities, Recipient Ownership, and the aspects of life-long credentials are better supported/standardized. From here, we incredibly value community feedback and support.  


## Out of scope
### VC methods 
#### may be subject
 - Subjectivity w/ certain methods (such as alumniOf - what does that mean)
 - Methods should have well-defined definitions and standards

#### Possible Service/Tooling to parse a BC V2 to create a BC V3
Allowing ease of recipients of Blockcerts V2 to now receives a BC v3.
