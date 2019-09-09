**Rebooting Web of Trust Prague**

# **Benefits Of Open Verification For Digital Credentials**

[The original title was Issuer-Independent Verifications]

Primary Author: Bill Claxton ([NextID](http://nextid.com/), Singapore)

Contributors (Alphabetical Order): Cara Bloom ([MITRE](https://www.mitre.org), USA), Juan Caballero ([Spherity](mailto:juan.caballero@spherity.com), Berlin), Rieks Joosten (TNO, Netherlands), Anthony Ronning, ([Learning Machine](https://www.learningmachine.com/), USA) and Wong Wai Chung ([NextID](http://nextid.com/), Singapore)

**Abstract**

Interoperability is an important capability of systems which exchange data.  In the realm of digital identity, a number of vendors are developing and deploying systems which issue computationally verifiable digital credentials to commemorate and act as proof of some set of claims, such as the award of an academic degree.  However these credentials commonly use proprietary data schemas which are not readily verifiable in a consistent manner.  

The authors propose an open verification system (the “Open Verifier”) which could be used to verify any digital credential which complies with the data structure in the W3C Proposed Recommendation for Verifiable Credentials (“PR”). Among the authors of this paper are implementers of two well-known digital credential formats: OpenCerts and BlockCerts.  There is thus a good opportunity for development of a working Open Verifier as an activity to follow the publication of this paper.

**Audience**

This paper will be of interest to those who are developing or deploying digital credential issuance and verification systems which will rely (wholly or in part) on the W3C Proposed Recommendation for Verifiable Credentials.  This includes individuals involved in project, product and process management.  While some knowledge of blockchains and distributed ledgers is presumed, technical knowledge of Verifiable Credentials data structures or process flows is not a prerequisite.

**Background & Nomenclature**

A Verifiable Credential (“VC”) can represent all of the same information that a physical credential represents. The addition of technologies, such as digital signatures, makes verifiable credentials more tamper-evident and more trustworthy than their physical counterparts.  According to the PR, there are 3 crucial elements in every VC: (a) an Issuer, (b) one or more Subjects and (c) one or more claims.  These claims are assertions made about the Subject by the Issuer.

In this paper, we use slightly different terms for the actors.  For example, we describe each Subject as a “Recipient” of their credential, to convey the sense that this credential represents a certificate of achievement conferred on the Subject(s) and no one else. We use the term “Bearer” instead of Holder, however the Bearer should not be presumed to be the owner of the title conferred.  We use the term “Consumer” instead of Verifier to avoid confusion with the software application which performs verification.

<table>
  <tr>
   <td><strong>Role in VC Data Model</strong>
   </td>
   <td><strong>Role in This Paper</strong>
   </td>
   <td><strong>Remarks</strong>
   </td>
  </tr>
  <tr>
   <td>Issuer 
   </td>
   <td>Issuer 
   </td>
   <td>The organisation or entity making a set of claims about a Subject. A single credential must have only one Issuer.
   </td>
  </tr>
  <tr>
   <td>Subject
   </td>
   <td>Recipient
   </td>
   <td>The individual(s) about whom the claims are being made.  A single credential may have more than one Subject / Recipient.
   </td>
  </tr>
  <tr>
   <td>Holder
   </td>
   <td>Bearer
   </td>
   <td>The individual who is presenting the credential to a Consumer, often with the implied representation that they are also the same person as one Subject / Recipient.
   </td>
  </tr>
  <tr>
   <td>Verifier 
   </td>
   <td>Consumer 
   </td>
   <td>An individual who is relying on the credential, typically after programmatically verifying that credential.  The act of relying on a credential, whether verified or not,  is a judgement decision of the Verifier / Consumer.
   </td>
  </tr>
</table>



**Discussion**

Independent and, ideally, also universal verification of credentials is a key requirement for trust in Verifiable Credentials and will lead to broader adoption by vendors, issuers, and end-users in different ways.  The challenge is that each vendor is creating their own credential schemas and there are no common methods for cross-vendor/ecosystem verification.  In this paper, we propose a set of methods by which a vendor can assure issuers that the credentials using the vendor’s chosen schema can be independently verified. 

Ultimately we envision a “universal verifier” which is interoperable with a broad set of credential formats, parallel to (and of course reliant on) the “universal resolver” for DIDs.  The schemas of these different credential formats can be seen as a subset (or implementation of) the Verifiable Credentials data specification.  It should be possible to identify the schema type (sometimes called a “meta-schema”) early in a verification process: for instance, knowing whether a credential is academic, medical or financial might be a useful scale at which to specify this, or perhaps more or less granular scales.  With this foundation, vendors will naturally converge on a quick implementation of methods that make their credentials broadly useful.

The system of verification cannot be wholly dependent on end-user critical thinking and analysis, particularly in cases where both credential bearer and credential issuer are unknown or at low trust at time of verification. Nudging and signaling will be an integral part of the credential-passing UX and adoption roadmaps, but for quality checks such as these to eventually develop to support end-user adoption, future reputation and trust systems need to be anchored to “audit trails” of trust.  One way to quickly build these up is by bootstrapping pre-SSI issuer verification systems (such as government-administered identity provider systems and education credentialing), focusing on interoperability and redundancy with more focused systems.  

**Credential Address Resolution**

The credential itself is a document which is stored somewhere and exchanged via some transport method such as an email attachment.  The Issuer may or may not be responsible for hosting the credential document.  The credential should be accessible by a resolvable URI or CAS address.  

Note, the document may or may not be an encrypted file.  We’ll not comment on the encryption or decryption process in this paper.

Before processing of the credential can occur, the credential must be made accessible to the verifier.  There are two ways to do this.



- Push - the consumer may browse to a physical file or use drag and drop to start the verification process.
- Pull - the consumer may supply a URI or CAS address to retrieve the credential.  This method is also well-suited to transmitted links (eg- the credential is shared via an email).  Note that the link would include both the verification page and the credential address, possibly with other parameters appended.

**Proposed Standard Methods**

We are proposing a set of methods by which any digital credential which is designed to support the PR can be verified.  In other words, we are itemising the functionality of a general purpose verification mechanism.  The authors intend this paper as a scoping document for an open source project, to implement an issuer-independent verification mechanism.



- File structure - The credential must have a schema and the schema must be supported.  If supported, the data structure of the credential must be consistent with the schema.
- Type - The type indicated in the schema is used to inform the consumer as well as to validate the fields in the credential (eg- this is an academic credential, so expects a transcript).
- Trust anchor - The trust anchor is a proof that the credential has not been tampered with.  The verification of a trust anchor can be blockchain and vendor specific, and may not involve a blockchain at all (eg- an RSA signature).  In the non-VC open credential world, the norm is to compare the merkle proof with a merkle root, which allows determination that a credential is tamper free.
- Issuer verification (for each issuer) - The desired outcome is list of verification checks and results, that help to establish that the credential issuer can be trusted.  Some are boolean results (eg- the public key and/or issuer registry matches) and some are metrics (eg- the number of certs issued in past 10 days).  
  - Cert Revocation - Check revocation list to see if Public Key of issuer was valid when cert was issued (Blockcert)
  - Issuer can be confirmed by a DNS check- a DNS record containing an ethereum address pointing to the smart contract governing the data storage (NextCert)
  - (VC)
  - If not part of previous steps, a separate check is done for] Issuer Revocation - If supported, check that the issuer public key is not revoked.
- Recipient verification - The desired outcome is boolean, indicating whether the bearer is able to provide a solution to a challenge hidden within the verifiable credential. 
- Iteration of claims - A simple list of claims.
- Embargo and expiration dates (for each claim) - including a check whether the current time is between the embargo and expiration dates.

<!-- begin Rieks’ contributions -->

[This text may need to be rearranged/moved to other parts (or removed); it’s a braindump.]

Their concern, which is **the problem that this paper addresses**, is that whenever they receive data (within the context of some process), it needs to be decided whether or not that data is valid for use within that process. This ‘validation activity’ is currently mostly manual or, if digital, redundantly so: employees of an organization look at the content that users/customers provide through HTML forms (e.g. to assess that it is complete), they also look at PDFs that have been uploaded (e.g. looking at the logo and signature to guess whether or not its original was genuine), they may consult webservices of authoritative registries (e.g. to verify that data that was provided is in fact consistent with the contents of such registries), and all sorts of other means, everything to reach the decision of whether or not that data can be used in the process for which it was provided.

SSI technologies allow the users/customers to also provide data in a different manner, which we will loosely refer to as ‘verifiable data objects’. Verifiable data objects come in various flavours which go by names as OpenCerts, Verifiable Credentials, OpenID tokens, etc. Verifiable data objects share the property that they have been created (issued) by a specific party (a person or organization), and their contents can say anything about anyone or anything. 

They are called ‘verifiable data objects ’ because they may have characteristics, the existence of which can be established automatically. For example, a verifiable data object may be digitally signed by its issuer, which means that for as long as the digital signature can be verified, we know that the contents of the data object has not changed since it was issued. 

Using SSI technologies in processes is beneficial for all parties involved for several reasons. [Do we want to elaborate on this? I’m thinking about less time needed to gather all data and verify it, and consequently: cheaper validation, process gets data of higher quality, ...?] 

Determining whether or not data that is received is valid for further use is not something that can always be done automatically. In some cases, data obtained from a passport may still be considered value if the passport has not expired for 3, or 6 months. An automated decision that throws out a verifiable data object only because it has (just) expired may be too rigid. On the other hand, a verifiable data object whose signature doesn’t check out may be rejected automatically.

There are various ‘levels’ of validation. A basic level is to establish that a verifiable data object is well-constructed. An example of what this would mean in the physical world is a passport, or a money-bill: they should have all security characteristics that are defined for them, regardless of who it was issued for. Similarly, a verifiable data object should (usually) have a digital signature that checks out.

Another level of validation has to do about the contents. In a passport of some given country, the issuing body should be in (or under the control of) the national government. In a diploma, the grades and courses that are listed must be part of the curriculum of the educational organization that issued the diploma.

Validation may thus go from the basic level to a very detailed level, and the level that is needed differs from one situation to the other. That makes a generic validation mechanism hard to achieve.

<!-- end Reiks’ contributions -->

**Benefits of Open Verification**

[ to be continued... ]

**Architectural Differences between Open-Certificate verification processes and Verifiable Data Object verification processes**

[ to be continued... ]

**Conclusion**

[ to be continued... ]
