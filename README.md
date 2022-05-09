# Rebooting the Web of Trust IX: Prague (September 2019)

This repository contains documents related to RWOT9, the ninth
Rebooting the Web of Trust design workshop, which was held
in Prague, the Czech Republic, September 3rd to 6th, 2019. 

The goal of the workshop is to generate five technical white papers 
and/or proposals on topics decided by the group that would have the 
greatest impact on the future.

Visit [Eventbrite](http://rwot9.eventbrite.com) for more information and to purchase tickets.

## Final Papers

## [*Alice Attempts to Abuse a Verifiable Credential*](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/alice-attempts-abuse-verifiable-credential.pdf) [(Text)](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/alice-attempts-abuse-verifiable-credential.md)
#### by P. Dingle, S. Hammann, D. Hardman, C. Winczewski, S. Smith

> Verifiable credentials (VCs) are an exciting innovation in decentralized identity. By standardizing a data format that allows the holder of a credential to be in control of the receipt and the presentation of digital documents, VCs represent a step forward in data control, while still allowing authoritative information to flow. However, there are reasonable concerns around whether the remote interactions that VCs enable can be secured. A verifiable credential is easy to copy. The cryptographic keys that protect them are easy to share. This makes an old problem from physical credential space more pressing: What mechanisms exist for the system to prevent fraud?

> In this paper, we explore a subset of the fraud problem: vulnerabilities associated with a malicious credential holder. Our frame is a fictional narrative about Alice, a person who receives a prescription as a verifiable credential. Unfortunately, Alice is addicted to the prescribed drug, she is eager to earn quick cash, and she has little respect for legal processes—so she has multiple motives to apply her credential and creativity for mischief.

## [*Blockcerts V3 Proposal*](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/BlockcertsV3.pdf) [(Text)](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/BlockcertsV3.md)
#### by Anthony Ronning & Wong Wai Chung waichung@nextid.com

> As the standards around Verifiable Credentials are starting to take form, different flavors of "verifiable credentials-like" data structures need to make necessary changes to leverage on the rulesets outlined and constantly reviewed by knowledgeable communities such as the W3C. The purpose of this paper is to identify all of the changes needed for Blockcerts to comply with the Verifiable Credentials (VCs) and Decentralized Identifiers (DIDs) standards and to expand upon the additional benefits of using a blockchain in combination with Verifiable Credentials. This paper is meant to act as an explainer in which a formal specification can be created.

> This paper proposes multiple implementation options for several properties. The intention is that we can engage the Blockcerts / Verifiable Credential communities and see what fits best.

## [*Decentralized Identity as a Meta-platform: How Cooperation Beats Aggregation*](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/CooperationBeatsAggregation.pdf) [(Text)](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/CooperationBeatsAggregation.md)
#### by Michael Shea, Samuel M. Smith Ph.D., Carsten Stöcker Ph.D.

> A meta-platform is a platform that enables and fosters participant-controlled value transfer across and among
other platforms and participants; because platforms are a type of network, a meta-platform enables a network
of network efects. This cooperation among platforms may be advantageous in comparison to centralized power
(non-cooperation) in some contexts, particularly where a new network scaling law for meta-platforms can be
argued to apply directly. An open, interoperable, portable, decentralized identity framework is a prime
candidate for becoming such a meta-platform and for leveraging this aggregate network efect.

> Significant momentum has been developing behind a universal decentralized identity system based on open
standards, including the W3C-supported decentralized identifer (DID) and verifable credential (VC) standards. Associated industry groups supporting this open standard include the Decentralized Identity Foundation
(DIF), the Sovrin Foundation, and the HyperLedger Foundation projects Indy, Aries, and Ursa.

> The purpose of this paper is to foster awareness of the economic benefts of cooperation and the crucial role
decentralized identity may play in unleashing new sources of value creation and transfer among cooperating
platforms.

### [*Encrypted Data Vaults*](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/encrypted-data-vaults.pdf) [(Text)](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/encrypted-data-vaults.md)
#### Amy Guy, David Lamers, Tobias Looker, Manu Sporny, Dmitri Zagidulin

> This paper describes current approaches and architectures, derived requirements, design goals, and dangers that implementers should be aware of when implementing data storage. This paper also explores the base assumptions of these sorts of systems such as providing privacy-respecting mechanisms for storing, indexing, and retrieving encrypted data, as well as data portability.

### [*Reputation Interpretation*](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/reputation-interpretation.pdf) [(Text)](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/reputation-interpretation.md)
#### Arthur Brock, Kaliya Hamlin, Grace (Rebecca) Rachmany, Jakub Lanc

> This paper explores how to take a "reputation" trust graph with multiple characteristics and create actionable output. It is not focused on the automation of the process, which could be applied by human processing of information or through a programmed software implementations.

### [*A Rubric for Decentralization of DID Methods*](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/final-documents/decentralization-rubric.pdf)
#### Joe Andrieu (joe@legreq.com), Shannon Appelcline (shannon.appelcine@gmail.com), Amy Guy (amy@rhiaro.co.uk), Joachim Lohkamp (joachim@jolocom.com), Drummond Reed (drummond.reed@evernym.com), Markus Sabadello (markus@danubetech.com), and Oliver Terbu (oliver.terbu@consensys.net)

> The communities behind Decentralized Identifiers (DIDs) bring together a diverse group of contributors
who have decidedly different notions of exactly what “decentralization” means.

> Rather than attempting to resolve this potentially unresolvable question, we propose a rubric — a
scoring guide used to evaluate the performance of a product or a project — that teaches how to evaluate
a given DID Method according to one’s own requirements.

## Topics & Advance Readings

In advance of the design workshop, all participants are invited to contribute a
one-or-two page topic paper to be shared with the other attendees on
either:

   * A specific problem that they wanted to solve with a web-of-trust solution, and why current solutions (PGP or CA-based PKI) can't address the problem?
   * A specific solution related to the web-of-trust that you'd like others to use or contribute to?

Please see the [Topics & Advance Readings directory](topics-and-advance-readings) for all the current papers (and how to upload yours).

## Complete Rebooting the Web of Trust Listing

A different repository is available for each of the Rebooting the Web of Trust design workshops:

* [Rebooting the Web of Trust XI: Netherlands (September 2022)](https://github.com/WebOfTrustInfo/rwot11-netherlands)
* [Rebooting the Web of Trust X: Buenos Aires (March 2020)](https://github.com/WebOfTrustInfo/rwot10-buenosaires)
* [Rebooting the Web of Trust IX: Prague (September 2019)](https://github.com/WebOfTrustInfo/rwot9-prague)
* [Rebooting the Web of Trust VIII: Barcelona (March 2019)](https://github.com/WebOfTrustInfo/rwot8-barcelona)
* [Rebooting the Web of Trust VII: Toronto (September 2018)](https://github.com/WebOfTrustInfo/rwot7-fall2018)
* [Rebooting the Web of Trust VI: Santa Barbara (March 2018)](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-spring2018)
* [Rebooting the Web of Trust V: Boston (October 2017)](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-fall2017)
* [Rebooting the Web of Trust IV: Paris (April 2017)](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-spring2017)
* [Rebooting the Web of Trust III: San Francisco (October 2016)](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-fall2016)
* [Rebooting the Web of Trust II: ID2020 (May 2016)](https://github.com/WebOfTrustInfo/ID2020DesignWorkshop)
* [Rebooting the Web of Trust I: San Francisco (November 2015)](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust)

## License

All of the contents of this directory are licensed [Creative Commons CC-BY](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/master/final-documents/LICENSE-CC-BY-4.0.md) their contributors.
