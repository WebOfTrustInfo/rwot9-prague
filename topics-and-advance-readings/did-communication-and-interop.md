# DID Communication and Interoperability

Daniel Bluhm <daniel.bluhm@sovrin.org>

## The DID-Based SSI Community

Though the [Decentralized Identifier Specification][1] is only just now entering
the standards track at the W3C, an incredibly diverse community focused on
utilizing DIDs to improve our interactions on the internet is already thriving.
At the time of writing, 32 different methods are registered on the [DID Method
Registry][2] with each method being backed by numerous other organizations.

This diversity is a crucial part of a healthy SSI ecosystem,
ideally giving vendors and identity owners the ability to choose the solution
that best suits them and their needs. However, with such a diverse SSI
Community, it is no surprise that each DID Method and surrounding ecosystem
can differ quite significantly from each other. These differences can, again, be
beneficial; but, without efforts to ensure the right level of interoperability,
we risk producing a segmented ecosystem where your identity is not truly
Self-Sovereign.

The goal for this paper for RWOT is to outline the required foundational
elements for interoperability using DID Communication with references to
relevant existing specifications.

## DID Communication

[DID Communication][3] or DIDComm is an effort to standardize messaging for the
core functions of a Self-Sovereign Identity. DIDComm is closely related to the
work of Identity Agents undertaken in the Hyperledger Aries Projects. An
Identity Agent is that enables an Identity Owner to interact with other people,
organizations, and things in an SSI World. An agent has the ability to perform
the cryptographic operations and store the keys needed to maintain high levels
of cryptographic trust. Or, to put it simply, it's the app that an Identity
Owner would use to receive, store, exchange, and manage their verifiable
credentials.

An agent achieves these capabilities through messaging with other agents via
DIDComm; however, anything can use DIDComm. Any software that is capable of
receiving, decoding, and processing a DIDComm message can adopt some of the same
functionality. For instance, a web server can selectively implement just the
DIDComm protocols for verifying credentials to log in a user rather than
implementing the full suite of DIDComm protocols that an agent might typically
support.

DIDComm at its core defines three major building blocks to creating
interoperable communication standards:
- An "[encryption envelope][4]" or the format for encoding an encrypted and/or
	signed payload,
- A "[message][5]" or the payload format,
- And "[protocols][6]" or definitions of messages and their flow between
	corresponding parties to achieve some goal.

These building blocks can be used to conduct the secure exchange of information
between two or more parties while remaining transport agnostic. A DIDComm
message can be delivered through HTTP/HTTPS, XMPP, Bluetooth, Email, QR Code,
snail mail, or even carrier pigeon.

These characteristics, making it simple to adopt whichever protocols are needed
and making no assumptions about the transport mechanism, make DIDComm a
favorable foundation for the layer of interoperability between ecosystems.

[1]: https://w3c-ccg.github.io/did-spec/
[2]: https://w3c-ccg.github.io/did-method-registry/
[3]: https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0005-didcomm/README.md
[4]: https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0021-didcomm-message-anatomy/README.md#envelope-level
[5]: https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0021-didcomm-message-anatomy/README.md#content-level
[6]: https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0003-protocols/README.md#what-is-a-protocol
