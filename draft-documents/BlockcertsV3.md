# Blockcerts V3.0

[Anthony Ronning](aronning@learningmachine.com) (Learning Machine), [Wong Wai Chung](waichung@nextid.com) (NextID)

## Abstract

As the standards around verifiable credentials are starting to take form, different flavours of ‘verifiable credentials-like` data structures need to make necessary changes in order to leverage on the rulesets outlined and constantly reviewed by a knowledgeable community like RWOT and W3C. The purpose of this paper is to identify all of the changes needed to comply with the Verifiable Credentials & Decentralized Identifiers standards. 

## VC Schema & Examples
The verifiable credentials is a data schema that is defined and published as a Proposed Recommendation to W3C. It seeks to represent the same information that a physical credential represents that are also tamper-evident and more trustworthy while also addressing future considerations in our societies that are becoming increasingly digitalised. Some of these concerns include but are not limited to privacy preserving goals.

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

Currently Blockcerts is an Extension to Open Badges, which is a specification and open technical standard originally developed by the Mozilla Foundation [https://openbadges.org/]. Open Badges is widely adopted by Universities and Microcredential plateforms as a way to issue acheivements and allows recipients to hold and collect into "backpacks". 

An example standard Open Badge can be seen below:

```
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

It can be seperated into 3 parts, the assertion, the badge, and the issuer. 


Assertion

```
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

```
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

```
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

```
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
        "type": "BTCOpReturn"
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

Besides some of the minor differences in layout/metadata between the example Blockcerts and example Open Badge, the main differences in schema (ie, the blockcerts extensions), are below.

RecipientProfile (https://www.blockcerts.org/schema/2.0/recipientSchema.json)

```
"recipientProfile": {
    "type": [
      "RecipientProfile",
      "Extension"
    ],
    "publicKey": "ecdsa-koblitz-pubkey:mtr98kany9G1XYNU74pRnfBQmaCg2FZLmc",
    "name": "Eularia Landroth"
  }
```

This allows for additional recipient information that can be used to make a string claim of ownership over the credential. In additional to the `name` and `publicKey` properties in this example, there is an `id` field in this schema that is reserved for future uses of DIDs. 


Verification (https://github.com/IMSGlobal/cert-schema/blob/master/docs/open_badge_v2_extensions.md)

```
"verification": {
    "publicKey": "ecdsa-koblitz-pubkey:msBCHdwaQ7N2ypBYupkp6uNxtr9Pg76imj",
    "type": [
      "MerkleProofVerification2017",
      "Extension"
    ]
  }
```

In this case, Verification is an Open Badge `VerificationObject` with a `MerkleProofVerification2017` extension to allow for the `publicKey` of the issuer. It is used during the verification step of a Blockcerts to ensure that the issuer public key matches the public key creating the blockchain transaction with this credential.

One of the last major differences is `Signature` with the MerkleProof2017 extension

Signature (https://www.blockcerts.org/schema/2.0/merkleProof2017Schema.json)

```
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
	    "type": "BTCOpReturn"
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

In this property, we go through all of the merkle proof's required to validate a hash against a merkle root hash on a blockchain. For more information on this procedure, visit the spec (https://w3c-dvcg.github.io/lds-merkleproof2017/).



TODO talk about issuer profile verification and the differences between OB & BC. This may be a prereq for understanding the DIDs section of this paper when we get there.


More information about the exact schema being used for blockcerts can be found here (https://www.blockcerts.org/schema/2.0/context.json) & general information here (https://github.com/blockchain-certificates/cert-schema/blob/master/docs/schema-2.md).


## Comparison
Comparison between BC v2 and VC

## Blockcerts as VC Implementation

TODO Badge specific claims as a VC

Focusing in on the Blockcerts specific additions to Open Badges (`recipientProfile`, `verification`, and `signature`) we can make the following mappings over to a VC.

### `recipientProfile`
This part could essentially go away and be replaced with `credentialSubject.id` and `credentialSubject.name`

```
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

```
  "credentialSubject": {
    "id": "ecdsa-koblitz-pubkey:mtr98kany9G1XYNU74pRnfBQmaCg2FZLmc", // can use DID instead too
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

It may seem as though we could get away with putting the `verification` public key in the issuer DID instead, but, depending on the DID method, that could be changed. For Blockcerts issued to a blockchain, we should continue to leave `verification` inside the document to verify its immutibility. 

### `signature`

Verifiable Credentials require a `proof` property that is used for verifying the immutibliity of a VC as well as proving that a certain issuer is the one that signed the VC. Before VC, Blockcerts used `signature` to prove immutibility. What role does `signature` provide if we are already required to implement `proof`? 

One important property that `proof` does not provide alone is the aspect of time stamping. A `created` date can be applied to `proof`, but since that can be created with any date, we cannot prove it existed at a certain time. 

Using a blockchain can be benefitial here, as it proves that the document existed with a high degree of certainty at the time of the transaction (collisions techically can still occur due to hashing, though highly unlikely). 

I am proposing that we make `signature` optional for those that do not wish to take advantage of time stamping with a blockchain. Without `signature`, we can still verify integrity with `proof`. 


It may be possible to create a new `proof` type that supports the structure/purpose defined in `signature` here.

### Additional Fields

#### `display`

In Blockcerts V2, it is not part of the standard, but we've been building a lot of support for `displayHtml` unofficially. In mobile wallets, verifiers, etc. As well as 3rd party libraries building for it as well. 

Proposing for V3, it would be great if we can throw in official support for displays. Extending past `displayHtml`, we should allow support for any type of display. Some may not want to use `html` but instead use `pdf`, an `image`, etc. 


For the schema, it can simply be `type` and `data` properties.

Example:

```
"display": {
	"type": "html",
	"data": "<p>hello world</p>"
	}
```

#### `metadata`

Similar to the above `display`/`displayHtml` section, we similarily do not have an official standard around the use of the `metadatajson` property we have. We have unofficial support in both the mobile app & verifier to display some metadata information to the viewer. 

Proposing for V3, if we could add this to the standard, but allow for different types of metadata format, maybe `XSD` for example, it would allow issuers to take advantage of that more, and continue to support it officially in some of the Blockcerts ecosystem. 

Could be similar to `display`, adding `type` & `data`. 

```
"metadata": {
	"type": "json",
	"data": "{\"test\": true"
}
```




## DID Implementations
 - Issuer vs Recipient
 - Make DID meaningful (ties back to recipient/issuer and make use of DID for verification)
 - Possibilities for service endpoints for DIDs

## VC methods 
### may be subject
 - Talk about the subjectivity w/ certain methods (such as alumniOf - what does that really mean)
 - Methods should have well defined definitions and standards

### Possible to create a method that looks similar to the Blockcerts/OpenBadge BadgeClass object.

### Possible Service/Tooling to parse a BC V2 to create a BC V3