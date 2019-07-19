﻿#  Topics & Advance Readings

In advance of the design workshop, all participants produced a one-or-two page topic paper to be shared with the other attendees on either:

* A specific problem that they wanted to solve with a web-of-trust solution, and why current solutions (PGP or CA-based PKI) can't address the problem?
* A specific solution related to the web-of-trust that you'd like others to use or contribute to?

If you will be attending Rebooting the Web of Trust Fall 2019 in Prague, the Czech Republic, please upload your topic papers and advanced readings to this directory with a pull request.

## Pull Request Submission

To add a paper, create a pull request to this repo with your contribution (preferably as an .md file, but if you can't, as a PDF), along with updates to the README.md in this folder. Please also include a byline with contact information in the paper itself.

Please also enter your paper _twice_ in this README file, once in the topical listing (adding a new category describing your topic, if necessary) and one in the alphabetical listing. Please be sure to include the full URL for your paper in the README, so that we can copy it to the main page URL and have it still correctly link.

If you don't know how to submit a pull request, please instead submit an issue.

#### Primers 

These primers overview major topics which are likely to be discussed
at the design workshop. If you read nothing else, read these. (But
really, read as much as you can!)

* [DID Primer](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/did-primer.md) — Decentralized Identifiers ([extended version](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/did-primer-extended.md) also available)
* [Functional Identity Primer](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/functional-identity-primer.md) — A different way to look at identity
* [Verifiable Credentials Primer](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/verifiable-credentials-primer.md) — the project formerly known as Verifiable Claims
* [Glossary of Terms](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/glossary-primer.md) — a brief dictionary of technical terms used at RWOT

## Topical Listing

### Security
[Addressing DID Connection Man in the Middle Attacks](addressing-MITM-attacks.md) - Kyle Den Hartog

### DIDs

* [DID Resolution collected diagrams](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/did-resolution-collected-diagrams.md)
  * By [Markus Sabadello](https://danubetech.com/)
  * "This is a collection of the diagrams that have been used so far to illustrate various key topics of DID Resolution."
  * #did

* [Rubrics for Decentralization of DID Methods Creative Brief](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/rubrics.md)
  * By [Joe Andrieu](mailto:joe@legreq.com), [Amy G](mailto:amy@rhiaro.co.uk), [Joachim Lohkamp](mailto:joachim@jolocom.com), [=Drummond Reed](mailto:drummond.reed@evernym.com), [Markus Sabadello](mailto:markus@danubetech.com), [Oliver Terbu](mailto:oliver.terbu@consensys.net), [Kai Wagner](mailto:kai@jolocom.com)
  * "The Rubrics for Decentralization of DID Methods document (the Document) will help people evaluate real or potential DID Methods. This document outlines the collaborative aspirations of the Document’s editors."
  * #did #rubrics #decentralization

### Secure Storage

* [Datashards: secure storage primitives for the web](./datashards-rationale.md)
* By [Christopher Lemmer Webber](https://dustycloud.org/), with help from [Serge Wroclawski](https://emacsen.net/@emacsen) and [Tom Marble](http://info9.net/wiki/tmarble/)
* "Over the last year we have been working on a general mechanism for URIs representing private, encrypted storage that can live in a variety of locations.  We call this system 'Datashards'."
* #storage #datashards #cas


* [Combining Verifiable Credentials and Zero Knowledge Proof Systems](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/verifiable-credentials-and-zero-knowledge-proof-systems.md)
  * by Yancy Ribbens
  * Anonymous credentials enable a holder (prover) to reveal select information to a verifier during the verification process.  In order to build anonymous credential systems, ZKPs can be combined with Verifiable Credentials to enhance user privacy.  This is a proposal to develop library support for Verifiable Credentials and recommend ZKP formats for different use cases and credential attributes.
* [KERI for a Universal DKMI](https://github.com/SmithSamuelM/rwot9-prague/blob/master/topics-and-advance-readings/KERI-Universal-DKMI.md)
* [Decentralising Opencerts](https://github.com/waichung/rwot9-prague/blob/master/topics-and-advance-readings/Decentralising%20OpenCerts%20v2.md)
  * by Bill Claxton and Wong Wai Chung
  * "In March 2018, Singapore's can-do government introduced the OpenCerts solution for issuing academic certificates linked to the Ethereum public blockchain.  We believe that the code and schema provided by OpenCerts can be the foundation of a verifiable digital credentials issuance mechanism.  But several changes have to be made in the implementation, to make it more decentralised and reach adoption at scale."
  * #privacy #identity #verifiability #centralisation #singapore
* [Secure Data Hubs: Encrypted Storage for the Web](./secure-data-hubs.md)
  * by Manu Sporny, Dave Longley, and Amy Guy
  * "The Secure Data Hubs specification describes a privacy-respecting mechanism for storing, mirroring, indexing, sharing, and retrieving encrypted data at a storage provider."

### ActivityPub / Spam

* [Keeping Unwanted Messages off the Fediverse](./ap-unwanted-messages.md)
  * By [Serge Wroclawski](http://blog.emacsen.net) with advice and ideas by [Christopher Lemmer Webber](https://dustycloud.org)
  * "A collection of techniques to keep unwanted messages (spam, phishing, hate speech) off the Fediverse, with a focus on OCAP and WoT.
  * #activitypub #spam #wot #ocap

### Mandates and Delegation

* [Mandates and Delegation](./mandates-and-delegation.md) (Rieks Joosten)
  * The paper aims to inventory how mandates and delegations are used in practice. From that, we want to derive a conceptual, generic (mental) model that we can use to discuss any issues and ultimately transform that in useful, standardizable artefacts that allow embedding and using mandates in VCs.
  * #mandates #delegation #law #VC


### Verifiable Data Chains / Decentralised Autonomic Data (DADs)

* [A DID based solution for verifiable data streaming & processing in cyber-physical systems] (./A_DID_based_solution_for_data_processing.md)

### Web of trust alternatives

* [Decentralized Identity as a Meta Platform](https://github.com/SmithSamuelM/rwot9-prague/blob/master/topics-and-advance-readings/Decentralized-Identity-Meta-platform.md)
* [Firefly Trust Sync](./firefly-trust-sync.md)

### Security

[Formal protocol verification for SSI](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/formal_verification_for_ssi.md)

## Alphabetical Listing

* [A DID based solution for verifiable data streaming & processing in cyber-physical systems] (./A_DID_based_solution_for_data_processing.md) - Carsten Stöcker, Alexander Yenkalow, Juan Caballero
* [Addressing DID Connection Man in the Middle Attacks](addressing-MITM-attacks.md) - Kyle Den Hartog
* [Bare minimum agent for identity](./Bare-minimum-agent.md)
* [Combining Verifiable Credentials and Zero Knowledge Proof Systems](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/verifiable-credentials-and-zero-knowledge-proof-systems.md)
* [Decentralising Opencerts](https://github.com/waichung/rwot9-prague/blob/master/topics-and-advance-readings/Decentralising%20OpenCerts%20v2.md)
* [DID Resolution collected diagrams](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/did-resolution-collected-diagrams.md)
* [Firefly Trust Sync](https://github.com/tmarble/rwot9-prague/blob/master/topics-and-advance-readings//firefly-trust-sync.md)
* [Formal protocol verification for SSI](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/formal_verification_for_ssi.md)
* [KERI for a Universal DKMI](https://github.com/SmithSamuelM/rwot9-prague/blob/master/topics-and-advance-readings/KERI-Universal-DKMI.md)
* [Mandates and Delegation](./mandates-and-delegation.md) 
* [Rubrics for Decentralization of DID Methods Creative Brief](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/rubrics.md)
* [Secure Data Hubs: Encrypted Storage for the Web](./secure-data-hubs.md)

