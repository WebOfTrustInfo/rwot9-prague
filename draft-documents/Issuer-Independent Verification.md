## Rebooting Web of Trust Prague

## Issuer-Independent Verification

Primary Author: Bill Claxton ([NextID](http://nextid.com/), Singapore)
Contributors (Alphabetical Order): Cara Bloom ([MITRE](https://www.mitre.org), USA), Juan Caballero ([Spherity](mailto:juan.caballero@spherity.com), Berlin), Anthony Ronning, ([Learning Machine](https://www.learningmachine.com/), USA) and Wong Wai Chung ([NextID](http://nextid.com/), Singapore).

## Abstract

Independent and, ideally, also universal verification of credentials is a key requirement for trust in Verifiable Credentials and will lead to broader adoption by vendors, issuers, and end-users in different ways.  The challenge is that each vendor is creating their own credential schemas and there are no common methods for cross-vendor/ecosystem verification.  In this paper, we will propose a set of methods by which a vendor can assure issuers that the credentials using the vendor’s chosen schema can be independently verified. 

Ultimately we envision a "universal verifier" which is interoperable with a broad set of credential formats, parallel to (and of course reliant on) the "universal resolver" for DIDs.  The schemas of these different credential formats can be seen as a subset (or implementation of) the Verifiable Credentials data specification.  It should be possible to identify the schema type (sometimes called a "meta-schema") early in a verification process: for instance, knowing whether a credential is academic, medical or financial might be a useful scale at which to specify this, or perhaps more or less granular scales.  With this foundation, vendors will naturally converge on a quick implementation of methods that make their credentials broadly useful.

The system of verification cannot be wholly dependent on end-user critical thinking and analysis, particularly in cases where both credential bearer and credential issuer are unknown or at low trust at time of verification. Nudging and signaling will be an integral part of the credential-passing UX and adoption roadmaps, but for quality checks such as these to eventually develop to support end-user adoption, future reputation and trust systems need to be anchored to “audit trails” of trust.  One way to quickly build these up is by bootstrapping pre-SSI issuer verification systems (such as government-administered identity provider systems and education credentialing), focusing on interoperability and redundancy with more focused systems.  Importantly, implementers with hands-on experience of the OpenCerts schema and BlockCerts standards are represented here in the writing of this document to provide a test-case for interoperability on existing systems.

Link to this paper: [https://tinyurl.com/rwot9openverifier](https://tinyurl.com/rwot9openverifier)
