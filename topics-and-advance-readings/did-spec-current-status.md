# The Current Status of the DID Specification

By Amy Guy &lt;amy@rhiaro.co.uk&gt;, Digital Bazaar

Work on the [Decentralized Identifier 1.0 specification](https://w3c-ccg.github.io/did-spec/) began at RWOT \#2 in May 2016, and a draft was published on 21 November 2016. Work continued under the custody of the [W3C Credentials Community Group](https://www.w3.org/community/credentials/), a group of 237 members, who contribute by taking part in [weekly teleconference calls](https://w3c-ccg.github.io/meetings/), engaging in discussions on the [mailing list](https://lists.w3.org/Archives/Public/public-credentials/), and [raising issues on the spec on GitHub](https://github.com/w3c-ccg/did-spec/issues/). A W3C Working Group is currently in the process of being [chartered](https://w3c-ccg.github.io/did-wg-charter/) in order to progress the work further and take the DID Specification (and possibly others) to W3C Recommendation status over the next two years. It's possible that by the time of RWOT9 the group will have been chartered and begun meeting (watch this space).

A version of the DID Specification has been frozen as a [Community Group Final Report](https://w3c-ccg.github.io/did-spec/CGFR/2019-08-10/) so that it can be submitted as formal input to the Working Group when the time comes.

This document serves as a summary of the current state of work on the specification. It includes a rough categorization of the current open [issues](https://github.com/w3c-ccg/did-spec/issues) and [pull requests](https://github.com/w3c-ccg/did-spec/pulls), with the goal of identifying actions which can be taken quickly to move the spec forward, as well as topics which need extended discussion amongst the community. Issues (and sometimes PRs) are categorized as follows:

* **clarify**: Clarification or disambiguation of concepts the community already has consensus on.
* **discuss**: Topics which need more discussion to reach consensus about.
* **editorial**: Updates to informative language, without changes to meaning or conformance criteria.
* **elsewhere**: Issues relating to other documents (specs, namespaces, etc).
* **question**: Questions about the spec or implementation guidance.

If you're new to DIDs, or want a refresher on the background and core concepts of the DID spec, you will find it useful to read the [DID Primer](did-primer.md) (or [extended DID Primer](did-primer-extended.md)) first.

This document will be updated as work on the DID specification progresses, so information will be current at the time of RWOT9.

## Topics of note

Major areas of ongoing discussion and work, which may span multiple issues or PRs, are outlined here.

* Cleaning up introduction(s), overview, and similar ([issues and PRs](https://github.com/w3c-ccg/did-spec/labels/intro%2Foverview):
  * Paragraphs of introductory text throughout the spec contain a lot of background information that made sense during earlier drafts, when the work was being introduced to the community, but should be made more succinct or moved out to supporting documents as we progress towards a W3C Working Draft.
  * Feedback on related documents such as the DID Working Group Charter and the DID Resolution specification have resulted in a need for additional introductory or explanatory text in some places.
  * Paragraphs of introductory and explanatory text through the spec contain ideological points that are not necessarily agreed by everyone. These should be worked on to improve consensus, and remove ambiguity or potential misreadings.
* Matrix parameters - which should be included in the DID URI and which belong elsewhere in the stack? (eg. "DID parameters that are part of the DID URL specify what resource is being identified, whereas DID resolver options that are not part of the DID URL control how that resource is dereferenced")

## Clarification needed

Some topics have consensus amongst members of the Community Group, or are intuitively understood by people who have been deeply embedded in the work for a while, but remain unclear with regards to text in the specification. For these, the spec needs new text, or reworking of existing text, to make sure concepts are communicated clearly and unambiguously to new readers.

Issues are labeled '[clarify](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Aclarify)' and include:

* Relationship with key management operations: [#147](https://github.com/w3c-ccg/did-spec/issues/147)
* Definition of "proof purpose": [#213](https://github.com/w3c-ccg/did-spec/issues/213)
* Representing services: [#224](https://github.com/w3c-ccg/did-spec/issues/224)
* Making sure normative statements are testable: [#228](https://github.com/w3c-ccg/did-spec/issues/228)

Action: The CG (or future WG) should agree definitive definitions or statements for each of these, and then work to integrate them into the spec text.

## Bigger discussion points

Some topics need deeper discussion to ensure common understanding amongst the CG/WG and the wider community, or more technical work to make sure they are resolved properly.

Issues are labeled '[discuss](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Adiscuss)' and include:

* Matrix parameters: [PR#195](https://github.com/w3c-ccg/did-spec/pull/195), [PR#193](https://github.com/w3c-ccg/did-spec/pull/193), [PR#192](https://github.com/w3c-ccg/did-spec/pull/192), [PR#191](https://github.com/w3c-ccg/did-spec/pull/191)
* Definition of DID controller: [#263](https://github.com/w3c-ccg/did-spec/issues/263), [#205](https://github.com/w3c-ccg/did-spec/issues/205)
* `id` for `service` and `publicKey`: [#247](https://github.com/w3c-ccg/did-spec/issues/247)
* What do/can/should DIDs identify? [#216](https://github.com/w3c-ccg/did-spec/issues/216), [#148](https://github.com/w3c-ccg/did-spec/issues/148)
* Method-specific DID params: [#200](https://github.com/w3c-ccg/did-spec/issues/200)
* Empty `method-specific-id`: [#198](https://github.com/w3c-ccg/did-spec/issues/198)
* Key revocation: [#96](https://github.com/w3c-ccg/did-spec/issues/96)

Action: discuss at RWOT and on CCG calls or WG meetings, resolve misunderstandings, and where applicable break issues down into manageable changes that can be made to the spec.

## Smaller todos

Editorial issues, such as grammatical fixes or reworking sentences without changing the meaning, and perhaps structural changes like section naming or ordering, are labeled '[editorial](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Aeditorial)' (not listed here, see link).

Action: PRs please!

## External documents

Some aspects of the DID work are eventually extracted into separate specifications. There are other external documents which are connected to the spec. Issues relating to these are labeled '[elsewhere](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Aelsewhere)'. Issues are not listed here (click the link) but relevant documents include:

* [The DID Resolution specification](https://w3c-ccg.github.io/did-resolution/)
* [The DID Method Registry](https://w3c-ccg.github.io/did-method-registry/)
* [The JSON-LD context](https://github.com/w3c-ccg/did-spec/tree/gh-pages/contexts)
* [The Linked Data Cryptosuites Registry](https://w3c-ccg.github.io/ld-cryptosuite-registry/)

Action: Open issues or PRs on external documents, update references or summaries in the DID spec if applicable.


## Questions, implementation guidance

Some issues are opened by people with questions about the spec (which don't need spec changes to answer) or requests for guidance about implementations or technical details. These are labeled '[question](https://github.com/w3c-ccg/did-spec/issues?q=is%3Aissue+is%3Aopen+label%3Aquestion)' (not listed here, see link).

Action: answer the commenter's question(s), check they are happy, and close the issue.
