#  Topics & Advance Readings

In advance of the design workshop, all participants produced a one-or-two page topic paper to be shared with the other attendees on either:

* A specific problem that they wanted to solve with a web-of-trust solution, and why current solutions (PGP or CA-based PKI) can't address the problem?
* A specific solution related to the web-of-trust that you'd like others to use or contribute to?

If you will be attending Rebooting the Web of Trust Fall 2019 in Prague, the Czech Republic, please upload your topic papers and advanced readings to this directory with a pull request.

## Pull Request Submission

To add a paper, create a pull request to this repo with your contribution (preferably as an .md file, but if you can't, as a PDF), along with updates to the README.md in this folder. Please also include a byline with contact information in the paper itself.

Please also enter your paper _twice_ in this README file, once in the topical listing (adding a new category describing your topic, if necessary) and one in the alphabetical listing. Please be sure to include the full URL for your paper in the README, so that we can copy it to the main page URL and have it still correctly link.

If you don't know how to submit a pull request, please instead submit an issue.

## Primer Listing

These primers overview major topics which are likely to be discussed
at the design workshop. If you read nothing else, read these. (But
really, read as much as you can!)

* [DID Primer](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/did-primer.md) — Decentralized Identifiers ([extended version](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/did-primer-extended.md) also available)
* [Functional Identity Primer](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/functional-identity-primer.md) — A different way to look at identity
* [Verifiable Credentials Primer](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/verifiable-credentials-primer.md) — the project formerly known as Verifiable Claims
* [Glossary of Terms](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/glossary-primer.md) — a brief dictionary of technical terms used at RWOT

## Topical Listing

### ActivityPub / Spam

* [Keeping Unwanted Messages off the Fediverse](./ap-unwanted-messages.md)
  * By [Serge Wroclawski](http://blog.emacsen.net) with advice and ideas by [Christopher Lemmer Webber](https://dustycloud.org)
  * "A collection of techniques to keep unwanted messages (spam, phishing, hate speech) off the Fediverse, with a focus on OCAP and WoT.
  * #activitypub #spam #wot #ocap
  
### DIDs

* [DID Resolution collected diagrams](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/did-resolution-collected-diagrams.md)
  * By [Markus Sabadello](https://danubetech.com/)
  * "This is a collection of the diagrams that have been used so far to illustrate various key topics of DID Resolution."
  * #did

* [Rubrics for Decentralization of DID Methods Creative Brief](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/rubrics.md)
  * By [Joe Andrieu](mailto:joe@legreq.com), [Amy G](mailto:amy@rhiaro.co.uk), [Joachim Lohkamp](mailto:joachim@jolocom.com), [=Drummond Reed](mailto:drummond.reed@evernym.com), [Markus Sabadello](mailto:markus@danubetech.com), [Oliver Terbu](mailto:oliver.terbu@consensys.net), [Kai Wagner](mailto:kai@jolocom.com)
  * "The Rubrics for Decentralization of DID Methods document (the Document) will help people evaluate real or potential DID Methods. This document outlines the collaborative aspirations of the Document’s editors."
  * #did #rubrics #decentralization

### Mandates and Delegation

* [Mandates and Delegation](./mandates-and-delegation.md) (Rieks Joosten)
  * The paper aims to inventory how mandates and delegations are used in practice. From that, we want to derive a conceptual, generic (mental) model that we can use to discuss any issues and ultimately transform that in useful, standardizable artefacts that allow embedding and using mandates in VCs.
  * #mandates #delegation #law #VC

### Secure Storage

* [Combining Verifiable Credentials and Zero Knowledge Proof Systems](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/verifiable-credentials-and-zero-knowledge-proof-systems.md)
  * by Yancy Ribbens
  * Anonymous credentials enable a holder (prover) to reveal select information to a verifier during the verification process.  In order to build anonymous credential systems, ZKPs can be combined with Verifiable Credentials to enhance user privacy.  This is a proposal to develop library support for Verifiable Credentials and recommend ZKP formats for different use cases and credential attributes.

* [Datashards: secure storage primitives for the web](./datashards-rationale.md)
   * By [Christopher Lemmer Webber](https://dustycloud.org/), with help from [Serge Wroclawski](https://emacsen.net/@emacsen) and [Tom Marble](http://info9.net/wiki/tmarble/)
   * "Over the last year we have been working on a general mechanism for URIs representing private, encrypted storage that can live in a variety of locations.  We call this system 'Datashards'."
   * #storage #datashards #cas

* [Decentralising Opencerts](https://github.com/waichung/rwot9-prague/blob/master/topics-and-advance-readings/Decentralising%20OpenCerts%20v2.md)
   * by Bill Claxton and Wong Wai Chung
   * "In March 2018, Singapore's can-do government introduced the OpenCerts solution for issuing academic certificates linked to the Ethereum public blockchain.  We believe that the code and schema provided by OpenCerts can be the foundation of a verifiable digital credentials issuance mechanism.  But several changes have to be made in the implementation, to make it more decentralised and reach adoption at scale."
   * #privacy #identity #verifiability #centralisation #singapore

* [KERI for a Universal DKMI](https://github.com/SmithSamuelM/rwot9-prague/blob/master/topics-and-advance-readings/KERI-Universal-DKMI.md)
   * by Samuel Smith
   * "The Key Event Receipt Infrastructure (KERI) provides a minimally sufficient means for managing signing authority and tracking events for a crypto-graphic key-pair based decentralized identifier such as a W3C DID. This includes inception, rotation, interaction, and delegation. It includes single and multi-signature schemes. ... A more in depth technical description of KERI is provided here."
   * #KERI #DKMI #did #dad

* [Secure Data Hubs: Encrypted Storage for the Web](./secure-data-hubs.md)
   * by Manu Sporny, Dave Longley, and Amy Guy
   * "The Secure Data Hubs specification describes a privacy-respecting mechanism for storing, mirroring, indexing, sharing, and retrieving encrypted data at a storage provider."

### Security

* [Addressing DID Connection Man in the Middle Attacks](addressing-MITM-attacks.md) 
   * By Kyle Den Hartog
   * "There's two options for addressing Man-in-the-middle (MITM) that are created by the Trust On First Use (TOFU) problem: Passing a hash of a key or DID Document through a trusted out of band channel. This is also called fingerprinting; or Adding a key as a self-attested attribute to a credential."
   * #TOFU
   
* [Formal protocol verification for SSI](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/formal_verification_for_ssi.md)
   * by hammanns
   * "Protocol verification models different agents and the messages they can send over a network. In particular, symbolic protocol verification in the Dolev-Yao network attacker model assumes that the attacker controls the network, i.e., the attacker can read, send, block, and modify messages, but cannot break cryptography (i.e., cryptography is assumed to be perfect). The goal is to detect logical errors in the protocol design that can lead to attacks on desired security properties (such as the secrecy and integrity of messages)."
   * #protocol #verification #did
   
* [Preventing Transferrability with ZKP-based Credentials](https://github.com/dhh1128/rwot9-prague/blob/master/topics-and-advance-readings/zkp-safety.md)
    * By Daniel Hardman and Lovesh Harchandani
    * "Some in the digital credential movement have claimed that ZKP-based credentials are inherently unsafe because they can be shared by a malicious holder. The reasoning is that ZKPs guarantee perfect anonymity, and are therefore transferable by simply sharing the link secret. This is a misunderstanding of how ZKP-based credentials work. In fact, ZKPs can provide the same sorts of transfer protections as any other type of credential."
    * #fraud #credentials #zkp #privacy
   
### Standards Working Groups

* [NVC for Standards Working Groups](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/nvc.md) 
   * "We propose to facilitate the collaborative drafting of a paper that discusses the possible use of non-violent communications (NVC) and cognitive behavioral (CBT) methodologies, to create a collaboration toolkit for Internet standards working groups."
   * by Claire Rumore & Moses Ma
   * #cooperation #communication #standards

### Verfiable Credentials
* [Decision Making with Verifiable Credentials](./decision-making-with-verifiable-credentials.md)
  * "The paper will focus on the intersection between verifiable credentials and decision making ... We start by giving an overview of the problem in the context of mortgage lending and then describe a general model of decision making which is reconciled with the verifiable credentials data model. Then discuss the properties of our proposed approach as well as possible implementations." 
  * by Edward Curran, Paul Ezhilchelvan, Aad Van Moorsel & Simon Brown (AB)
  * #verifiablecredentials, #decisionmaking, #DMN, #financialservices
   
### Verifiable Data Chains / Decentralised Autonomic Data (DADs)

* [A DID based solution for verifiable data streaming & processing in cyber-physical systems](./A_DID_based_solution_for_data_processing.md)
   * "In this paper we will introduce the concept verifiable data chains and data provenance for industrial applications such as driving event processing, manufacturing value chains in regulated industries and insure AI propositions. We do a deep dive discussion for driving event processing in mobility systems while highlighting the benefits of using DIDs for data provenance in order to increase safety in the mobility system."
   *  by Dr. Carsten Stöcker (Spherity GmbH), Dr. Michael Rüther (Spherity GmbH), Alexander Yenkalow (Spherity GmbH), Juan Caballero (The Purple Tornado)
   * #verifiableclaims #dad #did #provenance
   
### Verifiable Credentials Use Cases

* [Decentralising Opencerts](https://github.com/waichung/rwot9-prague/blob/master/topics-and-advance-readings/Decentralising%20OpenCerts%20v2.md)
   * "Transacting IoT data must be different in many respects in order to build much-needed trust in IoT-enabled Data Marketplaces, trust that will be key to their sustainability. Data generated internally to an organization is usually not enough to remain competitive, improve customer experience, and optimize strategic decision-making. However, there is still no transparent and reliable marketplace for data trading with fair price. Furthermore, the verification of the machines (e.g. sensors) for data collection becomes another crutial issue. As a result, an innovative type of platform with the introduction of distributed legder technology (DLT) has emerged, in order to transform data into profits with better trust basic."
   
* [Verifiable Credentials in Incentivized Competency Assessment](./vc-in-incentivized-competency-assessment.md)
   * "We leverage web of trust concept in order to create a network of competencies where Experts (Examiners) act as verifiers to assess user's competency on a given subject. We propose using decentralized staking and slashing mechanism similar to Augur's dispute model in order to create financial incentives for users to minimize fraud in the network. Finally, we propose a design for mechanism that produces verifiable credentials of skills and competencies which do not require centralized assessor or an institution."
   * by Stepan Gershuni (credentia.me)
   * #competency-based-assessment #ssi #decentralized-identifiers #verifiable-credentials #digital-certificates

### Web of Trust Alternatives

* [Decentralized Identity as a Meta Platform](https://github.com/SmithSamuelM/rwot9-prague/blob/master/topics-and-advance-readings/Decentralized-Identity-Meta-platform.md)
   * by Samuel Smith
   * "The purpose of this paper is to foster awareness of the economic benefits of cooperation and the crucial role decentralized identity may play in unleashing historic new sources of value creation and transfer."
   * #cooperation #did
   
* [Firefly Trust Sync](./firefly-trust-sync.md)
   * by Tom Marble
   * "Introducing the Firefly Trust Sync (Firefly) architecture as a decentralized, web-of-trust alternative to address the shortcomings of the Certificate Authority (CA) based Public Key Infrastructure (CA-based PKI) and the Pretty Good Privacy (PGP) web-of-trust. Self sovereign identity is a cornerstone of this architecture and yet it does not rely whatsoever on distributed ledger technology. Essential design elements are presented with initial thoughts on both advantages and disadvantages of this approach as well as some next steps."
   * #firefly #web-of-trust
   
## Alphabetical Listing

* [A DID based solution for verifiable data streaming & processing in cyber-physical systems](./A_DID_based_solution_for_data_processing.md) - Carsten Stöcker, Alexander Yenkalow, Juan Caballero
* [Addressing DID Connection Man in the Middle Attacks](addressing-MITM-attacks.md) - Kyle Den Hartog
* [Bare minimum agent for identity](./Bare-minimum-agent.md)
* [Combining Verifiable Credentials and Zero Knowledge Proof Systems](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/verifiable-credentials-and-zero-knowledge-proof-systems.md)
* [Decentralized Identifiers to Enable Trusted Machine Economy](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/Decentralized%20Identifiers%20to%20Enable%20Trusted%20Machine%20Economy.md)
* [Decentralising Opencerts](https://github.com/waichung/rwot9-prague/blob/master/topics-and-advance-readings/Decentralising%20OpenCerts%20v2.md)
* [Decision Making with Verifiable Credentials](./decision-making-with-verifiable-credentials.md)
* [DID Resolution collected diagrams](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/did-resolution-collected-diagrams.md)
* [Firefly Trust Sync](https://github.com/tmarble/rwot9-prague/blob/master/topics-and-advance-readings//firefly-trust-sync.md)
* [Formal protocol verification for SSI](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/formal_verification_for_ssi.md)
* [KERI for a Universal DKMI](https://github.com/SmithSamuelM/rwot9-prague/blob/master/topics-and-advance-readings/KERI-Universal-DKMI.md)
* [Mandates and Delegation](./mandates-and-delegation.md) 
* [NVC for Standards Working Groups](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/nvc.md) by Claire Rumore & Moses Ma
* [Preventing Transferability with ZKP-based Credentials](https://github.com/dhh1128/rwot9-prague/blob/master/topics-and-advance-readings/zkp-safety.md)
* [Rubrics for Decentralization of DID Methods Creative Brief](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/rubrics.md)
* [Secure Data Hubs: Encrypted Storage for the Web](./secure-data-hubs.md)

