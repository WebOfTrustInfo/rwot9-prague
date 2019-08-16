# Using Verifiable Claims as a Proof of Ownership for Blockcerts

## Contributors
Anthony Ronning (aronning@learningmachine.com), Chris Winczewski (cwinczewski@learningmachine.com), Dan Hughes (dhughes@learningmachine.com)

## Abstract

When Blockcerts first came into existence in 2016, technologies such as Verifiable Credentials and Decentralized Identifiers were still in they're infancy. Blockcerts went in sort of a staging state first, as an extension to Open Badges. With the current model, there is not an implementation for proving recipient ownership of issued Blockcerts. While the work to begin moving Blockcerts to a [Verifiable Credential will commence soon](https://www.learningmachine.com/future-proof), there may still be a need to prove ownership for pre-vc Blockcerts (Blockcerts V2). The proposed method outlined below would be able to use a Verifiable Credential from a recipient to prove ownership of a Blockcert needing verification. 


## Structure of a Blockcerts

The structure of a V2 Blockcerts is similar in nature to a Verifiable Credential today. See [Open Badges are Verifiable Credentials](https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/open-badges-are-verifiable-credentials.md). 

```js
{
  "@context": [
    "https://w3id.org/openbadges/v2",
    "https://w3id.org/blockcerts/v2",
    ...
  ],
  "type": "Assertion",
  "id": "urn:uuid:0063b428-9f2d-5d04-a7e5-6b82c0d4853b",
  "recipient": {
    "type": "email",
    "identity": "email@email.com",
    "hashed": false
  },
  "recipientProfile": {
    "type": [
      "RecipientProfile",
      "Extension"
    ],
    "name": "Testing Test",
    "publicKey": "ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH"
  },
  "badge": {
    "type": "BadgeClass",
    "id": "urn:uuid:6c9989c5-3548-54be-be34-1427c15c4881",
    "name": "Name",
    "description": "description",
    "image": "..."
    "criteria": {},
    "issuer": {
      "type": "Profile",
      "id": "https://test.com/issuer.json",
      "name": "Test",
      "url": "https://test.com",
      "image": "..."
      "email": "test@test.com",
      "revocationList": "https://test.com/revocation.json"
    },
    "signatureLines": [
      {
        "type": [
          "SignatureLine",
          "Extension"
        ],
        "jobTitle": "Job Title",
        "image": "..."
      }
    ]
  },
  "verification": {
    "type": [
      "MerkleProofVerification2017",
      "Extension"
    ],
    "publicKey": "ecdsa-koblitz-pubkey:1AwdUWQzJgfDDjeKtpPzMfYMHejFBrxZfo"
  },
  "issuedOn": "2019-07-30T17:53:20.277+00:00",
  "metadataJson": "....",
  "displayHtml": "..."
  "nonce": "87035d70-44e5-4e79-ad71-34e71f3184e6",
  "universalIdentifier": "0063b428-9f2d-5d04-a7e5-6b82c0d4853b",
  "signature": {
    "type": [
      "MerkleProof2017",
      "Extension"
    ],
    "merkleRoot": "123a67b97f1df64e25db03c40ad746d2cf27827695b714f423ff4ae988506a77",
    "targetHash": "8b53d4317b32a909ea6aeb709c3d49828770906305fc3a878719a54919021db9",
    "proof": [
      {
        "right": "8b53d4317b32a909ea6aeb709c3d49828770906305fc3a878719a54919021db9"
      },
      ...
    ],
    "anchors": [
      {
        "sourceId": "2378076e8e140012814e98a2b2cb1af07ec760b239c1d6d93ba54d658a010ecd",
        "type": "BTCOpReturn",
        "chain": "bitcoinMainnet"
      }
    ]
  }
}
```


The important parts that are relevant for this method are the `ID` and `recipientProfile`. 

```js
	"id": "urn:uuid:0063b428-9f2d-5d04-a7e5-6b82c0d4853b",
	"recipientProfile": {
	"type": [
	  "RecipientProfile",
	  "Extension"
	],
	"name": "Testing Test",
	"publicKey": "ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH"
	}
```

## Structure of a Signed Verifiable Credential
This is an example of a [BTCR](https://w3c-ccg.github.io/didm-btcr/) Signed Verifiable Credential that came out of some of the work from the [BTCR Hackathon 2019](https://github.com/WebOfTrustInfo/btcr-hackathon-2019)

```js
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "urn:web-of-trust:context"
  ],
  "id": "urn:uuid:4f66661a-d387-446e-bb73-34c8fe603b1a",
  "type": [
    "VerifiableCredential",
    "WoTRelationshipCredential"
  ],
  "issuer": "did:btcr:xg35-jzrx-qtyt-jqr",
  "issuanceDate": "2010-01-01T19:23:24Z",
  "credentialSubject": {
    "id": "did:btcr:xg35-jzrx-qtyt-jqr",
    "knows": {
      "id": "did:btcr:8jal-lzzq-qqqq-69f7-ac",
      "publicKey": {
        "id": "did:btcr:8jal-lzzq-qqqq-69f7-ac#satoshi",
        "type": "EcdsaSecp256k1VerificationKey2019",
        "publicKeyBase58": "Pnq3wLmbvyHqXWrV36kdfKfaq1hu7itBMdWrGWXgr53RF"
      }
    }
  },
  "proof": {
    "type": "EcdsaSecp256k1Signature2019",
    "created": "2019-08-14T00:46:05Z",
    "jws": "eyJhbGciOiJFUzI1NksiLCJiNjQiOmZhbHNlLCJjcml0IjpbImI2NCJdfQ..MEYCIQCTh7tmCnOQfUGLaX60x1kJ-9Y9rhPG1EKfgGaR7CR9qAIhAJ4Wzz8-D3PXMH4SW3HWPiH5yjmoidlz_lHyVQB2zRS4",
    "proofPurpose": "assertionMethod",
    "verificationMethod": "did:btcr:xg35-jzrx-qtyt-jqr#satoshi"
  }
}
```

The main parts of the VC here are as follows: 

- `issuer`: Entity creating/signing the credential

- `credentialSubject`: the `type` of credential and the properties that make up the credential - this will vary with each type of `credentialSubject`

- `proof`: The signed proof of the rest of the credential, as a `jws`. 


## Proving Ownership

Using the Blockcerts [mobile app](https://www.blockcerts.org/), a recipient can transmit their public key to their issuer for the issuer to include it in their Blockcert. We have been doing this from the beginning due to the importance of self-sovereign ownership of records, even if the capabilities to prove it was not present yet. 


### Constructing Challenge

First, we need to present a "challenge" for the recipient to answer and sign with their private key. This can take for in the same structure that we expect the `credentialSubject` claim to look like.

```js
  "credentialSubject": {
    "id": "ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH",
    "challenge": "urn:uuid:9940edfa-acd0-4ee1-aa15-f37a9aabca0b"
    "ownership": {
      "id": "urn:uuid:0063b428-9f2d-5d04-a7e5-6b82c0d4853b"
    }
  }
```

In this scenario, it says that `credentialSubject.id` (referring to the `recipientProfile.publicKey` in the Blockcerts file) owns the document with `id` matching the `id` of the Blockcert.

We need to add `challenge` as a random `uuid` to be sure that the recipient has not signed a similar claim before and the entity in question is not transmitting an already signed VC that they gained access to. The challenger needs to keep track of `challenge` to be sure that the signed VC has the same value once returned by the recipient. 


### Constructing Ownership Verifiable Credential

Once the recipient has received the challenge, they need to create a VC with the challenge information and then sign it. 

```js
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "urn:web-of-trust:context"
  ],
  "id": "urn:uuid:7e1f58a8-9cd9-42c7-a0cd-4b0836531e49",
  "type": [
    "VerifiableCredential",
  ],
  "issuer": "ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH",
  "issuanceDate": "2010-01-01T19:23:24Z",
  "credentialSubject": {
    "id": "ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH",
    "challenge": "urn:uuid:9940edfa-acd0-4ee1-aa15-f37a9aabca0b"
    "ownership": {
      "id": "urn:uuid:0063b428-9f2d-5d04-a7e5-6b82c0d4853b"
    }
  },
  "proof": {
    "type": "EcdsaKoblitzSignature2016",
    "created": "2019-08-14T00:46:05Z",
    "jws": "{jws}", // this would be replaced by the actual signed jws of this credential
    "proofPurpose": "assertionMethod",
    "verificationMethod": "ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH#key" // we will construct/resolve #key in the next step
  }
}
```


### Proving Verifiable Credential Owns Blockcerts 

Once the verifier has the signed VC above, it may now verify its signature, check the "answer" to the challenge, and verify the `credentialSubject.ownership.id` matches the `id` in the Blockcerts file.

#### Resolve the recipient

Since we only have a recipient public key, we need to be able to resolve it a verifiable credential capable document. 

`ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH`: 

```js
{
  '@context': 'https://w3id.org/did/v0.11',
  id: 'ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH',
  publicKey: [
    {
      id: 'ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH#key',
      controller: 'ecdsa-koblitz-pubkey:1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH',
      type: 'EcdsaKoblitzSignature2016',
      publicKey: '1QBiZ94RQ5iyGW2m8TDoaEmKohQzAjVWkH'
    }
  ],
  authentication: ['#key'],
  assertionMethod: ['#key']
}
```

Now we can use the above doc to verify the `proof` of the signed VC. Any verifier library that can handle `EcdsaKoblitzSignature2016` should be able to verify the signed VC. 

#### Compare Challenge

If the signed VC verifies successfully, then check `credentialSubject.challenge` to ensure it matches what we sent the recipient. 

```js
"credentialSubject": {
    "challenge": "urn:uuid:9940edfa-acd0-4ee1-aa15-f37a9aabca0b"
  }
```

#### Compare Correct Ownership

If the signed vc verifies and has the correct challenge, check the verifiable credential is referencing the Blockcert in question. 

From VC:

```js
  "credentialSubject": {
    "ownership": {
      "id": "urn:uuid:0063b428-9f2d-5d04-a7e5-6b82c0d4853b"
    }
  }
```

From Blockcert:

```js
  "id": "urn:uuid:0063b428-9f2d-5d04-a7e5-6b82c0d4853b"
```

---

If all checks out, then we have just verified ownership!


## Constraints/Assumptions Made

- `ecdsa-koblitz-pubkey` as a resolvable value that confroms to a vc capable document
- Not sure if `ownership` is already a formalized `credentialSubject` type and/or it's capable of doing this already.
- Assumes a mechanism/secure channel in place for verifier and subject is in place. 



## Summary

For Blockcerts (and any other immutable credential where recipient public keys are gathered), we can leverage the Verifiable Credential standard to form/verify claims of ownership for existing credentials. Verifiers can challenge recipients on the ownership of the credential even if the credential in question is not currently a Verifiable Credential type. Recipients are then able to answer the challenge by signing a Verifiable Credential that shows ownership, and ideally, any universal Verifiable Credential verifier can prove. 