# A Rubric for Decentralization of DID Methods

By Joe Andrieu [*joe@legreq.com*](mailto:joe@legreq.com) , Shannon
Appelcline shannona@skotos.net, Amy Guy amy@rhiaro.co.uk, Joachim
Lohkamp [*joachim@jolocom.com*](mailto:joachim@jolocom.com), Drummond
Reed [*drummond.reed@evernym.com*](mailto:drummond.reed@evernym.com),
Markus Sabadello
[*markus@danubetech.com*](mailto:markus@danubetech.com), Oliver Terbu
[*oliver.terbu@consensys.net*](mailto:oliver.terbu@consensys.net), and
Kai Wagner [*kai@jolocom.com*](mailto:kai@jolocom.com)

## Abstract

The communities behind Decentralized Identifiers (DIDs) bring together a
diverse group of contributors, who have decidedly different notions of
exactly what “decentralization” means. For some, the notion of a DID
anchored to DNS is anathema, for others, DIDs that cannot be publicly
verified are problematic. This debate about decentralization is a
continuation of a similar, ongoing argument in cryptocurrency circles:
the question of whether or not bitcoin or ethereum is more decentralized
is a nearly endless source of argument. Rather than attempting to
resolve this potentially unresolvable question, we propose a rubric —
which is a scoring guide used to evaluate performance, a product, or a
project — that teaches how to evaluate a given DID method according to
one’s own requirements. Our goal is to develop a guide that minimizes
judgment and bias. Rather than advocating particular solutions, the
rubric presents a series of criteria which an evaluator can apply to any
DID method based on their particular use cases. We also avoid reducing
the evaluation to a single number because the criteria tend to be
multidimensional and many of the options are not necessarily good or
bad: it is the obligation of the evaluator to understand how each
response in each criteria might illuminate favorable or unfavorable
consequences for their needs. Finally, this rubric allows evaluating
aspects of decentralization of a DID method, but it is not exhaustive,
and does not cover other issues that may affect selection or adoption of
a particular method, such as privacy or efficiency.

## Introduction

## Background

What is a rubric

-   Criteria

-   Options

-   Responses

Four Types of Options

1.  Yes or No question

2.  Spectrum -- The possible answers are points along a spectrum.
    > Evaluation is choosing the closest point for each Method.

3.  List

4.  Multiple choice(?)

Some criteria, applied to some DID Methods, will be N/A (not
applicable).

[]{#_bj528l751jab .anchor}​How to apply this Rubric

Evaluate the criteria that matters to you against a given DID Method.

If a Method offers variability (in the response to a criterion), then
evaluate each variant. For example, did:ethr supports Ethereum mainnet
and multiple testnets, e.g., rinkeby. To fully apply a criterion to
did:ethr, you will evaluate it against all the variations that matter to
you. This applies to Level 2 Networks that can operate on multiple Level
1 Networks as well as DID Methods that directly offer support for
multiple underlying registries.

The examples in this document evaluate each DID Method as it is now.

Timing: An evaluation should be noted with the date at which it
occurred. Any response to a given criteria may change over time.

[]{#_e7mlowxqs9s6 .anchor}​The Criteria

​1​ Rulemaking
==============

\[TODO: The Network and Registry Governance sections (1.1+1.2) are
older. Sections 1.3-1.6 were then written as expanded forms for the
Method Governance. You need to decide whether to break up 1.1 and 1.2 in
a similar way to 1.3 to 1.6; or fully subsume sections 1.1 and 1.2 into
the sections 1.3-1.6 and evaluate each based on all three criteria:
Network, Registry, and Method. In either way, there’s a discrepancy
right now between 1.1, 1.2, and the 1.3-1.6 -SA\]

​1.1​ Network Governance (spectrum)
-----------------------------------

How open is the governance of the DID network?

A.  Anyone can participate in an open, fair process

B.  Governance is restricted to a selected group, using open processes

C.  Governance is restricted to a selected group, without transparency

D.  Governance is ill-defined, leaving participation to an uncertain
    > group

### ​1.1.1​ Relevance

Governance of a DID network determines how the rules of the underlying
network evolve. The more confidence the evaluator has that the
governance represents the interests of DID controllers, the more
confidence the evaluator can have that the network will remain stable,
available, and resistance to attack or censorship.

### ​1.1.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  did:peer:   n/a              did:peer has no intrinsic network. It can use any communications channel between parties.
  did:git:    C                The git “network” is the git source code, which is controlled (currently) by 16 people. They do not have a public issues process.
  did:btcr:   D                Changes to the bitcoin protocol are chaotic and uncertain. They use BIPs, but the path to adoption is uncertain and the relative power of developers, miners, and users is open to debate.
  did:sov::   B                The Sovrin Foundation has an open transparent community governance model but not yet have open elections of trustees.
  did:ethr:   B                Ethereum evolves through EIPs, which can be proposed by anyone, discussed by “the community” and someone decides
  did:jolo:   B                Jolo’s network is Ethereum.

​1.2​ Registry Governance (spectrum)
------------------------------------

How open is the governance of the DID registry?

A.  Anyone can participate in an open, fair process

B.  Governance is restricted to a selected group, using open processes

C.  Governance is restricted to a selected group, without transparency

D.  Governance is ill-defined, leaving participation to an uncertain
    > group

### ​1.2.1​ Relevance

Governance of a DID registry determines the business rules of CRUD
operations for the method, which are ultimately recorded on the network.
The more confidence the evaluator has that the governance represents the
interests of evaluator, the more confidence the evaluator can have that
the registry will remain stable, available, and resistance to attack or
censorship.

### ​1.2.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- ------------------------------------------------------------------------------------------------------------------------------------------------
  did:peer:   B                Rules for accepting changes to the business rules are bilaterally negotiated between the peers, subject to conformance with the specification.
  did:git:    C                The controllers of the git repo are a limited set, but their decisions are “meatspace protocol” and hence not explicitly transparent.
  did:btcr:   D                The registry for BTCR is the network, which has uncertain governance.
  did:sov::   B                The Sovrin Foundation has an open transparent community governance model but not yet have open elections of trustees.
  did:ethr:   A                This classification applies to mainnet
  did:jolo:   A                

​1.3​ Breadth of Authority
--------------------------

How open is the governance authority?

-   Specification is governed by a single entity.

-   Specification is governed by a closed set of multiple parties.

-   Specification is governed by an open set of multiple parties.

### ​1.3.1​ Relevance

Is the governing authority for the DID method innately centralized? Is
the method governed by a single entity, who could make arbitrary changes
to the governance? Or is it governed by a closed set of parties, without
fully open access?

### ​1.3.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- -------
  did:peer:                    
  did:git:                     
  did:btcr:                    
  did:sov::                    
  did:ethr:                    
  did:jolo:                    

​1.4​ Privatization
-------------------

How privatized is the economic interest of the governing authority?

-   The governing authority is established to extract rents from the DID
    > method (Libra)

-   The governing authority is established to enhance profits for a
    > limited set of parties (USB, CDMA, etc)

-   The governing authority is established for the common good of a
    > limited set of parties (InCommon)

-   The governing authority is established for the public good (BTCR)

### ​1.4.1​ Relevance

The underlying goals of a DID method may affect the centralization of
the method. If the goal of a method is to enhance or support a certain
group, then there may be centralization focused on that group and their
interests.

### ​1.4.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- -------
  did:peer:                    
  did:git:                     
  did:btcr:                    
  did:sov::                    
  did:ethr:                    
  did:jolo:                    

1.5​ Governance Openness
------------------------

How open is the governance of the DID method specification? (cribbage)

-   Commentary is open.

-   Decision making is formal.

-   Decision making is open.

-   Process is transparent.

### ​1.5.1​ Relevance

The centralization of the governance can be impacted by the openness of
the rule making. Open commentary allows anyone to at least offer input.
A formal decision making allows for well-described and well-understood
rule making that anyone can participate in. Open decision making means
that anyone can participate in the collective choice (whether it be
voting, rough consensus, or something else). Finally, a transparent
process means that anyone can see and understand how the collective
choice was made.

### ​1.5.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- ----------------------------
  did:peer:   TBD              ☐☒☐☐☒ \[NONE ENTERED YET\]
  did:git:    TBD              ☐☐☒☐☒
  did:btcr:   TBD              ☐☒☐☐☒
  did:sov::   TBD              ☐☒☐☐☒
  did:ethr:   TBD              ☐☒☐☐☒
  did:jolo:   TBD              ☐☒☐☐☒

​1.6​ Governance Cost
---------------------

How expensive is it to participate in governance (in time, money, or
effort)? (spectrum)

-   Free to all

-   Inexpensive, but accessible

-   Modest cost for interested parties

-   Expensive and restricted

### ​1.6.1​ Relevance

Governance of a DID method specification determines who makes the
decisions about a given method specification. DID operations map to the
registry. In a perfect world, Method specifications would be correct and
never change. In practice, someone usually has the formal or de facto
authority to update the Method spec.

### ​1.6.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- --------------------------------------------------------------------------------------------------------------
  did:peer:                    
  did:git:                     
  did:btcr:                    
  did:sov::                    
  did:ethr:                    
  did:jolo:                    Jolocom makes the decisions, but it is driven by customers and partners. Highly informal, open, transparent.

​1.7​ Specification Maturity
----------------------------

How long has the specification been published?

1.  Just a concept sketch

2.  A complete draft...

3.  ...

4.  …

5.  Published as a fixed, recommended specification

6.  \[Published for X years\]

​1.8​ Organizational Maturity
-----------------------------

How mature is the entity who controls the specification

​1.9​ Scope of Usage
--------------------

How widely can DIDs of this method be used?

-   Central: DIDs can only be created and used with a single,
    > centralized party.

-   Paired: DID can be created and used pairwise, between any two
    > parties.

-   Contextual: DIDs can be created and used contextually, between any
    > set of collaborating parties.

-   Universal: DIDs can only be created and usable universally, between
    > any number of parties.

### ​1.9.1​ Relevance

Different methods enable different scopes in which a DID might be
considered usable or valid. For example, peer DIDs are only usable
between the two peers who share unique DIDs with each other; other
parties are unable to resolve the DID, find the DID Document, and use
its information to establish secure interactions. In contrast, BTCR
records all DIDs on a public ledger, meaning that all DIDs are
fundamentally accessible to any party who might receive the DID.
Contextual DIDs are a middle ground that allow a set of parties to use
DIDs, while those outside that group cannot meaningfully do so. Finally,
central DIDs use the DID syntax and DID Documents to establish secure
communications, but authority to use these DIDs resides with the central
party, who may revoke that ability at their discretion.

### ​1.9.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- -------
  did:peer:   Paired           
  did:git:    Contextual       
  did:btcr:   Universal        
  did:sov:    Universal        
  did:ethr:   Universal        
  did:jolo:   Universal        

​1.10​ Auditability
-------------------

Can you retrieve cryptographic proof of the history of changes to a
given DID Document?

### ​1.10.1​ Relevance

Trustlessness is a prerequisite of a decentralized system. If you HAVE
TO trust the source of a DID Document (i.e., if you can’t verify
cryptographically a DID Document that is returned from resolution), then
you are at the mercy of a potentially centralized authority.

### ​1.10.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- --------------------------------------------------------------------------------------------------------------
  did:peer:   no               did:peer relies on the authority of the peer, without auditability of changes
  did:git:    yes              did:git uses signed commits to maintain integrity of current DID Documents
  did:btcr:   yes              did:btcr maintains its history of changes in linked transactions on the blockchain
  did:sov:    yes              did:sov records all transitions on ledger
  did:ethr:   yes              did:ethr uses an event log of all operations performed on each DID
  did:jolo:   yes              did:jolo starts with a transaction on ledger, then uses an event log of all operations performed on each DID

​2​ Operation
=============

​2.1​ Permissioned Operation (spectrum)
---------------------------------------

To use the DID method, do you need permission?

> Anyone can participate fully (full read/write and participation in
> consensus)
>
> Anyone can read/write, consensus mechanism is permissioned
>
> Anyone can read, writing and consensus is permissioned
>
> All participation is permissioned

### ​2.1.1​ Relevance

Permissioned operation impacts the availability of the network to
various participants, which can affect inclusivity with regard to
underserved or vulnerable populations. Permissioned networks also expose
the permission giver to legal or other attack.

### ​2.1.2​ Examples

  Method            Classification      Notes
  ----------------- ------------------- ------------------------------------------------------------------------------------------------
  did:peer:         1.1                 Anyone can participate fully, you just need a peer.
  did:git:          1.2                 Anyone can participate fully, consensus is managed by meat-space protocol on a per repo basis.
  did:btcr:         1.1                 
  did:sov:          1.3 moving to 1.2   Moving from Permissioned Write Access to Public Write Access
  did:ethr:         1.1                 This classification applies to mainnet
  did:jolo:         1.1                 
  did:jolo:...:x:                       Rubric should be evaluated based on the additional constraints of sub-network X

​2.2​ Financial accountability (spectrum)
-----------------------------------------

How transparent and fair are the economics of the method?

> ​All operational finances are transparent and accounted for
>
> ​Compensation for primary operators is transparent
>
> ​Some financial flows are visible
>
> ​Operation is privatized with no visibility

### ​2.2.1​ Relevance

Similar to Governance (\#3), financial accountability reflects the
integrity and sustainability of the DID registry. The more open,
transparent, and accountable the system, the greater the conference a
DID controller may have that it will remain stable and operational, and
therefore continue to provide service.

### ​2.2.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- ----------------------------------------
  did:peer:   N/A              
  did:git:    N/A              
  did:btcr:   3.1              
  did:sov::   3.1              
  did:ethr:   3.1              This classification applies to mainnet
  did:jolo:   3.1              

​2.3​ Interoperability (pick the most applicable) 
--------------------------------------------------

Does the DID method restrict access or functionality to particular
wallet implementations?

> Any wallet can work with any resolver on any registry
>
> Any wallet can work with multiple resolvers and multiple registries
>
> Some implementations of a wallets can work with some resolvers
>
> There is a single combined suite of resolver, registry, and wallet

### ​2.3.1​ Relevance

The ability to communicate with different (ideally all) resolvers and
registries significantly increases the applicability of a decentralized
identity layer / usability of a given wallet. Vice versa limited
capability to work with other methods and registries restrict usage.

### ​2.3.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------
  did:peer:   TBD              
  did:git:    TBD              
  did:btcr:   TBD              
  did:sov::   TBD              
  did:ethr:   4.0.1            Registries can be anchored on any EVM-compatible blockchain. The DID contains a discriminator which indicates where the corresponding registry is anchored.
  did:jolo:   4.0.2            Registries can be anchored on any EVM-compatible blockchain. (no discriminator yet)

​2.4​ Operational Maturity
--------------------------

How long has the specification been in live usage?

\[some thing like this, about if it’s in live usage or not and for how
long\]

1.  Just a concept sketch

2.  A complete draft...

3.  ...

4.  …

5.  Published as a fixed, recommended specification

​2.5​ Wallet Code Base (pick the most applicable)
-------------------------------------------------

How decentralized is the wallet code base?

> There are multiple, independently funded, interoperable Wallet
> implementations in different languages on different operating systems
> on different hardware.
>
> There are multiple interoperable open source Wallet implementations in
> different languages
>
> ​There is an open source Wallet code base
>
> There is a single, closed source binary Wallet for a single operating
> system on a single hardware platform

### ​2.5.1​ Relevance

Typically, wallets control the seed, keys, or in general cryptographic
material used to proof control of a DID. It is important to ensure
long-term sustainability, reliability and avoid vendor lock-in of the
wallet code base to prevent the identity loss. As a DID is often
associated with verifiable credentials (except ZKP-based verifiable
credentials), this rubric becomes even more sensitive.

### ​2.5.2​ Examples

  Method      Classification      Notes
  ----------- ------------------- ----------------------------------------
  did:peer:   TBD                 
  did:git:    TBD                 
  did:btcr:   TBD                 
  did:sov::   5.0.1               
  did:ethr:   5.0.1               This classification applies to mainnet
  did:jolo:   ### ​2.5.3​ 5.0.3   

​2.6​ Resolver Code Base (pick the most applicable)
---------------------------------------------------

How decentralized is the resolver code base?

> ​There are multiple, independently funded, interoperable Resolver
> implementations in different languages on different operating systems
> on different hardware.
>
> ​There are multiple interoperable open source Resolver implementations
> in different languages
>
> ​There is an open source code base for a Resolver
>
> There is a single, closed source binary Resolver

==

WE HAVE THIS ADDITIONAL QUESTION

> Is trusted resolution possible with limited resources (e.g. on mobile
> devices) without relying on authoritative intermediaries (e.g.
> blockchain explorer APIs)?

==

### ​2.6.1​ Relevance

This rubric is similar to Wallet Code Base. Additionally, this rubric
describes the impact on the DID controller’s communication partners and
their ability to verify the proof of control of that DID, as well as to
obtain the DID controller’s service endpoints to engage with the DID
controller in another context.

### ​2.6.2​ Examples

  Method      Classification   Notes
  ----------- ---------------- ----------------------------------------
  did:peer:   TBD              
  did:git:    TBD              
  did:btcr:   TBD              
  did:sov::   TBD              
  did:ethr:   6.0.1            This classification applies to mainnet
  did:jolo:   6.0.3            

​3​ Enforcement
===============

Are the rules being enforced?

How do you know that the rules are being enforced?

[]{#_vfxcbsn24350 .anchor}​Conclusion

[]{#_sethcaid7gb .anchor}​Appendix A - Terminology

**Evaluator** - The individual or organization applying a DID Method
rubric to evaluate a DID Method

**Network** - the underlying “L1” network that enables communication and
recording of transactions, .e.g, for BTCR, any of the main bitcoin
networks can be used (mainnet, testnet, etc.). For did:ethr, the network
is any EVM-compliant network (each DID specifies one and only one such
network)..

**Registry** - the instantiated business logic that allows DID
operations that are ultimately recorded on the network. In did:ethr, the
registry is a smart contract. In did:btcr, the registry is the specific
bitcoin network (the network and the registry is the same)..
