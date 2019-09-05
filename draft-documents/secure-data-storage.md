# Encrypted Data Vaults

Authors: David Lamers, Tobias Looker, Daniel Bluhm, Amy Guy, Manu Sporny, Dmitri Zagidulin, Kim Hamilton Duffy

Paper Lead: Manu Sporny
After RWoT9 Lead: Amy Guy

We store a significant amount of sensitive data online such as personally identifying information (PII), trade secrets, family pictures, and customer information. The data that we store should be encrypted in transit and at rest but is often not protected in an appropriate manner.

This paper describes current approaches and architectures, derived requirements, and dangers that implementers should be aware of when implementing data storage.

This paper also explores the base assumptions of these sorts of systems such as providing privacy-respecting mechanisms for storing, indexing, and retrieving encrypted data, as well as data portability.

# Survey of existing work
      - [Secure Data Hubs](https://msporny.github.io/data-hubs/)
      - [DIF's Identity Hubs](https://github.com/decentralized-identity/identity-hub/blob/master/explainer.md)
      - [Data Shards](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/datashards-rationale.md)
      - [Hyperledger Aries](https://github.com/hyperledger/aries-rfcs)
      - [Solid](https://github.com/solid/solid-spec/)
      - [Blockstack](https://docs.blockstack.org/storage/overview.html)
      - [NextCloud](https://docs.nextcloud.com/server/16/developer_manual/client_apis/index.html)
      - IPFS / [IPLD](https://github.com/ipld/specs)
      - [Tahoe LAFS](https://tahoe-lafs.org/trac/tahoe-lafs)

The problem of decentralized data storage has been approached from various different angles already. This section outlines commonalities and differences between different existing implementations. Separating storage from applications which use the stored data is key to most of these architectures. Some of these projects specify their application ecosystems along with the data storage mechanisms, and some are concerned only with storage.

[Blockstack](https://docs.blockstack.org/storage/overview.html), [NextCloud](https://docs.nextcloud.com/server/16/developer_manual/client_apis/index.html) and [Solid](https://github.com/solid/solid-spec/) all describe decoupled application and storage architectures.

Blockstack uses a blockchain for transactional data, but not for end users' stored data itself. The Blockstack data storage system is called Gaia, which runs as a service and writes to a user's chosen storage once a user has authenticated with the clientside application they wish to use. The storage, chosen by the user, may be on a centralized cloud provider like AWS or a VPS like those provided by DigitalOcean. Gaia writes the data exactly as given, whether a valid or invalid data format, encrypted or not, so long as a valid bearer token is included in the request.

NextCloud uses WebDAV to read and write data

Solid combines [LDP](https://www.w3.org/TR/ldp) with [OpenID Connect]() auth and [Web Access Control]() to end users to sign into client applications, and read and write data from their personal storage. Resources (data objects) on Solid servers are represented by HTTP URIs, and Solid servers receive HTTP requests (`GET`, `POST`, `PUT`, `DELETE`) containing RDF payloads and create or modify the target URI accordingly. Resources are listed in `ldp:Container`s, which serve as indexes which can be updated by end users or client applications according to specific needs. Additional indexes include the Type Registry, which allows clients to easily retrieve particular resources according to their `rdf:type` attribute, and for client applications to associate the type of data they most frequently operate on with the URI of the application itself. No search interface has been specified. Some implementations may expose a SPARQL endpoint. Data on Solid servers is not encrypted. HTTPS is assumed for the connection between clients and servers. Different instances of Solid servers do not communicate with each other.

At a lower level, [Data Shards](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/datashards-rationale.md) is concerned with encrypted storage and replication of data across devices.

[Tahoe-LAFS](https://tahoe-lafs.org/trac/tahoe-lafs) uses a client-server architecture, whereby a local client encrypts data, breaks it into pieces, and stores it on one or more servers on other devices (or the inverse). The client creates and stores redundant pieces of data so system is resilient to corruption of some shards or servers going offline. Servers can neither read nor modify the data. Data is organised in a filesystem like directory structure and access control makes use of this. Data can be mutable or immutable.

IPFS

IPLD

[DIF's Identity Hubs](https://github.com/decentralized-identity/identity-hub/blob/master/explainer.md)

[Hyperledger Aries](https://github.com/hyperledger/aries-rfcs)

## Core Use Cases (David)
From an end-user perspective the following top three use cases have been identified. This list is not extensive and just covers the most important ones.

- **Use data and control access to it**:
 As end-user I want to store my data in the encrypted data vault. Since I don’t want the storage provider to be aware of any data I store, I will encrypt my data on the edge device. This means that all my data is encrypted in transit and at rest, only I as end-user can see and use the actual data. When I have stored my data, I need a unique endpoint for each document that I can use to retrieve the data I have stored before.
A large amount of data will be stored in the vault which requires that I can do some searching. Since I don’t want to be my storage provider to be aware of any (meta-)data I want to use encrypted indexes and be able to query the vault on those.

- **Share data with one or more entities**:
As an end-user, I might want to share my data with other entities.

- **Keep the same data in more than one place**:
Data

The requirements and architecture section further elaborate on the technical side of the use cases


## Deployment Topologies (Daniel)

This specification can be deployed in a number of topologies to support the variety of use cases listed above. The following topologies are specifically considered by this specification.

> How much detail are we looking for here?

### Mobile device only

A hub can run as a library on a mobile device. This library can utilize local storage to provide an encrypted database. In this configuration, both the hub and the client would reside on the same device.

- Uniform interface for accessing data, transition to remote storage later if desired?

> Separate service or as a library? Or left to the implementer and not designated by the spec?.

### Mobile paired with cloud storage

When paired with cloud storage, a mobile device can take advantage of remote resources.

### Multiple devices (single user) paired with cloud storage

When adding more devices managed by a single user, the hub can be used to synchronize data across devices.

### Multiple devices (multiple users) paired with cloud storage

When pairing multiple users with cloud storage... (TODO)


# Requirements (Manu)

This section elaborates upon a number of requirements that have been gathered from the core use cases.

## Privacy and Multi-party Encryption

To ensure an entity's privacy, the use of encryption in transit and at rest is a requirement for the ecosystem.

One of the goals of the technology is to ensure that information is always protected from unauthorized parties. It is necessary that all data is encrypted in transit and at rest. Since data could be shared with more than one entity, it is also necessary for the encryption mechanism to support encrypting data to multiple parties.

## Sharing and Authorization

This technology is designed to ensure the authorized sharing of information between multiple parties. It is necessary to have a mechanism that enables the sharing of encrypted information among one or more entities.

There are multiple valid authorization schemes that are possible. The technology is expected to specify one mandatory mechanism, but also allow other alternate authorization schemes. Examples of authorization schemes include OAuth, HTTP Signatures, and Authorization Capabilities (ZCAPs).

## Replication

It is expected that information can be backed up on a continuous basis. For this reason, it is necessary for the system to support at least one mandatory replication strategy, but also allow other alternate replication strategies.

## Metadata and Searching

Large volumes of data are expected to be stored using this technology. It is important for clients to be able to associate metadata with the data such that it can be searched. Since it is also important for the service provider to not see data that they are not authorized to see, the searching of metadata by the service provider is expected to be performed in a way that doesn't enable them to see the metadata. An encrypted search mechanism is a necessary feature of the technology.

## Protocols

Since this technology can reside in a variety of operating environments, it is important that at least one protocol is mandatory, but that other protcols are also allowed by the design. Examples of protocols include HTTP, gRPC, Bluetooth, and binary on-the-wire protocols.

# Design Goals (Manu)

This section elaborates upon a number of guiding principles and design goals that have shaped this technology.

## Prioritize Privacy

Fundamentally, this technology is intended to protect an entity's privacy. When exploring new features, the first question that is explored is "How would this impact privacy?".

- Privacy-preserving storage of data
- Simplicity - Minimal API and atomic features necessary to meet advanced client/server responsibilities.
- Layered architecture - higher order features are layered on top of simpler features and are specified in other specifications layered on top of this one.
- Ensure common data operations are supported (CRUD and search)

## Architecture (Tobias & Dmitri)
Secure Data Hubs, define a client-server relationship, whereby the hub is regarded as the server and the client which acts as the interface used to interact with the hub. This enforced architecture is required due to some of the unique properties of secure data hubs. (TODO complete)

> Note: Even though a client-server relationship is establish with secure data hubs, nothing excludes both the server/hub and client existing on the same device, in fact the expectation is this will be a popular model for running local hubs that replicate with hubs that are hosted elsewhere.

### Server Responsibilities
The server is assumed to be of low trust and hence must have no visibility of the data it persists, however even in this model it still has a set of minimum responsibilities it must adhere to.
-	Expose an API for clients to consume.
-	Enforce authorization policies on requests: When a hub client makes a request to query, persist, modify or delete data in the hub, the hub must enforce any associated authorization policy that is associated with the request.
-	Validate requests: When a hub client makes a request to query, persist, modify or delete data in the hub, the hub must validate the request.
-	Persist global configuration.
-	Persist data: The hub is free to persist data however it is designed, however it must adhere to the common expectations of a data storage provider, such as reliable persistence, updatability and ability to query.

### Advance Server Responsibilities
- Notifications: A commonly associated feature with data storage providers is a mechanism by which to notify about changes to the data it persists. A hub may optional implement such mechanism by which clients can subscribe to changes in data from the hub.

### Client Responsibilities
(Dmitri)

The Client is responsible for providing an interface to the Server, with  bindings for each relevant protocol (HTTP, RPC, or some binary over-the-wire  protocol), as required by the use case.

In addition, at the most basic level, the client is responsible for the following functionality.

#### Encryption/Decryption of Individual Data Resources

Since one of the primary design goals of this spec is privacy-preserving storage of data, it is essential that all encryption and decryption of data is done on the client side, at the edges. The data (including metadata) MUST be opaque to the server, and the architecture is designed to prevent the server from being able to decrypt it.

#### Sharding of Data Into Encrypted Chunks

* Explain why chunking is necessary (rather than storing the data as a single continuous resource) to prevent bandwidth DDOS type attacks (esp. relevant for large files)
* Chunking partially addresses "file size" type attacks (if the data is smaller than a single chunk, padding is introduced)
* Each chunk is individually encrypted (as a JWE / CWE)
* The chunks (ordering and location) will be recorded/tracked in a manifest-like document (see next section)

#### Streams / Manifest Documents

When writing data, the Client encrypts and splits the data into chunks, and sends the chunks to the Server. The Client must also create a manifest-like document (Stream / Structured Document in the SDH spec currently).

#### Replication

#### Index Tags

**Question:** Does this belong in the Advanced Client section?

- Providing index tags to enable querying over encrypted data


### Advanced Client Responsibilities
    - Advanced Client Responsibilities (Dmitri)
        - sharing with other entities
        - global manifests and integrity protection

## Extension Points
  - Authorization Strategies
  - Data Hub protocol (http, didcomm-like, etc)
  - Replication Strategies

## Security and Privacy Considerations
    - Malicious/Accidental deletion of data
    - Ignoring authorization rules
    - Add garbage data to data store
    - Timing attacks on access to data
    - Do not put encrypted data on public networks
    - Unencrypted data and metadata on service provider
    - Partial Matching w/ Encrypted Indexes
    - What a malicious provider, threat model

## Parking Lot / Out of Scope
    - Query details, sorting, pagination
    - Key Management
    - Choice of Authz strategy
    - Choice of Change control / conflict resolution strategy

## General Thoughts

- If we are going to claim secure hubs have integrity, we need to address whether the data hub provider has the ability to delete information without a clients knowledge.
- Authorization model, does the hub merely enforce authorization rules, or act as an authorization server.
- What are the assumptions of trust the host the hub must provide, enforcement of authorization rules? Perhaps discuss potential attack vectors from the host of the hub?
- Discuss if data hubs should have the responsibility to sync with other data hubs (and if so, how to resolve conflicts)
- Determine how different authz mechanisms are used such as OAuth, ZCAPs, etc.
- Encrypted searching relies on direct equality
- What are the opportunities for encrypted searching (e.g. using Homomorphic encryption), and what are the dangers
- We dont have anyway to retrive the history of an objects updates

### Archictectual Discussion Points

- Authorization
- Architecture a secure data hub is associated with e.g P2P hub and spoke, server client etc?
- Should secure data hubs define an api and associated information divorced from HTTP and instead provider another spec about how an HTTP based web server implementation could be realized?
- Should the authorization interface be included in the secure data hub or should this be pluggable and seperate and the only firm designated role of a hub is the enforcement of authorization rules specified elsewhere?


### Existing solutions / implementations / proposals

* Solid PODS
    * LDP (RDF data) + authentication + ACL
* Identity Hubs
* Tahoe FS?
* NextCloud
*

### Naming things is hard

We need to define 'hub'?

Do we call it something else? Is 'storage' right or is that more about the persistence layer?

'encrypted' instead of 'secure'?

### Things missing from current spec

* Design goals
* Authorisation and access control (multiple auth schemes)
    * Mandate one, make others optional

## Implications of adding a commit strategy interface to hubs

- The hub provider must enforce the rules set out by the document type, i.e check the commit is valid. This varies for different commit strategies
- The hub provider must be able to assemble the current state of an object when requested


Lucidchart link (boxes that were on the whiteboard): https://www.lucidchart.com/invitations/accept/ce2fdea4-19ee-47fc-bf45-39d5a6628a9b
