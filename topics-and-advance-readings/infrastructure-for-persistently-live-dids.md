# Infrastructure for Persistently Live DIDs

As self sovereign identity has begun coming to the fore, specs and protocols have been developed to bring this idea to fruition. The digitial identity document specs are being worked upon by standadizing bodies, and blockchains have been both re-appropriated and newly developed with self sovereign identity in mind. This architecture has inherennt shortcomingns - it is either sacrificing liveness or attempting to build despite that lack which may seem unfixable.

Because writing to a blockchain has an inherently large overhead, this has lead to a bifurcation in the spec where a record must be maintained on a blockchain that references a collection of verifiable credentials stored elsewhere. This can introduce problems of synchrony. There are both limiting factors and liabilities associated with this architecture.

The limiting factors are of both lesser and greater types. On the lesser end, there is the minutia of knitting both layers together. More standards, more software, more maintenance, and possibly more legal situations are required to knit both layers together. On the greater end, it limits the types of applications that may be run on such an infrastructure, since any application/feat of coordination requiring significant liveness will not be able to run. 

However more importantly, there are potentially serious liabilities - that of credential revocation. If an identity provider makes a mistake, or receives new information annd must adjust the status of a particular claim, if they have already signed and circulated a claim, how are they to revoke it? How are the various entities the claim is poised to be presented towards going to know it is no longer valid? Perhaps the issuer of the claim could use a discreet private key to sign each claim. But that could become prohibitively expensive. Or the issuer could use classes of keys, and revoke whole classes of keys at once. But that could effect more than the required targets of revocation. And for every scenario mentioned, this would entail another round trip to the issuer to check if they indeed were authorized, which would defeat the entire point of the signing process. It seems that liveness is a desirable property whenn considering mutating permission systems. 

A solution to those complexities would be to have an inherently networked computational fabric that would consolidate both functions required for self sovereign identity to work - reliable navigability to a particular identity, and the serving of the claims data itself. This would change the rules of interactions for agents in the system in a significatn way. In the current spec, the custody of the verified credentials is given to the idenntity about whom the claim is made. The authority making the claim creates a signed artifact which they hand off to the individual they make the claim about. 

An inherently networked computational fabric could reverse the flow of that transaction. Instead of a credential being created for handoff to an identity and subsequent presentation to an organization/agent as proof of verification, it would be the organization that queries the identity authority with the public key of the identity, and the authority would respond with a positive or negative assertion regarding the query. Doing so would enable rapid updating of identity credentials and systems dependent on identity at all granularities between every agent. 

There are no current implementations of such a system. Although, they have been theorized, and with blockchain type ledgers, they are imminently possible. One such envisioned system, Gravity, is under development. It would be able to provide all properties important to self sovereign identity, including privacy, censorship resistance, transparency, openness to all, and verifiability. More specifically, Gravity, ideally envisioned, is the folllowing: a resilient distributed application runtime that empowers/induces safe computational semantics, cryptographically secure protocols and orthogonally persistent state.

The Gravity protocol is a language based on lambda calculus, prototypes, object capabilities and message passing to create distributed applications.
Gravity nodes are isolated runtime processes connected through cryptographic capabilities. They jointly create a distributed runtime and implement the following protocols:
A distributed ordered message queue to share an event loop and timeline.
A distributed relative address space / scope, to refer to and access objects in the network securely.
A distributed development environment, to collaboratively create, debug and share objects.
Gravity Applications are executed on top of this runtime, and selectively share protocols, state and computation. Gravity applications are:
Persistent: The state of the node and its data structures are durable. The state of the node can be recovered after failure, reboot of the Gravity node or moving across nodes.
Private: Gravity nodes can create an isolated shared state and event timeline.
Verifiable: The integrity of the state, protocol, and execution of a Gravity node is verifiable.
Transactional: State transitions are isolated and atomically consistent across Gravity nodes.
Distributed: Application state is selectively stored across multiple nodes and doesn’t rely on single global mutable state. Applications are networked and only optionally share state, making them inherently scalable.
Secure: A Gravity node can keep secrets. All state is stored and transmitted in an encrypted form.
Safe: Gravity applications follow a secure computation model based on object capabilities and the principle of least authority.
Redundant: Gravity applications may use multiple nodes to execute/verify code, to send messages through, or to store state. Gravity provides constructs that enable high availability and fault recovery.
Portable: Gravity applications and data structures may move across gravity nodes, further improving resilience and adaptability.
Reflective: Protocols, state, and computation may be defined, accessed, analyzed and updated from within Gravity itself.
Gravity enables the creation of a new generation of distributed and resilient applications that are inherently networked.

In Gravity, there would be one class of applications for all identities, be it an authority or an individual. At the programmatic level, these applications would be the same. And so every identity could provide a claim for any other enntity. A public/private keypair would be an address on the Gravity network, at which place this program would live, waiting  for requests or making requests itself. It would be able to scale to serve millions of requests per hour or be so small as to only make ten requests a day. The infrastructural dev/ops requirements would be built into the runtime of the network, along with every other application that would be running in the Gravity network. The same case is true for the verifiability of such applications.


Although speculative, the assurances something like Gravity could provide may make it an attractive option for future development.
