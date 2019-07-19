# Firefly Trust Sync

By [Tom Marble](http://info9.net/wiki/tmarble/)

<a id="org85d52ce"></a>

## Abstract

Introducing the Firefly Trust Sync (Firefly) architecture as a
decentralized, web-of-trust alternative to address the shortcomings of
the Certificate Authority (CA) based Public Key Infrastructure
(CA-based PKI) and the Pretty Good Privacy (PGP) web-of-trust.  Self
sovereign identity is a cornerstone of this architecture and yet it
does not rely whatsoever on distributed ledger technology.  Essential
design elements are presented with initial thoughts on both advantages
and disadvantages of this approach as well as some next steps.

1.  [Abstract](#org85d52ce)
2.  [Introduction](#org03225db)
    1.  [Problems](#org447efa5)
    2.  [Goals](#orgb5d2b5d)
3.  [Design](#org2a25b9a)
    1.  [Extending SQRL for peer to peer authentication](#org35a8f30)
    2.  [Bootstrapping with DNS and TLS](#orgf9a0a53)
    3.  [A distributed graph database](#org81e01b9)
    4.  [Anonymity by default](#org8331e55)
    5.  [Optional Pet Names](#org6dec8dd)
    6.  [Onion query obfuscation](#org9d13de0)
4.  [Use Cases](#org3a9e005)
    1.  [Invitation to Firefly](#org5c05a97)
    2.  [Identity linking](#orgc0fbd06)
    3.  [Verify web site certificates](#orgb427007)
    4.  [Verify ssh server fingerprints](#orgbab907b)
    5.  [Send Secure e-mail](#orge749b98)
    6.  [Trust revocation](#org480397d)
5.  [Advantages](#org70d147e)
    1.  [Distributed secure database](#org065424a)
    2.  [Energy conservation](#org3b861d5)
    3.  [There is no cabal](#org9f05148)
    4.  [No key escrow](#org7b046cb)
    5.  [Network tolerant of identity server failures](#org99ef30d)
    6.  [Anti-spam provision](#orge814572)
    7.  [Anonymity by default](#org3dec0c5)
6.  [Disadvantages](#org3e3429f)
    1.  [A server for each identity](#orgb1242c4)
    2.  [UX Challenge](#org8a83364)
7.  [Next Steps](#org782c1b4)
    1.  [Immutability and GDPR Compliance](#orge012047)
    2.  [Open Source Prototype](#org044ef9a)
    3.  [Performance Analysis](#orgecedcf1)
    4.  [Auditing and reproducible builds](#org23757d2)
    5.  [Threat Assessments](#orgc8f517a)
    6.  [Future](#orgda19723)


<a id="org03225db"></a>

# Introduction

The success of the Internet has been based on the independence and
asynchrony of participants growing organically. The Domain Name
Service (DNS<sup><a id="fnr.1" class="footref" href="#fn.1">1</a></sup>) is one of the essential Internet services that
functions as a federation of decentralized servers which has tracked
the growth of the Internet itself. In first wave of e-commerce a
solution was needed for consumers to safely transmit their credit card
information to merchants and that drove the development of Secure
Sockets Layer (SSL) &#x2013; later Transport Layer Security (TLS) &#x2013; and
the CA-based PKI. The PGP Web of Trust is an effort to leverage public
key cryptography for a slightly more generalized model of trust. And
yet all of these technologies are succumbing to growing pains *or*
outright attacks.

The name Firefly evokes one of many biomimetic lessons we may
discover in nature<sup><a id="fnr.2" class="footref" href="#fn.2">2</a></sup>.


<a id="org447efa5"></a>

## Problems

The Firefly architecture proposes to address these problems:


### The CA-based PKI is fragile

The primary problem with the CA-based PKI is the prevalence of Man in
the Middle attacks (MiTM<sup><a id="fnr.3" class="footref" href="#fn.3">3</a></sup>). There have been a series of band-aid
measures like Extended Validation certificates (now seen as a
failure<sup><a id="fnr.4" class="footref" href="#fn.4">4</a></sup>) and Certificate Transparency<sup><a id="fnr.5" class="footref" href="#fn.5">5</a></sup> yet the audits can't
scale (directly), it has time windows of vulnerability, it may leak
browsing information and it doesn't have a standard user experience
(UX) in case of auditing failure<sup><a id="fnr.6" class="footref" href="#fn.6">6</a></sup>.


### The PGP Web of Trust has problems

The network of automatically synchronized public key servers<sup><a id="fnr.7" class="footref" href="#fn.7">7</a></sup> has
worked remarkably well despite some unfortunate design choices that
the identities (UID's which are often e-mail addresses) are completely
exposed and anyone can attach certifications to a key. Largely due to
UX failures the convenience of using short ID's led to the Evil-32
attack<sup><a id="fnr.8" class="footref" href="#fn.8">8</a></sup>. And to make matters worse now we are now seeing
certificate flooding<sup><a id="fnr.9" class="footref" href="#fn.9">9</a></sup>.


### Failure of secure e-mail

Despite the availability of core technologies to send PGP encrypted
e-mail it simply has failed due to incredible complexity and absolute
lack of UX design.  In it's place are a myriad of ad-hoc solutions &#x2013;
often involving some poor messaging implementation on a website which is
"secured" by TLS<sup><a id="fnr.10" class="footref" href="#fn.10">10</a></sup>.


<a id="orgb5d2b5d"></a>

## Goals

Firefly architecture aspires to the following goals:


### An additional TLS Certificate check

Validating TLS certificates in Firefly could provide additional
assurance to Certificate Transparency Auditing and/or offer an
alternative verification path for certificates that do not participate
in the CA-based PKI.


### An alternative public key verification for identities

Perhaps the most common use of the PGP Web of Trust is to verify the
public key of an e-mail correspondent with whom we would like to share
secure messages.  Firefly could replicate this functionality without
some of the design shortcomings of PGP network while providing and
countermeasures for known attacks.


### Avoid the environmental catastrophe of the blockchain

While it is fashionable for self-sovereign digital identity solutions
to rely on distributed ledger technology<sup><a id="fnr.11" class="footref" href="#fn.11">11</a></sup> Firefly
offers an alternative which will not exacerbate climate change<sup><a id="fnr.12" class="footref" href="#fn.12">12</a></sup>.


<a id="org2a25b9a"></a>

# Design

The core principle of Firefly is that each identity owner shall have
exclusive control of their private key material. The impact of this
design choice is that if the proposed pre-planned key backup and
recovery procedures are not followed there is literally no one to call
&#x2013; the identity will be lost. And yet this is the ultimate way to
ensure against abuse by third parties &#x2013; including services offering
convenience via key material management or escrow. This creates an
additional incentive to take proper care of key material.


<a id="org35a8f30"></a>

## Extending SQRL for peer to peer authentication

Software implementations of Firefly will be built "on the shoulders
of giants" as is most software. Core key management will be handled
with Steve Gibson's public domain Secure Quick Reliable Login (SQRL<sup><a id="fnr.13" class="footref" href="#fn.13">13</a></sup>)
technology. The essential concepts leveraged from SQRL include:


### An unique public key pair for every identity relationship

SQRL is designed around a master password based Password Based Key
Derivation Function (PBKDF) which generates an Ed25519 Elliptic curve
public key pair<sup><a id="fnr.14" class="footref" href="#fn.14">14</a></sup> for *every* website (identity client) requiring
authentication.

This leads to one (of many) SQRL advantages in that disparate
websites cannot collude to merge identities as the public
key for each site is unique. And it obviates using a password
manager as the master password is all that is needed to
access the keypair for a given client.


### A concise, offline, paper based identity backup solution

The master SQRL identity information can be represented in a few
hundred bytes and is designed to printed on paper as QR Code for ease
of machine scanning (which is useful in the case of sharing an
identity between multiple devices). The offline backup is encrypted
using a 24-digit decimal Rescue Code which, obviously, should be
stored separately.

Firefly extensions involve using SQRL deliberately for machine-to-machine
communication (in addition to human user to machine communication) as
well as supporting a superset of the SQRL API for web-of-trust
operations.


<a id="orgf9a0a53"></a>

## Bootstrapping with DNS and TLS

Any alternate web-of-trust solution could not be "self hosted"
initially and thus Firefly will need to begin (at least) by relying on
existing DNS and CA-based PKI solutions. Even if self hosting becomes
feasible it makes much more sense to use the existing DNS and CA-based
PKI as additional inputs to the trust heuristic (i.e. the answers may
provide fascinating telemetry that might suggest that a MiTM is being
attempted, for example).

To the degree there is concern about DNS accuracy and/or privacy an
interim solution may involve using DNS over HTTPS (DOH<sup><a id="fnr.15" class="footref" href="#fn.15">15</a></sup>).

Fortunately it is quite easy now to automate creation of Let's
Encrypt<sup><a id="fnr.16" class="footref" href="#fn.16">16</a></sup> TLS certificates.


<a id="org81e01b9"></a>

## A distributed graph database

Each Firefly identity node maintains a set of trust assertions that
may be queried. Unlike the Secure Keyserver network there is no
attempt to constantly replicate the entirety of the trust database
everywhere. Based on the the type of the query it may be delegated to
peers and coalesce responses for for the caller. In this way the *query
function* will move to where the *data* is located (not vice
versa). As the web-of-trust is inherently a social graph it follows
that the data should be organized as a graph database<sup><a id="fnr.17" class="footref" href="#fn.17">17</a></sup>. And
recursive queries in a graph database can have a significant
performance advantage in a graph database vs. a relational
database<sup><a id="fnr.18" class="footref" href="#fn.18">18</a></sup>.

As each identify requires a server the Firefly architecture begins at
the maximum possible level of distribution. Just as a well known
public key has multiple signatures a well known identity in the
Firefly network will have trust assertions on multiple Firefly
servers. In this way the network is resilient against node failures.

In creating a query framework intended to gather multiple data points
as input to trust heuristics Firefly can weigh the importance of
multiple factors including: social proximity, number of positive
assertions, number of revocations, age of as assertions, input from
classic DNS and/or CA-based PKI or the PGP Web of Trust. Each
heuristic may require differing dimensions of consensus depending on
the sensitivity of the decision.  In the web-of-trust we don't expect
the simplicity of "one" answer and yet the signal of consensus will
outweigh the noise when an assertion is trustworthy.

Fortunately there is a wealth of resources in supporting graph
database design. By adding time to the traditional
entity–attribute–value model<sup><a id="fnr.19" class="footref" href="#fn.19">19</a></sup> it is possible to enable queries
over time (and presents an opportunity to take advantage of
immutability<sup><a id="fnr.20" class="footref" href="#fn.20">20</a></sup>). The EAVT schema may be more like the Resource
Description Framework (RDF<sup><a id="fnr.21" class="footref" href="#fn.21">21</a></sup>) Schema<sup><a id="fnr.22" class="footref" href="#fn.22">22</a></sup> or more like other
popular EAVT schemas<sup><a id="fnr.23" class="footref" href="#fn.23">23</a></sup>.

The implementation of the query language ("Firefly Script") takes
inspiration from Datalog<sup><a id="fnr.24" class="footref" href="#fn.24">24</a></sup> and SPARQL<sup><a id="fnr.25" class="footref" href="#fn.25">25</a></sup>.  Especially apropos
for running queries across the Firefly network is the SPARQL Federated
Query<sup><a id="fnr.26" class="footref" href="#fn.26">26</a></sup> standard and implementations<sup><a id="fnr.27" class="footref" href="#fn.27">27</a></sup>.


<a id="org8331e55"></a>

## Anonymity by default

As each Firefly public key is scoped to the context of a given
identity server (as inherited from SQRL) each assertion is, by
default, anonymous. Each Firefly user can decide the degree to which
their public key on any node may be associated with other identities
and/or metadata. In this way a public key may be associated with a
traditional UID (e.g. e-mail address, service URL) or remain opaque.


<a id="org6dec8dd"></a>

## Optional Pet Names

As noted in the paper on Pet Names<sup><a id="fnr.28" class="footref" href="#fn.28">28</a></sup> "Zooko's Triangle<sup><a id="fnr.29" class="footref" href="#fn.29">29</a></sup>
tells us that names can have two out of three properties:
decentralized, globally unique, human meaningful."

The domain name of a Firefly server (the scope) and a user public key
within that server acts as a globally unique identifier.  By design it
is decentralized, but alas not human meaningful.

Thus one type of trust assertion in Firefly is the association of a
Pet Name to Firefly identity giving us hope for human readability and
verification.


<a id="org9d13de0"></a>

## Onion query obfuscation

In some cases it may be desirable for Firefly queries to identify
their provenance (the requesting server), but this is not strictly
required. By leveraging work on federated queries and existing
Internet Protocol algorithms (e.g. Time-To-Live) one can imagine
constructing a layered approach to querying. At each hop in the query
a Firefly server is only aware of the identity of the client and does
not need to reveal the peers to which it will forward the
query. Given a minimum number of hops this may provide TOR<sup><a id="fnr.30" class="footref" href="#fn.30">30</a></sup> like
query anonymity.


<a id="org3a9e005"></a>

# Use Cases

The following use cases are examples of how the Firefly Trust Sync
architecture will operate:


<a id="org5c05a97"></a>

## Invitation to Firefly

As with many distributed networks participation starts with with an
invitation. Firefly's invitation process is inspired by, but hopefully
more simple than that of Secure Scuttlebutt<sup><a id="fnr.31" class="footref" href="#fn.31">31</a></sup>.

To explain how Alice will invite Bob to her network these
mnemonics will be used:

-   **AD** : Alice Domain = <https://alice.rocks>
-   **AK** : Alice private key
-   **Ak** : Alice public key
-   **BD** : Bob Domain = <https://bob.rocks>
-   **BK** : Bob private key
-   **Bk** : Bob public key

The invitation steps are:

1.  Alice sends Bob an invite code (in the EAVT schema):
    **AD** **Ak** **nonce-signed-by-AK**
2.  Bob verifies that **nonce-signed-by-AK** matches **Ak**
3.  Bob replies by authenticating to **AD** thus creating **BK\*/\*Bk**
4.  Bob sends a message to Alice: **BD** **Bk** **nonce-signed-by-BK**
5.  Alice verifies that **nonce-signed-by-BK** matches **Bk**
6.  Alice (**AD** : **Ak**) is now connected to Bob (**BD** : **Bk**)


<a id="orgc0fbd06"></a>

## Identity linking

On Alice's Firefly identity server she wants to assert that
she trusts Bob's identity by entering a fact in the graph database:

1.  Alice inserts an assertion (this example inspired by RDF where
    **aid** is an unique assertion id):
    -   **aid**, wot:truster, **Ak**
    -   **aid**, wot:id, **Bk**
    -   **aid**, wot:sig, **AK-signs-Bk**


<a id="orgb427007"></a>

## Verify web site certificates

We would like to use Firefly as verification for web site certificates.

Now adding the following mnemonics:

-   **W** : Website URL
-   **Wd** : The TLS certificate digest for **W**

Bob wants to publish an assertion that he trusts a given website's certificate:

1.  Bob inserts an assertion (on **BD**)
    -   **aid**, wot:truster, **Bk**
    -   **aid**, wot:web, **W**
    -   **aid**, wot:webcert, **Wd**
    -   **aid**, wot:sig, **BK-signs-W-Wd**

Given this information in the Firefly database we can propose an
extension to Monkeysphere<sup><a id="fnr.32" class="footref" href="#fn.32">32</a></sup> to query Firefly in addition to
(or as a replacement to) the PGP Web of trust.


<a id="orgbab907b"></a>

## Verify ssh server fingerprints

In the same way that Monkeysphere can improve the security
and user experience for both **ssh** server administrators and
users<sup><a id="fnr.33" class="footref" href="#fn.33">33</a></sup> we could propose extensions to Monkeysphere
for server identities.

Here the assertion entered into the Firefly database is
analogous to that for a web server above (and either may
allow specifying a non-standard port).


<a id="orge749b98"></a>

## Send Secure e-mail

By selecting an e-mail as a Pet Name and making trust assertions
about it two (or more) correspondents may trust they have
the proper public with which to encrypt secure e-mail for each other.

If Alice wants to associate the e-mail **<bob@bob.rocks>** with **BD** : **Bk**
she can insert this fact in the database:

1.  Alice trusts Bob's e-mail
    -   **aid**, wot:truster, **Ak**
    -   **aid**, wot:firefly, **BD**
    -   **aid**, wot:id, **Bk**
    -   **aid**, wot:email, **<bob@bob.rocks>**
    -   **aid**, wot:sig, **AK-signs-BD-Bk-email**

Alice knows, then, she can encrypt e-mail for Bob, and
(through analogous steps) Bob knows he can encrypt e-mail
for Alice **<alice@alice.rocks>** with **AD** : **Ak**.

At this point the secure mail exchange approach of Autocrypt<sup><a id="fnr.34" class="footref" href="#fn.34">34</a></sup>
could be used for Alice and Bob to communicate securely.


<a id="org480397d"></a>

## Trust revocation

As the database records a timestamp with every entry (the T in EAVT)
revoking a previous trust assertion is as easy as inserting
a new fact with the attribute **wot:revoke** in assertions where
**wot:sig** had been used.


<a id="org70d147e"></a>

# Advantages

Here are some advantages of the Firefly Trust Sync architecture:


<a id="org065424a"></a>

## Distributed secure database

Considering Firefly as a distributed, secure database can see
the immense benefits over using the blockchain as a database<sup><a id="fnr.35" class="footref" href="#fn.35">35</a></sup>.

*Would you use a database with these features?*

-   *Uses approximately the same amount of electricity as could power an average American household for a day per transaction*
-   *Supports 3 transactions / second across a global network with millions of CPUs/purpose-built ASICs*
-   *Takes over 10 minutes to "commit" a transaction*
-   *Doesn’t acknowledge accepted writes: requires you read your writes, but at any given time you may be on a blockchain fork, meaning your write might not actually make it into the “winning” fork of the blockchain (and no, just making it into the mempool doesn’t count). In other words: “blockchain technology” cannot by definition tell you if a given write is ever accepted/committed except by reading it out of the blockchain itself (and even then)*
-   *Can only be used as a transaction ledger denominated in a single currency, or to store/timestamp a maximum of 80 bytes per transaction*

*But it’s decentralized!*


<a id="org3b861d5"></a>

## Energy conservation

In making trust assertions by writing to a distributed graph database
Firefly is much more energy efficient that having multiple computers
sweat to brute force a one way function<sup><a id="fnr.36" class="footref" href="#fn.36">36</a></sup>:

*By late next year, bitcoin could be consuming more electricity than all the world’s solar panels currently produce &#x2013; about 1.8 percent of global electricity. That would effectively erase decades of progress on renewable energy.*

Given the urgency of global climate change we cannot, in good conscience,
advocate an alternative web-of-trust solution which is on track
to consume 32 Terawatthours (TWh) of energy<sup><a id="fnr.37" class="footref" href="#fn.37">37</a></sup>.


<a id="org9f05148"></a>

## There is no cabal

Some might advocate that "proof of stake"<sup><a id="fnr.38" class="footref" href="#fn.38">38</a></sup> blockchain technology won't suffer
from some of the problems of "proof of work" technology<sup><a id="fnr.39" class="footref" href="#fn.39">39</a></sup>.

And yet, in practice, it would seem that there is still a cabal
of minters that have asymmetric community power to create
Initial Coin Offerings (ICO's) and reap the benefits of the
*droit du Seigniorage*<sup><a id="fnr.40" class="footref" href="#fn.40">40</a></sup>.

In Firefly there is no dependence on any one specific, occult
blockchain network.


<a id="org7b046cb"></a>

## No key escrow

Firefly users are in complete control of their private key
material and do not need to trust any third party "escrow" service.


<a id="org99ef30d"></a>

## Network tolerant of identity server failures

As each identity is represented by a Firefly node (maximal distribution)
and widely held trust assertions are dispersed across the network
it is tolerant of temporary identity server failure.


<a id="orge814572"></a>

## Anti-spam provision

As only trusted identities can make assertions the dispersion of
naively "astroturfing" facts is limited.


<a id="org3dec0c5"></a>

## Anonymity by default

Firefly makes Pet Name style associations on a voluntary basis
by starting at a default of anonymity.


<a id="org3e3429f"></a>

# Disadvantages

Here are some disadvantages of the Firefly Trust Sync architecture
that need further consideration:


<a id="orgb1242c4"></a>

## A server for each identity

While each Firefly identity does not require a physical "server" *per se*
it does require it's own domain name, TLS certificate, and
web service API implementation.

The cost of asserting identities in Firefly is much higher than
in the current PGP Web of trust. While this may have a benefit
of discouraging the propagation of "noise", it is yet a barrier
to adoption.


<a id="org8a83364"></a>

## UX Challenge

One of the failures of the PGP Web of Trust was the utter lack
of user experience design. While the building blocks of SQRL,
Monkeysphere and Autocrypt have made great progress in addressing
parts of the UX challenge, Firefly will need comprehensive
UX design to successful


<a id="org782c1b4"></a>

# Next Steps

Further discussion and analysis of the Firefly Trust Sync architecture
is welcome. Here are a few important next steps to consider:


<a id="orge012047"></a>

## Immutability and GDPR Compliance

There is a certain engineering elegance to an immutable database
and "append only" logs have significant benefits from a security
auditing point of view. But what do we do when the "nuclear launch
codes" get accidentally added to the database. Or what about
very offensive speech?

An early question to resolve is to determine if there's any way
to get the security (and other benefits) of an immutable database<sup><a id="fnr.41" class="footref" href="#fn.41">41</a></sup>
and yet be in compliance with Europe's General Data Protection Regulation
(GDPR<sup><a id="fnr.42" class="footref" href="#fn.42">42</a></sup>)?


<a id="org044ef9a"></a>

## Open Source Prototype

There's nothing like working code to demonstrate that an architecture
design is plausible. An essential next step will be to build open
source prototypes of Firefly, including necessary extensions to
SQRL, Monkeysphere and Autocrypt.


<a id="orgecedcf1"></a>

## Performance Analysis

Given a prototype Firefly implementation it will be possible
to test common operations under synthetic load to determine
likely performance characteristics.


<a id="org23757d2"></a>

## Auditing and reproducible builds

Throughout the discussion of Firefly the focus has been about
trusting the data in the graph database. Clearly Firefly
needs to enable users to trust the software that implements
the system as well.

There may be an opportunity to make trust assertions about
the reproducibility<sup><a id="fnr.43" class="footref" href="#fn.43">43</a></sup> of Firefly software such that users
chain trust the "entire chain of custody" of a trust assertion
(including the software).


<a id="orgc8f517a"></a>

## Threat Assessments

A basic threat assessment must be done to elaborate
expected attacks, such as denial of service.

For each of these threats a mitigation or countermeasure should
be proposed.


<a id="orgda19723"></a>

## Future

Given a basic implementation of Firefly there are some interesting
future possibilities to consider:

-   Could Firefly help improve the trust of Internet of Things (IoT) devices?
-   Could small IoT devices be represented by a Firefly *proxy*?
-   Would it be possible to support TOR-like anonymous queries?
-   Could Firefly become the basis for a generalized trust API<sup><a id="fnr.44" class="footref" href="#fn.44">44</a></sup>?


# Footnotes

<sup><a id="fn.1" href="#fnr.1">1</a></sup> Domain Name System <br/> <https://en.wikipedia.org/wiki/Domain_Name_System>

<sup><a id="fn.2" href="#fnr.2">2</a></sup> SYNC: The Emerging Science of Spontaneous Order, by Steven H. Strogatz <br/> <http://www.stevenstrogatz.com/books/sync-the-emerging-science-of-spontaneous-order>

<sup><a id="fn.3" href="#fnr.3">3</a></sup> New Research Suggests That Governments May Fake SSL Certificates <br/> <https://www.eff.org/deeplinks/2010/03/researchers-reveal-likelihood-governments-fake-ssl>

<sup><a id="fn.4" href="#fnr.4">4</a></sup> Extended Validation Certificates are Dead <br/> <https://www.troyhunt.com/extended-validation-certificates-are-dead/>

<sup><a id="fn.5" href="#fnr.5">5</a></sup> Certificate Transparency Version 2.0 <br/> <https://tools.ietf.org/id/draft-ietf-trans-rfc6962-bis-30.html>

<sup><a id="fn.6" href="#fnr.6">6</a></sup> How will Certificate Transparency Logs be Audited in Practice? <br/> <https://www.agwa.name/blog/post/how_will_certificate_transparency_logs_be_audited_in_practice>

<sup><a id="fn.7" href="#fnr.7">7</a></sup> Secure Keyserver Network <br/> <https://bitbucket.org/skskeyserver/sks-keyserver/wiki/Home>

<sup><a id="fn.8" href="#fnr.8">8</a></sup> Evil-32 <br/> <https://evil32.com/>

<sup><a id="fn.9" href="#fnr.9">9</a></sup> Community Impact of OpenPGP Certificate Flooding <br/> <https://dkg.fifthhorseman.net/blog/community-impact-openpgp-cert-flooding.html>

<sup><a id="fn.10" href="#fnr.10">10</a></sup> Modern Alternatives to PGP <br/> <https://blog.gtank.cc/modern-alternatives-to-pgp/>

<sup><a id="fn.11" href="#fnr.11">11</a></sup> Decentralized Identifiers (DIDs) <br/> <https://w3c-ccg.github.io/did-spec/#introduction>

<sup><a id="fn.12" href="#fnr.12">12</a></sup> Bitcoin’s energy usage is huge – we can't afford to ignore it <br/> <https://www.theguardian.com/technology/2018/jan/17/bitcoin-electricity-usage-huge-climate-cryptocurrency>

<sup><a id="fn.13" href="#fnr.13">13</a></sup> Secure Quick Reliable Login <br/> <https://www.grc.com/sqrl/sqrl.htm>

<sup><a id="fn.14" href="#fnr.14">14</a></sup> SQRL Detailed Cryptographic Design <br/> <https://www.grc.com/sqrl/crypto.htm>

<sup><a id="fn.15" href="#fnr.15">15</a></sup> DOH: DNS over HTTPS has mitigation <br/> <https://en.wikipedia.org/wiki/DNS_over_HTTPS>

<sup><a id="fn.16" href="#fnr.16">16</a></sup> Let's Encrypt <br/> <https://letsencrypt.org/>

<sup><a id="fn.17" href="#fnr.17">17</a></sup> Graph Database <br/> <https://en.wikipedia.org/wiki/Graph_database>

<sup><a id="fn.18" href="#fnr.18">18</a></sup> Neo4j is faster than MySQL in performing recursive query <br/> <https://maxdemarzi.com/2017/02/06/neo4j-is-faster-than-mysql-in-performing-recursive-query/>

<sup><a id="fn.19" href="#fnr.19">19</a></sup> Entity–attribute–value model <br/> <https://en.wikipedia.org/wiki/Entity%E2%80%93attribute%E2%80%93value_model>

<sup><a id="fn.20" href="#fnr.20">20</a></sup> The rise of immutable data stores <br/> <https://usblogs.pwc.com/emerging-technology/the-rise-of-immutable-data-stores/>

<sup><a id="fn.21" href="#fnr.21">21</a></sup> Resource Description Framework <br/> <https://en.wikipedia.org/wiki/Resource_Description_Framework>

<sup><a id="fn.22" href="#fnr.22">22</a></sup> RDF Schema <br/> <https://en.wikipedia.org/wiki/RDF_Schema>

<sup><a id="fn.23" href="#fnr.23">23</a></sup> Unofficial guide to Datomic internals <br/> <https://tonsky.me/blog/unofficial-guide-to-datomic-internals/>

<sup><a id="fn.24" href="#fnr.24">24</a></sup> Datalog <br/> <https://en.wikipedia.org/wiki/Datalog>

<sup><a id="fn.25" href="#fnr.25">25</a></sup> SPARQL <br/> <https://en.wikipedia.org/wiki/SPARQL>

<sup><a id="fn.26" href="#fnr.26">26</a></sup> SPARQL 1.1 Federated Query <br/> <https://www.w3.org/TR/sparql11-federated-query/>

<sup><a id="fn.27" href="#fnr.27">27</a></sup> Blazegraph Federated Query <br/> <https://wiki.blazegraph.com/wiki/index.php/FederatedQuery>

<sup><a id="fn.28" href="#fnr.28">28</a></sup> Pet Names <br/> <https://github.com/cwebber/rebooting-the-web-of-trust-spring2018/blob/petnames/draft-documents/making-dids-invisible-with-petnames.md>

<sup><a id="fn.29" href="#fnr.29">29</a></sup> Zooko's Triangle <br/> <https://en.wikipedia.org/wiki/Zooko%27s_triangle>

<sup><a id="fn.30" href="#fnr.30">30</a></sup> TOR <br/> <https://www.torproject.org/>

<sup><a id="fn.31" href="#fnr.31">31</a></sup> Secure Scuttlebutt <br/> <https://ssbc.github.io/scuttlebutt-protocol-guide/>

<sup><a id="fn.32" href="#fnr.32">32</a></sup> Monkeysphere <br/> <http://monkeysphere.info/>

<sup><a id="fn.33" href="#fnr.33">33</a></sup> Monkeysphere for SSH <br/> <http://monkeysphere.info/getting-started-ssh/>

<sup><a id="fn.34" href="#fnr.34">34</a></sup> Autocrypt <br/> <https://autocrypt.org/>

<sup><a id="fn.35" href="#fnr.35">35</a></sup> On the dangers of a blockchain monoculture <br/> <http://tonyarcieri.com/on-the-dangers-of-a-blockchain-monoculture>

<sup><a id="fn.36" href="#fnr.36">36</a></sup> New Study of Bitcoin’s Energy Use Makes You Libertarian Nerds Look Even Worse Than Usual <br/> <https://www.motherjones.com/environment/2018/05/new-study-of-bitcoins-energy-use-makes-you-libertarian-nerds-look-even-worse-than-usual/>

<sup><a id="fn.37" href="#fnr.37">37</a></sup> The Environmental Case Against Bitcoin <br/> <https://newrepublic.com/article/146099/environmental-case-bitcoin>

<sup><a id="fn.38" href="#fnr.38">38</a></sup> Avalanche (AVA) — Blockchain 3.0: A Novel Metastable Consensus Protocol <br/> <https://hackernoon.com/avalanche-ava-blockchain-3-0-a-novel-metastable-consensus-protocol-28cdc4ee8984>

<sup><a id="fn.39" href="#fnr.39">39</a></sup> Scalable and Probabilistic Leaderless BFT Consensus through Metastability <br/> <https://arxiv.org/abs/1906.08936>

<sup><a id="fn.40" href="#fnr.40">40</a></sup> Seigniorage <br/> <https://en.wikipedia.org/wiki/Seigniorage>

<sup><a id="fn.41" href="#fnr.41">41</a></sup> Append-only databases and the GDPR conundrum <br/> <https://www.bloorresearch.com/2018/02/append-databases-gdpr-conundrum/?cn-reloaded=1>

<sup><a id="fn.42" href="#fnr.42">42</a></sup> GDPR: What your company should know and do, starting now <br/> <https://medium.com/wattx-stories/gdpr-what-your-company-should-know-and-do-starting-now-f62d70f72d7e>

<sup><a id="fn.43" href="#fnr.43">43</a></sup> Reproducible Builds <br/> <https://reproducible-builds.org/>

<sup><a id="fn.44" href="#fnr.44">44</a></sup> Fixing Trust on the Internet <br/> <https://libreplanet.org/2017/program/#day-2-timeslot-14-session-2-collapse>

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.

.
