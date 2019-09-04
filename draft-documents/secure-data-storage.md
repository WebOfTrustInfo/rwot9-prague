# Secure Data Storage

## Abstract

Authors: David Lamers, Tobias Looker, Daniel Bluhm, Amy Guy, Manu Sporny, Dmitri Zagidulin, Kim Hamilton Duffy

Paper Lead: Manu Sporny

After RWoT9 Lead: Amy Guy

We store a significant amount of sensitive data online such as personally identifying information (PII), trade secrets, family pictures, and customer information. The data that we store should be encrypted in transit and at rest but is often not protected in an appropriate manner.

This paper describes current approaches and architectures, derived requirements, and dangers that implementers should be aware of when implementing data storage.

This paper also explores the base assumptions of these sorts of systems such as providing privacy-respecting mechanisms for storing, indexing, and retrieving encrypted data, as well as data portability.

## PROPOSED Sections (in priority order)

- Introduction
  - Survey of existing work
      - [Secure Data Hubs](https://msporny.github.io/data-hubs/)
      - [DIF's Identity Hubs](https://github.com/decentralized-identity/identity-hub/blob/master/explainer.md)
      - [Data Shards](https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/datashards-rationale.md)
      - [Hyperledger Aries](https://github.com/hyperledger/aries-rfcs)
      - [Solid](https://github.com/solid/solid-spec/)
      - [Blockstack](https://docs.blockstack.org/storage/overview.html)
      - [NextCloud](https://docs.nextcloud.com/server/16/developer_manual/client_apis/index.html)
      - IPFS / IPLD
      - [Tahoe LAFS](https://tahoe-lafs.org/trac/tahoe-lafs)
- Core Use Cases
  - Use data and control access to it
      - data is encrypted in transit and at rest
      - Store, retrieve, index, and query
  - Share data with one or more entities
  - Keep the same data in more than one place
      - (replicate)
- Deployment Topologies
    - Mobile device only
    - Mobile device paired with cloud storage
    - Multiple devices (single user) paired with cloud storage
    - Multiple devices (multiple users) paired with cloud storage
- Requirements
    - Multi-party encryption of data in transit and at rest
    - Replicate data (related reading https://github.com/decentralized-identity/papers/blob/master/Hub%20Commit%20Strategies.md)
    - Search over encrypted data
    - Share data with one or more parties
    - Extensible authorization mechanisms (OAuth or ZCAPs or HTTP Signatures)
    - Support for multiple protocols (define HTTP, gRPC, binary on-the-wire, etc)
    - Metadata associated with data
- Design Goals
    - Privacy-preserving storage of data
    - Simplicity - Minimal API and atomic features necessary to meet advanced client/server responsibilities.
    - Layered architecture - higher order features are layered on top of simpler features and are specified in other specifications layered on top of this one.
    - Ensure common data operations are supported (CRUD and search)
- Architecture
  > Insert disclaimer that client/server can be on the same device, they can be peer devices, and so on.
    - Server Responsibilities
        - Enforce authorization policy on data operations
        - Validate requests related to data retrival and persistance (eg is the request trying to get a non-existent document)
        - Persist global configuration
        - Persistence of data (e.g., save as file, sharding already encrypted chunks)
        - Enforcement of change control strategy
    - Advanced Server Responsibilities
        - notifications and pub-sub
        - Audit trails (access log, log of changes)
    - Client Responsibilities
        - Encrypt/decrypt individual data
        - Replication
        - Sharding into encrypted chunks,
    - Advanced Client Responsibilities
        - sharing with other entities
        - global manifests and integrity protection
- Extension Points
  - Authorization Strategies
  - Data Hub protocol (http, didcomm-like, etc)
  - Replication Strategies
- Security and Privacy Considerations
    - Malicious/Accidental deletion of data
    - Ignoring authorization rules
    - Add garbage data to data store
    - Timing attacks on access to data
    - Do not put encrypted data on public networks
    - Unencrypted data and metadata on service provider
    - Partial Matching w/ Encrypted Indexes
    - What a malicious provider, threat model
- Parking Lot / Out of Scope
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
