# Formal protocol verification for SSI 

## Introduction

The SSI ecosystem has many components that interact with one another in complex ways. Edge agents and cloud agents interact by creating secure DIDComm channels, exchanging verifiable credentials, and more.

Even when best practices are followed during design and specification of such systems, security problems can still occur through unforeseen interactions. Simple protocols have been believed secure for a long time and found insecure only after tool-assisted formal analysis [1]. Traditionally, formal analysis has often been applied to already established standards and protocols; it has only recently been incorporated more into design processes, e.g., for TLS 1.3. [2]. Similarly, there is a great opportunity to incorporate formal verification into the SSI design process. This not only helps find potential problems, but the modeling process itself helps getting a more precise understanding of security requirements. 

Protocol verification models different agents and the messages they can send over a network. In particular, *symbolic* protocol verification in the *Dolev-Yao network attacker model* [3] assumes that the attacker controls the network, i.e., the attacker can read, send, block, and modify messages, but cannot break cryptography (i.e., cryptography is assumed to be perfect). The goal is to detect *logical* errors in the protocol design that can lead to attacks on desired security properties (such as the secrecy and integrity of messages).

## Modeling Agent-to-Agent Communication (DIDComm)

As a first step, we provide models of increasing complexity for DIDComm, agent-to-agent communication using peer DIDs. The security properties DIDComm aims to provide are *secrecy* (only the intended receiver can learn the content of the message), and in the case of authCrypt, *authentication/integrity* (the message received is what the sender sent). We give four different DIDComm models, which we describe next.

In model 1, the agents already know each other's public keys, and one agent sends an authCrypt-encrypted message to the other. This simple model illustrates how we model authCrypt and the security properties. We successfully verified secrecy of the exchanged message and non-injective agreement [6] (A and B agree that they are talking to each other, and agree on the message content) in this model.

In model 2, we assume that the agents do not have any previously shared information, and perform the DIDExchange [7] protocol over an insecure channel to exchange peer DIDs [8]. The invitee B then sends a message using authCrypt to the inviter A. Unsurprisingly, this protocol does not provide any security guarantees; the exchange was performed over an insecure channel, so neither A nor B have any reason to believe that they are actually talking to the other party. There are different ways to achieve guarantees, e.g., using offline verification or verifiable credentials. 

In model 3, we model the case where the users are in the same room and can perform offline verification. We assume that the agents display the DIDs of each connection. The users then check whether their agents display the same DIDs for the connection, and only proceed with sending the payload authCrypt message if they match. In this model, Tamarin finds an attack where an attacker can change the public keys bound to the DIDs. To avoid this possibility, the inviter must verify that the DID they receive from the invitee was generated using the generation algorithm using the stored version of the received DID Doc as input. We suggest to include the necessity of this check in the peer DID specification.

Model 4 implements the fix described above: A verifies for any exchange request whether the DID was generated according to the algorithm, and only accepts the exchange request if this is the case. In this fixed version, the security properties were proven automatically.

For readers interested in the details, a long version of this topic paper and the Tamarin models are available at https://github.com/SvenHammann90/SSI/tree/master/RWOT_9 .

## Future Work: Modeling other aspects of SSI

We briefly touch on some ideas about other topics, for which we have not yet done formal modeling. To model **verifiable credentials and issuers**, the following two points must be addressed. First, credential issuers usually have a public DID registered on a ledger. To model this, we must also introduce a public DID method and its CRUD operations [5]. Second, verification of verifiable credentials are not necessarily simple signature verification, but may involve zero-knowledge proofs. Verifiable credentials are also issued with respect to a link secret, which is not yet modeled.

We have not yet modeled **DKMS**, i.e., agents controlling different keys and authorization policies granting different rights to different agents. Thus, the model should be extended to model a DID subject, such as a person, separate from their agents, and consider a more fine-grained key distribution.

## References

[1] [https://en.wikipedia.org/wiki/Needham%E2%80%93Schroeder_protocol](https://en.wikipedia.org/wiki/Needham–Schroeder_protocol) ; 
Lowe, Gavin. "Breaking and fixing the Needham-Schroeder public-key protocol using FDR." *International Workshop on Tools and Algorithms for the Construction and Analysis of Systems*. Springer, Berlin, Heidelberg, 1996.

[2] Cremers, Cas, et al. "Automated analysis and verification of TLS 1.3: 0-RTT, resumption and delayed authentication." *2016 IEEE Symposium on Security and Privacy (SP)*. IEEE, 2016. ; 
Cremers, Cas, et al. "A comprehensive symbolic analysis of TLS 1.3." *Proceedings of the 2017 ACM SIGSAC Conference on Computer and Communications Security*. ACM, 2017.

[3] [https://en.wikipedia.org/wiki/Dolev%E2%80%93Yao_model](https://en.wikipedia.org/wiki/Dolev–Yao_model)

[4] https://tamarin-prover.github.io/

[5] https://w3c-ccg.github.io/did-spec/#did-operations

[6] Lowe, Gavin. "A hierarchy of authentication specifications." *Proceedings 10th Computer Security Foundations Workshop*. IEEE, 1997.

[7] https://github.com/hyperledger/aries-rfcs/blob/master/features/0023-did-exchange/README.md

[8] https://openssi.github.io/peer-did-method-spec/index.html

[9] https://openssi.github.io/peer-did-method-spec/index.html#guarantees

Contact Information: sven.hammann@inf.ethz.ch 