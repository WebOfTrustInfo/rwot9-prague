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

* [RWOT Primer](./rwot-primer.md) — How the design workshop works
* [DID Primer](./did-primer.md) — Decentralized Identifiers ([extended version](./did-primer-extended.md) also available)
* [Functional Identity Primer](./functional-identity-primer.md) — A different way to look at identity
* [Verifiable Credentials Primer](./verifiable-credentials-primer.md) — the project formerly known as Verifiable Claims
* [Glossary of Terms](./glossary-primer.md) — a brief dictionary of technical terms used at RWOT

## Topical Listing

### ActivityPub

* [Decentralizing Reputation with DID](./Decentralizing-Reputation-with-DID.md)
  * by [Adrian Gropper](http://healthurl.com)
  * "To scale decentralized commerce based on self-sovereign identity and decentralized identifiers we will need to provide a practical alternative to centralized reputation managers. Decentralization is a complex topic and the rubrics that will help formalize our community's approach to decentralization is work that’s just beginning. One way to evaluate decentralization is the absence of essential intermediaries in an otherwise peer-to-peer transaction by self-sovereign peers. A decentralized reputation solution must provide context, a negligible increase in transaction costs, and high resistance to gaming by either the peers to a transaction or their competitors."
  * #did #activitypub #fediverse #wot
  
* [Gently introducing DIDs to the Mastodon/ActivityPub Fediverse](./fediverse-did-integration.md)
  * by [Michael Pimmer](http://michael.pimmer.info/about/), [Paul Fuxjaeger](https://twitter.com/fuxjaeger), [Markus Sabadello](https://danubetech.com/about.html)
  * "Our goal is to bring self sovereign identity concepts to the current ActivityPub fediverse as soon and as securely as possible."
  * #did #activitypub #fediverse #wot
  
* [Keeping Unwanted Messages off the Fediverse](./ap-unwanted-messages.md)
  * By [Serge Wroclawski](http://blog.emacsen.net) with advice and ideas by [Christopher Lemmer Webber](https://dustycloud.org)
  * "A collection of techniques to keep unwanted messages (spam, phishing, hate speech) off the Fediverse, with a focus on OCAP and WoT.
  * #activitypub #spam #wot #ocap
  
### DIDs

* [DID Communication and Interoperability](./did-communication-and-interop.md)
  * By [Daniel Bluhm](mailto:daniel.bluhm@sovrin.org)
  * An overview of the need to achieve interoperability between SSI Stacks and how DID Communication can help.
  * #did #didcomm

* [DID Resolution collected diagrams](./did-resolution-collected-diagrams.md)
  * By [Markus Sabadello](https://danubetech.com/)
  * "This is a collection of the diagrams that have been used so far to illustrate various key topics of DID Resolution."
  * #did

* [DID Snail Method Specification](./didm-snail.md)
  * By [Amy Guy](https://rhiaro.co.uk/), Yancy Ribbens, Dmitri Zagidulin
  * Mapping DID-related concepts onto offline scenarios as an educational tool OR a silly waste of time for all involved: you decide.
  * #did #methods #education #inclusivity #outreach
  
* [DID Spec Current Status](./did-spec-current-status.md)
  * By [Amy Guy](https://rhiaro.co.uk/)
  * Summary of current issues and ongoing discussions on the DID Specification.
  * #did
  
* [Rubrics for Decentralization of DID Methods Creative Brief](./rubrics.md)
  * By [Joe Andrieu](mailto:joe@legreq.com), [Amy G](mailto:amy@rhiaro.co.uk), [Joachim Lohkamp](mailto:joachim@jolocom.com), [=Drummond Reed](mailto:drummond.reed@evernym.com), [Markus Sabadello](mailto:markus@danubetech.com), [Oliver Terbu](mailto:oliver.terbu@consensys.net), [Kai Wagner](mailto:kai@jolocom.com)
  * "The Rubrics for Decentralization of DID Methods document (the Document) will help people evaluate real or potential DID Methods. This document outlines the collaborative aspirations of the Document’s editors."
  * #did #rubrics #decentralization

* [A "Supreme Court" for Decentralization and Interoperability?](./topics-and-advance-readings/Supreme%20Court%20for%20decent%20and%20interop.md)
  * by [Juan Caballero](mailto:juan@sourcecheck.org)
  * "Should someone be rating or coordinating the testing of interoperability between resolvers and platforms? Maybe that same set of people (ideally, paid for this service) would be in a good position to "apply" the rubric for eco-system internal guidance until/unless a more definitive certification forms?"
  * #did #rubrics #interoperability #decentralization

* [X.509 DID Method - Decentralising PKI starting with a X.509 DID method](./X.509-DID-Method.md)
  * By [Bas Kaptijn - discipl.org](https://discipl.org), [Steven Gort - discipl.org](https://discipl.org), [Dr. Carsten Stöcker - spherity.com](https://spherity.com)
  * This paper proposes a X.509 DID (sub)method
  * #did #decentralization #pki #X.509
  
_See also Identity, Self-sovereign_

### DID/Verifiable Claim Infrastructure

* [Infrastructure for persistently live DIDs & Claims](./infrastructure-for-persistently-live-dids.md)
  * By [James Foley](https://github.com/realisation)
  * This paper considers limitations and liabilities of DID infrastructure and suggests a protocol as a solution
  * #did #decentralization 

  
### Identity

* [Bare minimum agent for identity](./Bare-minimum-agent.md)
  * by Snorre Lothar von Gohren Edwin
  * "First we want to discuss what the bare minimum specifications that an identity app needs to provide value? How can an identity be represented physically? What are the pros and cons of a combination of these situations. The second issue is to discuss how to enable an ecosystem, what is needed to get other startups with their own non did solutions in play. Is it SDKs, libraries, proxys, some kind of shared infrastructure?"
  * #identity #ecosystem #minimization
  
* [Building Blocks for Sovereign P2P Identity](./building-blocks-sovereign-p2p-identity.md)
  * by Arthur Brock, Joel Ulahanna, and Philip Beadle
  * "We present a collection of tools designed to perform as a complete foundation for distributed applications enable a fully distributed, peer-to-peer identity. These tools are integrated into an open-source, cryptographic, data integrity framework called Holochain, without promoting the Holochain Foundation into any elevated status of authority as an identity provider. Instead, the tools are specifically designed to enable the emergence of an ecosystem of providers leveraging the tools as a foundation for their services."
  * #identity #p2p #holochain

* [Decentralized Identity as a Meta Platform](./Decentralized-Identity-Meta-platform.md)
   * by Samuel Smith
   * "The purpose of this paper is to foster awareness of the economic benefits of cooperation and the crucial role decentralized identity may play in unleashing historic new sources of value creation and transfer."
   * #cooperation #did

* [Decentralized unique anonymous identity](./decentralized-unique-anonymous-identity.md)
   * by Andrew Edi
   * "The talk presents a novel way to create decentralized anonymous identity, that does not require any personally identifying information to be verified. The humanness and uniqueness is proven by running a collective simultaneous online Turing test."
   * #identity #DID #anonymity
   
* [Why we must ask the Why of Identity](./ask-why.md)
  * by Ian Grigg 
  * "When I formulated the 4 schools or types of identity (state, self, corporate, community), I was not thinking of inclusion, I was expressly intending to exclude"
  * #identity #definitions
  
* [Decentralized unique identity via graph-based Sybil-detection on a peer-to-peer credit network](./Decentralized-unique-identity-via-graph-based-Sybil-detection-on-a-peer-to-peer-credit-network.md)
  * by Aleeza Howitt 
  * "It should be possible to analyze the connectivity of members in a p2p credit network, and from this to determine which members are real and which are Sybils (fake or duplicate accounts)."
  * #identity #p2p #credit
  
### Identity, Self-sovereign

* [A Business Framework for SSI in IoT](./business-framework-for-ssi-in-iot.md)
  * by Michael Shea and Michael Corning
  * An approach to identify and surface the business needs and concerns to create a business case to support addition of SSI to IoT devices.
  * #ssiniot #businessofssi #iot #ssi
  
* [Formal protocol verification for SSI](./formal_verification_for_ssi.md)
   * by hammanns
   * "Protocol verification models different agents and the messages they can send over a network. In particular, symbolic protocol verification in the Dolev-Yao network attacker model assumes that the attacker controls the network, i.e., the attacker can read, send, block, and modify messages, but cannot break cryptography (i.e., cryptography is assumed to be perfect). The goal is to detect logical errors in the protocol design that can lead to attacks on desired security properties (such as the secrecy and integrity of messages)."
   * #protocol #verification #did
_See also DIDs_

### Key Management

* [KERI for a Universal DKMI](./KERI-Universal-DKMI.md)
   * by Samuel Smith
   * "The Key Event Receipt Infrastructure (KERI) provides a minimally sufficient means for managing signing authority and tracking events for a crypto-graphic key-pair based decentralized identifier such as a W3C DID. This includes inception, rotation, interaction, and delegation. It includes single and multi-signature schemes. ... A more in depth technical description of KERI is provided here."
   * #KERI #DKMI #did #dad
   
* [Publicly verifiable split-key schemes for hybrid secret sharing and multi-sig authorization](./verifiable-secret-sharing.md)
  * by Mark Friedenbach and Christopher Allen
  * When using the same underlying group, Shamir secret sharing and compact threshold multi-signature schemes are two sides of the same coin. By exploiting this fact we can create publicly verifiable secret sharing schemes for social key recovery which permit dual-use as threshold multi-signature authorization schemes.
  * #shamirsecretsharing #sss #keymanagement #keyrecovery #vss #multisig

* [Zion Key Management APIs and Social Key Recovery](./zion-sdks-skr.md)
  * by Hank Chiu, Hankuan Yu, David Chen and Jon Tsai
  * Zion Key Management SDK Sets provide rich sets of APIs to help developers to use keys which is protected in Secure Enclave.
  * #shamirsecretsharing #sss #keymanagement #keyrecovery
  
### Mandates and Delegation

* [Mandates and Delegation](./mandates-and-delegation.md) (Rieks Joosten)
  * The paper aims to inventory how mandates and delegations are used in practice. From that, we want to derive a conceptual, generic (mental) model that we can use to discuss any issues and ultimately transform that in useful, standardizable artefacts that allow embedding and using mandates in VCs.
  * #mandates #delegation #law #VC

### OpenCerts

* [Decentralising Opencerts](./rwot9-prague/blob/master/topics-and-advance-readings/Decentralising%20OpenCerts%20v2.md)
   * by Bill Claxton and Wong Wai Chung
   * "In March 2018, Singapore's can-do government introduced the OpenCerts solution for issuing academic certificates linked to the Ethereum public blockchain.  We believe that the code and schema provided by OpenCerts can be the foundation of a verifiable digital credentials issuance mechanism.  But several changes have to be made in the implementation, to make it more decentralised and reach adoption at scale."
   * #privacy #identity #verifiability #centralisation #singapore #opencerts
   
### Secure Storage
  
* [Datashards: secure storage primitives for the web](./datashards-rationale.md)
   * By [Christopher Lemmer Webber](https://dustycloud.org/), with help from [Serge Wroclawski](https://emacsen.net/@emacsen) and [Tom Marble](http://info9.net/wiki/tmarble/)
   * "Over the last year we have been working on a general mechanism for URIs representing private, encrypted storage that can live in a variety of locations.  We call this system 'Datashards'."
   * #storage #datashards #cas

* [Secure Data Hubs: Encrypted Storage for the Web](./secure-data-hubs.md)
   * by Manu Sporny, Dave Longley, and Amy Guy
   * "The Secure Data Hubs specification describes a privacy-respecting mechanism for storing, mirroring, indexing, sharing, and retrieving encrypted data at a storage provider."

### Security

* [Addressing DID Connection Man in the Middle Attacks](addressing-MITM-attacks.md)
   * By Kyle Den Hartog
   * "There's two options for addressing Man-in-the-middle (MITM) that are created by the Trust On First Use (TOFU) problem: Passing a hash of a key or DID Document through a trusted out of band channel. This is also called fingerprinting; or Adding a key as a self-attested attribute to a credential."
   * #TOFU

* [Preventing Transferrability with ZKP-based Credentials](./zkp-safety.md)
    * By Daniel Hardman and Lovesh Harchandani
    * "Some in the digital credential movement have claimed that ZKP-based credentials are inherently unsafe because they can be shared by a malicious holder. The reasoning is that ZKPs guarantee perfect anonymity, and are therefore transferable by simply sharing the link secret. This is a misunderstanding of how ZKP-based credentials work. In fact, ZKPs can provide the same sorts of transfer protections as any other type of credential."
    * #fraud #credentials #ZKP #zeroknowledgeproofs #privacy

### Standards Working Groups

* [NVC for Standards Working Groups](./nvc.md)
   * "We propose to facilitate the collaborative drafting of a paper that discusses the possible use of non-violent communications (NVC) and cognitive behavioral (CBT) methodologies, to create a collaboration toolkit for Internet standards working groups."
   * by Claire Rumore & Moses Ma
   * #cooperation #communication #standards

### Terminology

* [Terminology Process](./terminology.md) (Rieks Joosten)
  * Many problems exist as we try to 'fix' terminology. At RWoT-9, I propose to have (perhaps hackathon-like) sessions, the purpose of which is to establish a generally useable process for creating and maintaining terminologies, building on earlier experiences in this area at TNO. In order to validate this process, one (perhaps two) actual terminologies should be established. The paper [Terminology for Agent-Hub-Related Identity Concepts](./Terminology%20for%20Agent_Hub-Related%20Identity%20Concepts.pdf) might serve as a starting point for that. 

### Verfiable Credentials

* [Analysis of Verifiable Credential Protocols for Issuer Interactions](./vc_protocols_issuer.md)
  * by Martin Riedel, Daniel Kelleher

* [Combining Verifiable Credentials and Zero Knowledge Proof Systems](./verifiable-credentials-and-zero-knowledge-proof-systems.md)
  * by Yancy Ribbens
  * Anonymous credentials enable a holder (prover) to reveal select information to a verifier during the verification process.  In order to build anonymous credential systems, ZKPs can be combined with Verifiable Credentials to enhance user privacy.  This is a proposal to develop library support for Verifiable Credentials and recommend ZKP formats for different use cases and credential attributes.
  * #verifiable-credentials #ZKP #zeroknowledgeproofs
 
* [Decision Making with Verifiable Credentials](./decision-making-with-verifiable-credentials.md)
  * "The paper will focus on the intersection between verifiable credentials and decision making ... We start by giving an overview of the problem in the context of mortgage lending and then describe a general model of decision making which is reconciled with the verifiable credentials data model. Then discuss the properties of our proposed approach as well as possible implementations."
  * by Edward Curran, Paul Ezhilchelvan, Aad Van Moorsel & Simon Brown (AB)
  * #verifiablecredentials, #decisionmaking, #DMN, #financialservices
  
* [Establishing level of assurance with verifiable credentials and the need for a human centered design exploration](./level-of-assurance-crendtials.md)
  * "In this paper we would like to explore the idea of establishing levels of assurance, which will no longer be tied to single issuance processes, but also to a multi-source verification processes."
  * by Bentley Farrington , Bart Suichies and Víctor Martínez Jurado
  * #verifiable-credentials #assurance #humancentric
  
* [Islands, Tigers, and Bears, Oh My!](./islands.md)
  * by Daniel C. Burnett
  * "Many of the properties in VCs are optional, and of the ones that are mandatory there is often flexibility in how they can be used. It is very likely that credentials written assuming use of JSON-LD for vocabularies and semantics will have semantics that basic JSON processors will ignore. It is likely that VCs using zero knowledge proofs will be unverifiable by processors that do not understand zero knowledge proofs. In short, the syntax is generic enough to support all these options, but it is NOT the case that every VC in existence will be verifiable, or even understandable without verification, by every processor."
  * "This leads to a question that has frequently arisen in the VCWG: what level of interoperability can we expect, and is there a risk of the VC ecosystem devolving into islands of incompatible VCs?"
  * "In short, the answer is yes."
  * #verifiable-credentials #interoperability

* [Verifiable Credential Authentication via OpenID Connect (vc-authn-oidc)](./vc-authn-oidc.md)
  * by Tobias Looker
  * "The aim of this document is to describe how a standard OpenID provider (OP) can be extended to support verifiable credential authentication. With this support, a relying party (RP) is able to request this method of authentication to harness the power of verifiable credentials."
  * #verifiable-credentials #authentication #openid-connect

* [Addition of Proof Request/Response to a formal Verifiable Credentials specification](./verifiable-credentials-proof-request.md)
  * by Jonathan Reynolds, Daniel McGrogan
  * "The W3C Verifiable Credentials specification does not currently outline how credential data should be requested by a Verifier. Our document outlines the approach taken at Workday and proposes it as an addition or companion to the VC spec. At RWoT we wish to present our approach in order to get community feedback and consensus. Workday recently announced our credentialing platform and will shortly begin to issue credentials within our market verticals. We fully intend to support the community standards around credentialing and therefore wish to drive consensus in the community on a simple, standard approach for requesting and sharing VCs between a holder and verifier."
  * #verifiable-credentials #proof-request

### Verifiable Credentials Use Cases

* [Decentralized Identifiers to Enable Trusted Machine Economy](./Decentralized%20Identifiers%20to%20Enable%20Trusted%20Machine%20Economy.md)
   * "Transacting IoT data must be different in many respects in order to build much-needed trust in IoT-enabled Data Marketplaces, trust that will be key to their sustainability. Data generated internally to an organization is usually not enough to remain competitive, improve customer experience, and optimize strategic decision-making. However, there is still no transparent and reliable marketplace for data trading with fair price. Furthermore, the verification of the machines (e.g. sensors) for data collection becomes another crutial issue. As a result, an innovative type of platform with the introduction of distributed legder technology (DLT) has emerged, in order to transform data into profits with better trust basic."
  * #DID
  
 * [DID for ROSCAS](./DID_for_ROSCAS.md)
   * Rotating Savings and Credits Association are a type of Micro finance option. They have played an important role for lower income level group in the developing/emerging economies. While the legislation to regulate them and a formal study of the economic value they add is fairly recent, these have been around for more than 1000 years. Some researchers have also called ROSCAS as poor man’s banker. They provide a win-win situation for both borrowers and people who want to save without intervention of a central authorities like banks. However, the quick good return has often been used as bait for unsuspecting and gullible investors, resulting in very high value financial scandals that has often have political repercussions. In this paper we present the kind of scandals that take place in these schemes and how scaling them up digitally is extremely risky. How Decentralized Identifiers and Verifiable claims along with biometrics on mobile phone can be used to create a trust framework.
   * by Vineet Singh
   * #DID #ROSCAS
   
 * [Ecosystem Bootstrapping via Notary Credentials](./ecosystem-bootstrapping-via-notary-vcs.md)
   * Credentials do not yet factor into any significant public process such as requesting a Schengen visa for the purposes of attending RWoT IX.  The governments and businesses involved can not update their existing processes until there is an existing credential ecosystem resting on the proven ability of the general population to engage digital trust technology.  This paper explores the use of credentials which attest the observation of a primary document by an authority and the non-intrusive pairing of these credentials with existing processes.  This approach establishes the infrastructure required for a strong credential ecosystem without first requiring a global re-engineering of identity management.
   * by Eric Welton
   * #bootstrapping, #verifiablecredentials, #notary

* [SolidVC: A Decentralized Verifiable Credentials Management System](./solid-vc.md)
   * [SolidVC](https://github.com/kezike/solid-vc) is a decentralized Verifiable Credentials platform built with the open protocols of the Web and for the open community that the Web was intended to serve. It enables the unilateral issuance and presentation of credentials by anyone running the software locally, as well as verification of these credentials against an open credential status document. SolidVC is implemented in the context of [Solid](https://solid.inrupt.com), a Web technology developed at MIT in 2016 that allows decentralized applications to interact with personal data on behalf of users in an access controlled environment. In this paper, I discuss the motivation of SolidVC, provide sufficient background of supporting technologies, present my contribution, outline a real use case, and discuss future improvements to the platform.
   * by Kayode Ezike
   * #verifiablecredentials #solid #linkeddata
   
* [Using Verifiable Claims as a Proof of Ownership for Blockcerts](./Using%20Verifiable%20Claims%20as%20a%20Proof%20of%20Ownership%20for%20Blockcerts.md)
   * by Anthony Ronning, Chris Winczewski, Dan Hughes
   * "The proposed method outlined in this paper would be able to use a Verifiable Credential from a recipient to prove ownership of a Blockcert needing verification."
   * #verifiable-credentials #digitial-certificiates #ssi
   
* [Using Verifiable Credentials for German Government Grants](./vcs-for-german-grants.md)
  * This paper describes the potential usage of the SSI framework for the application of government grants. It takes into consideration the current developments from the German government with their "Bundes-chain" initiative. 
  * by Adrian Doerk
  * #verifiable-credentials #ssi #government  

* [Utilizing zero-knowledge proofs and verifiable credentials to provide privacy-friendly income tests for social housing](./zero-knowledge-proofs-and-vc-in-social-housing.md)
   * "This paper explains how we integrated zero knowledge proofs in our issuing and verifying flow of the universal ledger agent. We will this for a pilot this year covering the income test required in social housing."
   * by David Lamers (Rabobank)
   * #ZKP #zeroknowledgeproofs #verifiablecredentials #socialhousing #usecases
   
* [Verifiable Credentials in Incentivized Competency Assessment](./vc-in-incentivized-competency-assessment.md)
   * "We leverage web of trust concept in order to create a network of competencies where Experts (Examiners) act as verifiers to assess user's competency on a given subject. We propose using decentralized staking and slashing mechanism similar to Augur's dispute model in order to create financial incentives for users to minimize fraud in the network. Finally, we propose a design for mechanism that produces verifiable credentials of skills and competencies which do not require centralized assessor or an institution."
   * by Stepan Gershuni (credentia.me)
   * #competency-based-assessment #ssi #decentralized-identifiers #verifiable-credentials #digital-certificates

### Verifiable Data Chains / Decentralised Autonomic Data (DADs)

* [A DID based solution for verifiable data streaming & processing in cyber-physical systems](./A_DID_based_solution_for_data_processing.md)
   * "In this paper we will introduce the concept verifiable data chains and data provenance for industrial applications such as driving event processing, manufacturing value chains in regulated industries and insure AI propositions. We do a deep dive discussion for driving event processing in mobility systems while highlighting the benefits of using DIDs for data provenance in order to increase safety in the mobility system."
   *  by Dr. Carsten Stöcker (Spherity GmbH), Dr. Michael Rüther (Spherity GmbH), Alexander Yenkalow (Spherity GmbH), Juan Caballero (The Purple Tornado)
   * #verifiableclaims #dad #did #provenance
   
### Wallets

* [What's In Your Wallet](./whats-wallet.md)
  * by Christopher Allen and Joe Andrieu
  * "A Universal Identity Wallet (UIW) for digital credentials promises seamless interoperability across issuers and verifiers, and would be usable by people, organizations, and things, for digital transactions both online and off."
  * #wallet #universal-identity
  
### Web of Trust

* [Concerns for minorities in a Web of Trust](./concerns-for-minorities.md)
   * by Marie Axelsson
   * "As we keep building a new web of trust, we need to remember that the needs of marginalized groups are often not heard. It’s easy to talk about access just in terms of disability, and while it is one aspect it’s also important to remember that there are other marginalized groups who are not heard because they are a minority, or they are oppressed in other ways."
   * #web-of-trust #minorities
   
### Web of Trust Alternatives

* [Exploring Interpersonal Data](./exploring-interpersonal-data.md)
   * by Kaliya Young
   * I recently wrote a series with Glen Weyl about Decentralized Social Identity and it got me thinking about interpersonal data and what it looks like relative to decentralized idetnity standards since so much of the focus in our work is centered on getting existing "centralized" institutions to issue decentralized verifiable credentials.
   
* [Firefly Trust Sync](./firefly-trust-sync.md)
   * by Tom Marble
   * "Introducing the Firefly Trust Sync (Firefly) architecture as a decentralized, web-of-trust alternative to address the shortcomings of the Certificate Authority (CA) based Public Key Infrastructure (CA-based PKI) and the Pretty Good Privacy (PGP) web-of-trust. Self sovereign identity is a cornerstone of this architecture and yet it does not rely whatsoever on distributed ledger technology. Essential design elements are presented with initial thoughts on both advantages and disadvantages of this approach as well as some next steps."
   * #firefly #web-of-trust
   
* [Heresay: A Fuzzy Prediction Market for Distributed Reputation](./heresay.md)
  * by AJ Adams, Matt Condon
  * We propose a pattern for distributed, emergent reputation rendered via a fuzzy prediction market. In order to promote scale with resilience, legibility with ephemerality, and transitivity with context, we begin by investigating how identity, trust, and reputation function at intimate scale and under organic constraints.
  * #reputation #web-of-trust #privacy

* [Nodemail Protocol](./nodemail.md)
   * by Ethan Brown
   * Document describing the Nodemail Protocol.
   
* [Reimagining global: Programmable incentivization and its implications for personal governance](./reimagining-global-rwot9.md)
  * by [John R Hoopes IV](https://github.com/robisoniv/)
  * "Ideas for a new conception of global governance. Opt-in mechanisms of incentivization based on the conditional provision or restriction of access to financial or informational assets could provide individuals with an enforceable mechanism of self-regulation, to encourage intentional behavior."
   
* [Reputation Loops](./topics-and-advance-readings/reputation-loops.md)
   * by Matthew Schutte
   * An alternative way to think about generating good enough sense-making and social coordination through agent-centric combinings of correlated information from multiple sources. This is somewhat distinct from the transitive trust model that Web of Trust relies upon, but has similarities as well.
   
* [A Web of Credit Framework](./web-of-credit.md)
   * by Yonatan Sompolinsky and Alexandra Tran
   * "This document is a high-level discussion on using webs of trust for decentralized credit systems."

## Alphabetical Listing

* [Addition of Proof Request/Response to a formal Verifiable Credentials specification](./verifiable-credentials-proof-request.md)
* [Addressing DID Connection Man in the Middle Attacks](addressing-MITM-attacks.md) - Kyle Den Hartog
* [Analysis of Verifiable Credential Protocols for Issuer Interactions](./vc_protocols_issuer.md)
* [Bare minimum agent for identity](./Bare-minimum-agent.md)
* [Building Blocks for Sovereign P2P Identity](./building-blocks-sovereign-p2p-identity.md)
* [A Business Framework for SSI in IoT](business-framework-for-ssi-in-iot.md) - Michael Shea & Michael Corning
* [Combining Verifiable Credentials and Zero Knowledge Proof Systems](./verifiable-credentials-and-zero-knowledge-proof-systems.md)
* [Concerns for minorities in a Web of Trust](./concerns-for-minorities.md)
* [Datashards: secure storage primitives for the web](./datashards-rationale.md)
* [Decentralized Identifiers to Enable Trusted Machine Economy](./Decentralized%20Identifiers%20to%20Enable%20Trusted%20Machine%20Economy.md)
* [Decentralized Identity as a Meta Platform](./Decentralized-Identity-Meta-platform.md)
* [Decentralized unique anonymous identity](./decentralized-unique-anonymous-identity.md)
* [Decentralized unique identity via graph-based Sybil-detection on a peer-to-peer credit network](./Decentralized-unique-identity-via-graph-based-Sybil-detection-on-a-peer-to-peer-credit-network.md)
* [Decentralizing Opencerts](./Decentralising%20OpenCerts%20v2.md)
* [Decentralizing Reputation with DID](./Decentralizing-Reputation-with-DID.md)
* [Decision Making with Verifiable Credentials](./decision-making-with-verifiable-credentials.md)
* [A DID based solution for verifiable data streaming & processing in cyber-physical systems](./A_DID_based_solution_for_data_processing.md) - Carsten Stöcker, Alexander Yenkalow, Juan Caballero
* [DID Communication and Interoperability](./did-communication-and-interop.md)
* [DID_for_ROSCAS](./DID_for_ROSCAS.md)
* [DID Resolution collected diagrams](./did-resolution-collected-diagrams.md)
* [DID Snail Method Specification](./didm-snail.md)
* [DID Spec Current Status](./did-spec-current-status.md)
* [Ecosystem Bootstrapping via Notary Credentials](./ecosystem-bootstrapping-via-notary-vcs.md)
* [Establishing level of assurance with verifiable credentials and the need for a human centered design exploration](./level-of-assurance-crendtials.md)
* [Exploring Interpersonal Data](./exloring-interpersonal-data.md)
* [Firefly Trust Sync](./firefly-trust-sync.md)
* [Formal protocol verification for SSI](./formal_verification_for_ssi.md)
* [Gently introducing DIDs to the Mastodon/ActivityPub Fediverse](./fediverse-did-integration.md)
* [Heresay: A Fuzzy Prediction Market for Distributed Reputation](./heresay.md)
* [Islands, Tigers, and Bears, Oh My!](./islands.md)
* [Infrastructure for persistently live DIDs & Claims](./infrastructure-for-persistently-live-dids.md)
* [Keeping Unwanted Messages off the Fediverse](./ap-unwanted-messages.md)
* [KERI for a Universal DKMI](./KERI-Universal-DKMI.md)
* [Mandates and Delegation](./mandates-and-delegation.md)
* [Nodemail Protocol](./nodemail.md)
* [NVC for Standards Working Groups](./nvc.md) by Claire Rumore & Moses Ma
* [Preventing Transferability with ZKP-based Credentials](./zkp-safety.md)
* [Reputation Loops](./reputation-loops.md)
* [Rubrics for Decentralization of DID Methods Creative Brief](./rubrics.md)
* [Reimagining global: Programmable incentivization and its implications for personal governance](./reimagining-global-rwot9.md)
* [Secure Data Hubs: Encrypted Storage for the Web](./secure-data-hubs.md)
* [A "Supreme Court" for Decentralization and Interoperability?](./topics-and-advance-readings/Supreme%20Court%20for%20decent%20and%20interop.md)
* [SolidVC: A Decentralized Verifiable Credentials Management System](./solid-vc.md)
* [Terminology Process](./terminology.md)
* [Using Verifiable Claims as a Proof of Ownership for Blockcerts](./Using%20Verifiable%20Claims%20as%20a%20Proof%20of%20Ownership%20for%20Blockcerts.md)
* [Using Verifiable Credentials for German Government Grants](./vcs-for-german-grants.md)
* [Utilizing zero-knowledge proofs and verifiable credentials to provide privacy-friendly income tests for social housing](./zero-knowledge-proofs-and-vc-in-social-housing.md)
* [Verifiable Credential Authentication via OpenID Connect (vc-authn-oidc)](./vc-authn-oidc.md)
* [Verifiable Credentials in Incentivized Competency Assessment](./vc-in-incentivized-competency-assessment.md)
* [Publicly verifiable split-key schemes for hybrid secret sharing and multi-sig authorization](./verifiable-secret-sharing.md)
* [A Web of Credit Framework](./web-of-credit.md)
* [What's In Your Wallet](./whats-wallet.md)
* [Why we must ask the Why of Identity](./ask-why.md)
* [X.509 DID Method - Decentralising PKI starting with a X.509 DID method](./X.509-DID-Method.md)
* [Zion Key Management APIs and Social Key Recovery](./zion-sdks-skr.md)
