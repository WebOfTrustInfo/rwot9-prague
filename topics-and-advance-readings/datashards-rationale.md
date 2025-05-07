# Datashards: secure storage primitives for the web

By [Christopher Lemmer Webber](https://dustycloud.org/), with help from [Serge Wroclawski](https://emacsen.net/@emacsen) and [Tom Marble](http://info9.net/wiki/tmarble/)

<a id="orgbf3c6dc"></a>

## Introduction

Over the last year we have been working on a general mechanism for
URIs representing private, encrypted storage that can live in a
variety of locations.
We call this system "Datashards".
This document is an attempt to lay out its rationale and a very high
level overview of its design.


<a id="org14afde2"></a>

### The problem

The world wide web has brought an unprecedented level of connectivity
and information sharing to the world.
Sadly, very little of this information survives.
Websites go down often, and frequently it is only the portion of
content that is accessible via the Internet Archive that lives on (and
this too is limited to only public content).
This leaves the web reliant on a single steward to preserve its history,
and such content cannot even be reliably viewed via its original URI.

One way to improve this situation is to use content-addressed storage.
Instead of distributing an HTTP url linking to a picture of a cat, we
could distribute a hash of the picture of a cat, for example by using
`urn:sha256d:6nUldx59H40YLAS0ajkVJfx9k0pEX6fT-5HRDsMI8QA` as the identifier.
Now any server or client can store this picture of a cat.
Any node can ask other nodes if they have this cat picture, and we will
know if the cat picture they provide really is the same picture based
on whether the hashes match.
This is the basis of many peer-to-peer file storage systems.

Unfortunately, there are several problems with moving forward with such
a simple content-addressed system:

-   Any data store can inspect and observe all contents, so privacy does
    not exist on this layer.
-   This is even worse in a peer to peer system, because then the
    network cannot help spread content without being able to see all
    content.  If Carlos wants to send Bob a sappy love letter, how can
    he do so without the entire network being able to peek into their
    private life?
-   This ability to see the content you are helping to distribute is also
    a liability; a node wishing to be a good citizen and helping distribute
    content along the network may find that it is storing undesirable
    material in the clear.
    Sometimes it is best to know less.

Additionally, Datashards provides universal names, but a variety of
distribution/storage systems, from a local filesystem to a global
distributed hashtable to sneakernet to one-off REST endpoints, all
depending on need and threat analysis.
The names representing both shards and access capabilities remain the
same regardless of storage and distribution protocol.

<a id="orgf655caf"></a>

### Introducing Datashards

Datashard capabilities (or Datashard ocaps) are very similar to the
forementioned hash-based URNs and do, in fact, use content addressing
under the hood.
Datashard capabilities are valid URIs, and thus are valid link targets
for usage with the world wide web.

The heart of Datashard ocaps comes from chopping up and symmetrically
encrypting content into uniform-sized chunks/shards are content-addressed
"shard URNs".
The shards may be distributed amongst storage and distribution providers
without knowledge by those parties as to what the contents contain.
Only participants who have been explicitly delivered a Datashard
capability can assemble and transform these shards into meaningful
content.

Datashard capabilities come in two flavors (and two new URI schemes):

-   **idsc**: (Immutable DataShard Capability) for fixed/immutable content.
    Builds on shard URNs.
-   **mdsc**: (Mutable DataShard Capability) for mutable/updateable content.
    Builds on Immutable Datashard Capabilities.

Due to the nature of distributed updates, `mdsc:` capabilities have
some synchronization challenges that `idsc:` capabilities do not.
Nonetheless, updates are desirable and are thus provided in the system.


<a id="org4ca8a77"></a>

### History

Datashards has been in development for the last year as part of the
[Spritely](https://gitlab.com/spritely/) project, and prototype implementations exist and function.
The original implementations come from the [Spritely Magenc](https://gitlab.com/dustyweb/magenc/blob/master/magenc/scribblings/intro.org) and
[Spritely Crystal](https://gitlab.com/spritely/crystal/blob/master/crystal/scribblings/intro.org) demos (for the immutable and mutable storage concepts
respectively), and were shown in application towards the
federated social web in the [Spritely Golem](https://gitlab.com/spritely/golem/blob/master/README.org) demo.
Magenc was in fact [originally a RWoT submission](https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/topics-and-advance-readings/magenc.md) and has been iterated
on since that time.

However, the ideas in Datashards are not original.
Most ideas come from [Tahoe LAFS](https://tahoe-lafs.org/trac/tahoe-lafs), [Freenet](https://freenetproject.org/), and [libchop](https://nongnu.org/libchop/).
The main contribution of Datashards is distilling and simplifying
these designs into new URI schemes which can be used on the general
world wide web.

We believe Datashards is very easy to implement, and a
specification/implementation guide is forthcoming.


<a id="org62f35da"></a>

## Datashard URIs

The below explanations are high level summaries; for details
see the [Spritely Magenc](https://gitlab.com/dustyweb/magenc/blob/master/magenc/scribblings/intro.org) and [Spritely Crystal](https://gitlab.com/spritely/crystal/blob/master/crystal/scribblings/intro.org) writeups.

TODO: Those repositories are out of date/sync with the below
explanations.  Convert those documents to a shared Datashards
repository which follows the new URI patterns explained below.


<a id="org50a5367"></a>

### Shard URNs

Shard URNs follow the familiar notation of:

    urn:<hash-type>:<hash>

For example:

    urn:sha256d:X74UbU3NoLTA_Nupi8DhaJ_oQpQ95KFukMAkJJotKgo

These are for the encrypted fixed-size shards.
All shards are restricted to a fixed size of 32 kilobytes.
Thus, stores and delivery relays may be set up to accept and deliver
32 kilobyte shards corresponding to these hashes.

The convention of having objects be assembled from uniform-sized
shards prevents a length-of-file attack, where the specific content
stored is inferred from the file length.

TODO: Do we want to use the hashlink spec instead?  CBOR seems like
overhead but convergence might be good.


<a id="org4c913ac"></a>

### IDSC: Immutable Datashard Capabilities

Immutable content is represented by the following URI convention:

    idsc:<suite-id>.<manifest-hash>.<encryption-key>

Here is an example IDSC URI:

    idsc:p0.X74UbU3NoLTA_Nupi8DhaJ_oQpQ95KFukMAkJJotKgo.eekxqfiZIcEnc8cpR-sD_3X3qLaTzQW-KnovArMkGP0

The components of such a URI can be broken down as follows:

-   **suite-id**: A string of characters representing the "suite" of
    encryption protocols used by this IDSC.
    In the above example, the value is `p0`, for the prototype 0th
    suite, which uses [sha256d](https://en.bitcoinwiki.org/wiki/SHA-256d) hashes (double application of sha256
    to prevent [length extension attacks](https://en.wikipedia.org/wiki/Length_extension_attack)) for content and `aes-ctr` for
    encryption.
    In the future there will be other cryptographic suites available
    which combine specific cryptographic algorithms in a way believed
    to be safe.
-   **manifest-hash**: The base64 encoded (sans padding) hash of the
    initial/manifest shard.
    Converted to a Shard URN before retrieval; in the example
    above this would be converted to
    `urn:sha256d:X74UbU3NoLTA_Nupi8DhaJ_oQpQ95KFukMAkJJotKgo`
-   **encryption-key**: The base64 encoded (sans padding) symmetric key
    used to decrypt the retrieved shards, including the manifest.
    A unique key is generated for every IDSC upload.

Once the initial shard is decrypted upon being retrieved.
The initial shard is typed as either:

-   **raw** if small enough (less than ~32kb), in which case the entire
    file's contents are contained
-   **manifest** otherwise, in which case the actual shards to be
    retrieved is listed (if the manifest is too large, this object may
    itself chain to another manifest object until all shards are
    conveyed).

Each object retrieved is decrypted by the symmetric key.
(An initialization vector is also procedurally generated for each
shard retrieved; however, we are glossing over those details for
the sake of this writeup.)
Thus, while entities may request nodes to store and distribute shards,
only the entities that have been explicitly given an IDSC capability
may read its contents.


<a id="org7c0b3c7"></a>

### MDSC: Mutable Datashard Capabilities

MDSC URIs technically point to immutable IDSC revisions under the
hood, but may be incrementally updated, with no conflict prevention
guarantee.
(Approximation of such guarantees may be modeled via eventual
consistency systems if desired, however.)
Each MDSC is generated from a unique verification/signature (aka
public/private) asymmetric keypair, and in fact the verification
component of the identifier *is* the location of the verification key.
In addition to the content-addressed shard store described previously,
a new source of information is added for mutable capabilities:
registries, which track authorized revisions.
When generating a new version of an MDSC referenced object, writers
generate and sign a new certificate, then deliver to registries who
may then verify and further distribute that certificate to requesting
parties.

There are three access levels of MDSC capabilities:

-   **verify-only caps** (aka *verify* caps): Can verify that the
    metadata describing a revision is an authorized revision, even
    though it can't read the revision's contents or write new
    authorized revisions.
    This is the only crystal capability that the registries know about;
    we never share read or write capabilities with registries.
-   **read caps** (aka *verify-read* caps): Can verify that a revision is
    valid, and can read the associated contents, but can't write out
    new authorized revisions.  Can be transformed into a verify-only
    cap.
-   **read-write caps** (aka *verify-read-write* caps): Can verify
    revisions, read the contents described by revisions, and can even
    write new authorized revisions.  Can be transformed into a read cap
    or verify-only cap.  Users holding a read-write cap should be very
    careful about handing these out and coordinating writes.

Each revision is a canonicalized document which signs off on an
incrementing revision number, an encrypted `idsc:` URI representing
the revision, and an initialization vector used to encrypt the
location.
Since the location is encrypted, registries can verify that the
document represents a new revision, but being only in possession of
the verify capability, cannot actually discover the contents without
access to the read capability.

The structure of a MDSC capability URI is:

    mdsc:<access-level>.<suite-id>.<keydata-hash>.<keydata-enckey>[.<read-key>|.<write-decryption-key>][/<version-num>[/<version-hash>]].

(TODO: This might be simplified if we move to elliptic curve keys;
then we don't need to put both the verify-key-hash and the
verify-key-enckey in the URI, we can just put the entire public key.)

The components of MDSC URIs are:

-   **access-level**: Either `v` for verify, `r` for read-verify, or `w`
    for read-write-verify.
-   **suite-id**: A string of characters representing the "suite" of
    encryption protocols used by this IDSC.  In the above examples, the
    value is `p0`, for the prototype 0th suite, which uses a
    combination of RSA public/private keypairs for the verify/write
    keys, the `p0` IDSC suite for looking up the verification key, and
    `sha256` to convert a write key to a read key.
-   **keydata-hash** and **keydata-enckey**: Used to look up the
    keydata for this MDSC object, which when retrieved contains
    the verification key. (TODO: If we switch to elliptic
    curve cryptography, we can simplify this to one component which
    is just the public key directly.)
-   **read-key**: If this is a read-verify ocap, provides the symmetric
    key used to decrypt the location of the object.
-   **write-decryption-key**: If this is a read-write-verify ocap, this
    is used to retrieve the write key from the keydata mentioned above.
    (TODO: Can also be simplified by embedding directly if using
    elliptic curve cryptography.)  Can be hashed to generate the read
    key.
-   **version-num**: Incrementing base-10 encoded integer used to
    sequentially order revisions, or identify one or a range of
    revisions matching that number.
-   **version-hash**: Since it is technically possible to issue multiple
    version numbers matching a revision, this allows specifying a
    precise version (the hash of the certificate).

Some examples of MDSC capability URIs:

    # verify ocap
    mdsc:v.p0.gl6qBg6i3dc5dz9cylxPcxIWn4SgLdTxWFzyqtwIljk.6B4Vy69Z6GnqF3VAk8eZkUBZbXgR5tWWoC1C_6Pbe7g
    # verify-read ocap
    mdsc:r.p0.gl6qBg6i3dc5dz9cylxPcxIWn4SgLdTxWFzyqtwIljk.6B4Vy69Z6GnqF3VAk8eZkUBZbXgR5tWWoC1C_6Pbe7g.wtNehlhYRxooG1un7cLBDMvjs2S-uEz1jLFgfDEH3Cs
    # verify-read ocap for revision 1
    mdsc:r.p0.gl6qBg6i3dc5dz9cylxPcxIWn4SgLdTxWFzyqtwIljk.6B4Vy69Z6GnqF3VAk8eZkUBZbXgR5tWWoC1C_6Pbe7g.wtNehlhYRxooG1un7cLBDMvjs2S-uEz1jLFgfDEH3Cs/1/
    # verify-read ocap for revision 1, specific hash
    mdsc:r.p0.gl6qBg6i3dc5dz9cylxPcxIWn4SgLdTxWFzyqtwIljk.6B4Vy69Z6GnqF3VAk8eZkUBZbXgR5tWWoC1C_6Pbe7g.wtNehlhYRxooG1un7cLBDMvjs2S-uEz1jLFgfDEH3Cs/1/bNIYWl3VtH5e3m0Znp80fU5qtH6IvqpGl3GlyXmNoD0
    # verify-read-write ocap
    mdsc:w.p0.gl6qBg6i3dc5dz9cylxPcxIWn4SgLdTxWFzyqtwIljk.6B4Vy69Z6GnqF3VAk8eZkUBZbXgR5tWWoC1C_6Pbe7g.MeMgmy_j0CI8jwT0EUX01bF7N0UAVSYwHhNQ67h2WAE

As stated before, there is no guarantee that multiple conflicting
revisions won't be issued, or that a user requesting the latest
revision will get the absolutely latest version.
However, a specific revision can be more explicitly marked by
specifying the `version-num` and `version-hash`.


<a id="orgb2b174d"></a>

## Distribution and storage mechanisms

Datashards does not itself specify storage or distribution mechanisms.
However, a variety of approaches are possible.


<a id="org1252f84"></a>

### IDSC content stores


<a id="org33621f1"></a>

#### Foundational operations

The foundational operations for a content store endpoint is:

-   **store-shard**: Accepts as its body a shard of no more and no less
    than 32 kilobytes.
    It returns the Shard URN that it thinks this data is represented
    by that data.
-   **get-shard**: Is queried for a Shard URN and in its response body
    returns what should be the data representing that data.
    Raises the appropriate "Not Found" error if it can't find it
    (though the store may itself recursively search the network for
    that content if appropriate).

In both cases the client MUST verify that the hash and the contents
match what the server claim they are.


<a id="org09f3599"></a>

#### Directed storage systems

-   Local storage: a local, on-disk or in-memory key-value store may be
    used to store hashes.  May be read-only, write-only, or read-write.
-   Remote storage: an endpoint may be provided (whether it be via HTTP
    or whatever else) using a key-value lookup and storage mechanism.
    May be read-only, write-only, or read-write.  
    Variations:
    -   A user's read-write storage endpoint for just their own data.
    -   A cluster of read-write storage endpoints, perhaps facilitated
        by a local abstract endpoint that pushes and pulls content from
        the cluster.
    -   Alice stores content on her server via her read-write endpoint,
        Alice's server sends an update to Bob's server providing an IDSC
        URI and a read-only endpoint for retrieving that content, and
        now Bob's server retrieves that content.


<a id="orge8818f1"></a>

#### Global storage systems

Multiple paths to global storage systems are possible:

-   A DHT such as Kademlia
-   Gossip protocols
-   Etc.

1.  Advisement against mixing with decrypted CAS nodes.

    For a global storage system, it is strongly advised to NOT reuse an
    existing content-addressed system such as IPFS.
    While this is absolutely possible, the liability considerations for
    being a node operator are dramatically more complicated if unencrypted
    content is conventionally stored alongside encrypted content.
    While it is also not possible to consistently programmatically detect
    which content is decrypted and which content is not, setting up new
    networks intentionally built for the purpose of never having such
    content on them should reduce the amount of relevant overlap.

2.  "Malicious content" lists

    It is possible that in building such a global system, a known list of
    "malicious content shards" becomes available or strongly encouraged to
    subscribe to, in which case such nodes might choose to not distribute
    or accept these shards.
    Since referring to shards is possible without revealing their
    contents, it is possible to do so without constructing an effective
    "shopping list" for data which is encrypted.
    However, following any such list will have to be based on a trust (or
    coercive) relationship between that node and the list-supplying-party.

3.  Eventual weakening of encryption

    One thing we cannot fully prevent is the possibility that today's
    robust encryption algorithms will weaken over time.
    While any transmitted content may be retained and eventually decoded,
    intentionally storing in a system designed to keep content around for
    a long time means that eventually, should weaknesses in the underlying
    cryptography be found, such secrets will be easier to access.
    As such, it may often be more desirable to use directed storage and
    transmission than global storage and transmission.
    
    That said, it may be possible to take steps such as mixing encryption
    mechanisms that might provide a possibility that secrets will remain
    secrets from prying eyes for longer.
    See the Tahoe-LAFS [One Hundred Year Cryptography](https://tahoe-lafs.org/trac/tahoe-lafs/wiki/OneHundredYearCryptography) for ideas.

<a id="org3afe81f"></a>

### MDSC revision registries


<a id="orgaa345b2"></a>

#### Foundational operations

A registry consists of two foundational operation, and one optional
operation.

-   **add-revision**: Submits a signed revision certificate in union with
    the verification capability to be updated.
    The submitting client MUST NOT submit a capability with read or
    write access; only verification-only capabilities are allowed.
    The server MUST then dereference the keydata and verify that it is
    a valid revision.
    The server may then update its table of known revisions with this
    revision.
-   **get-known-revisions**: Given a verification capability, returns
    an ordered set of all known good revisions, sorted first by revision
    number and then the specific revision hash.
    Specifying a more precise verification capability narrows the set
    returned; specifying a `version-num` returns only revisions
    matching that `version-num` whereas specifying both a `version-num`
    and `version-hash` specifies an exact commit.
    The client MUST verify that all revisions have authorized signatures
    and that revision numbers and version hashes match appropriately.

Optionally, registries may also support:

-   **get-store**: Suggests a content store by which one may retrieve IDSC
    objects (including the keydata in the present design).


<a id="orgbd57793"></a>

#### Directed registries

As with IDSC stores, registries can be local or remote.

The general patterns are the same as with IDSC stores, with the
additional complexity of potential conflicting updates (especially in
the case of multiple writers).


<a id="org37246c4"></a>

#### Global registries

Globally-facing registries may exist and cooperate with other
registries by sharing information, for example by using a gossip
protocol.
Again, there are no guarantees that a registry has or is conveying
the absolutely latest revisions of an MDSC object.


<a id="org290d51b"></a>

#### Cooperatively avoiding write conflicts

Malicious write conflicts are difficult to deal with and structurally
avoid.
However, it is feasible to *cooperatively* reduce the amount that
write conflicts occur in case of multiple writers.

Let's say that Alice and Bob are both stewards of an MDSC object.
If both of them push an update 3 before seeing each others' updates,
there will be a conflict as to which is the official update number 3.
However, Alice and Bob could voluntarily choose to always first push
updates to a special cooperative registry specifically built for this
task.
In most systems, registries should record and propagate any conflicts
they discover.
However, in this coordination registry, if either Alice or Bob tries
pushing an update for a revision number that the coordination registry
has already seen, the server will reject the update with an error message
that allows Alice or Bob to be informed so that they can resolve the
conflict before pushing it out to the wider network.


<a id="orgc64115b"></a>

## In contrast to existing systems


<a id="org2ac9464"></a>

### IPFS

[IPFS](https://ipfs.io/) is a popular content addressed store.
IPFS's default mode is to store unencrypted content.

In contrast, Datashards provides support for private distribution.
Datashards shards are opaque not only to make disclosure of contents
an intentional act but also to reduce the burden of participants hoping
to help the network.
Node operators should be able to help distribute content without being
liable for their contents.

For this reason, while a global Datashards store could be bootstrapped
very quickly by using IPFS as the backend, it is better to start out with
a global distribution network that simply does not have unencrypted content
as its default.


<a id="orgdd445fc"></a>

### Tahoe-LAFS

[Tahoe-LAFS](https://tahoe-lafs.org) is an incredible project and by far the greatest source of
inspiration for Datashards' content-addressed-but-private design.
The primary differences between Tahoe and Datashards are:

-   Tahoe is more mature and established than Datashards and has probably
    accounted for many rough edges we have yet to encounter.
-   Tahoe is currently mostly built for deployment to an intentionally
    constructed cluster of nodes (akin to the "directed" stores/registries
    described above) and as of yet does not support the option for global
    storage and distribution of content.
    In contrast, Datashards does not specify and is not tied to any
    specific storage or distribution mechanism.
-   Tahoe's URIs aren't constructed to be of "general use" on the web
    the same way that http or hash-based urn schemes are.
-   Tahoe provides some support for diff-based updates, which do not yet
    exist in MDSC (but could).
-   Tahoe supports pairwise redundancy in case of the loss of some
    chunks/shards, at some additional storage cost.


<a id="orgf2795e3"></a>

### Freenet

[Freenet](https://freenetproject.org/) pioneered many of the ideas used by both Tahoe and Datashards.
The primary differences between Freenet and Datashards are:

-   Freenet does not have and is not presently aiming for a variety of
    implementations or an effort to standardize its architecture.
-   Freenet supports one "global" storage and routing architecture
    (though rooted in small world networks) and is very tied to that
    design.
    In contrast, Datashards does not specify and is not tied to any
    specific storage or distribution mechanism.
-   Freenet supports pairwise redundancy in case of the loss of some
    chunks/shards, at some additional storage cost.


<a id="orgd117ada"></a>

## Where to from here?

-   Datashards has not yet undergone a security audit; we would like to
    have one if possible.
-   While some prototype applications utilizing Datashards have been
    built, we would like more user-facing applications, including:
    -   Real-world usage by distributed social networks
    -   Game asset storage
    -   Free Libre and Open Source software and cultural distribution
-   Currently the only implementation is in Racket, but another
    implementation is currently underway in Python.
    We would love to see implementations in as many languages as possible.
-   We do not yet have any global mechanisms built yet for the
    Datashards content addressed stores and registries.
    We are considering building prototypes of these based on Kademlia and
    gossip protocols.
-   Currently the IDSC structure does not support shard parity, but we have
    ideas on how to accomplish this if desired.
-   Metadata is not supported yet and objects follow the basic "bag of bytes"
    metaphor.
    Would it be better or worse to add support for metadata?
    We don't know.
-   The initial implementation of MDSC was built on RSA.  However, many
    components of it (and their explanation) would be greatly
    simplified by using elliptic curve cryptography, because the
    smaller keysize could mean that directly embedding the keys is feasible.
-   A step-by-step writeup of the algorithms used by Datashards needs
    to be written.
-   A test suite would be useful.
-   We would like to submit Datashards for standardization, pending enough
    implementations.

