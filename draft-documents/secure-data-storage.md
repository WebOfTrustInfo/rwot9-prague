# Secure Data Storage

## Abstract

Authors: David Lamers, Tobias Looker, Daniel Bluhm, Amy Guy, Manu Sporny

Paper Lead: Manu Sporny

After RWoT9 Lead: Amy Guy

We store a significant amount of sensitive data online such as personally identifying information, trade secrets, family pictures, and customer information. The data that we store should be encrypted in transit and at rest but is often not protected in an appropriate manner.

This paper describes current approaches and architectures, derived requirements, and dangers that implementers should be aware of when implementing data storage.

This paper also explores the base assumptions of these sorts of systems such as providing privacy-respecting mechanisms for storing, indexing, and retrieving encrypted data, as well as data portability.


## General Thoughts

- If we are going to claim secure hubs have integrity, we need to address whether the data hub provider has the ability to delete information without a clients knowledge.
- Authorization model, does the hub merely enforce authorization rules, or act as an authorization server.
- What are the assumptions of trust the host the hub must provide, enforcement of authorization rules? Perhaps discuss potential attack vectors from the host of the hub?
- Discuss if data hubs should have the responsibility to sync with other data hubs (and if so, conflict resolving)
- Determine how different authz mechanisms are used such as OAuth, ZCAPs, etc.
- Encrypted searching relies on direct equality

### Archictectual Discussion Points

- Authorization
- Architecture a secure data hub is associated with e.g P2P hub and spoke, server client etc?
-  


### Existing solutions / implementations / proposals

* Solid PODS
    * LDP (RDF data) + authentication + ACL
* Identity Hubs
* Tahoe FS?
*

### Naming things is hard

We need to define 'hub'?

Do we call it something else? Is 'storage' right or is that more about the persistence layer?

### Things missing from current spec

* Design goals
* Authorisation and access control (multiple auth schemes)
    * Mandate one, make others optional
