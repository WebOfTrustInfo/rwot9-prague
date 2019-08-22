
# Keeping Unwanted Messages off the Fediverse

## Table of Contents

1.  [Introduction](#orga7bd774)
2.  [ActivityPub Overview](#orgb21f688)
3.  [The Fediverse Today and Unwanted Messages](#org2158b95)
4.  [Proposed Suggestions](#org0327ae3)
    1.  [Mandatory Activity and Object Validation](#org6d76115)
    2.  [HTTP Signature Validation](#org2aecaba)
    3.  [Enhanced Privacy of Followers/Following Collection](#org68b0152)
    4.  [Strict Protocol Adherence](#orga345a07)
    5.  [Object-Capabilities Based Inboxes](#orgba8ad07)
    6.  [MultiBox](#org7937fed)
    7.  [Multiple Inboxes/Message Sorting](#org179021c)
    8.  [Sender Identification and Pet Names](#org5dbdd7f)
    9.  [Blacklists](#orgdc263ce)
    10. [Closing the Relay Hole](#org50fef34)
    11. [Content Based Filtering](#orga2680be)
    12. [Whitelists](#orgdc8155b)
    13. [Message Flagging/Sorting](#orgfbb0657)
    14. [Postage](#org6988e08)
    15. [Bounce Messages](#org3370488)
    16. [Promises](#org0983769)
5.  [Combining Techniques](#orge48a42e)
6.  [A Note for ActivityPub Node Operators](#org9339e40)
7.  [Conclusion](#orgde4153c)



<a id="orga7bd774"></a>

# Introduction

Unwanted messages are a challenge for all public communication systems. On a
federated network without a central form of control, the challenge is extended
to allowing for free communication between parties without a central means of
control while at the same time preventing undesired or harmful messages.

ActivityPub<sup><a id="fnr.1" class="footref" href="#fn.1">1</a></sup> is a W3C standard protocol designed to facilitate social
networks. The aggregate name for systems that use the ActivityPub is the
Fediverse. As of the time of publication, there are approximately three million
user accounts on the Fediverse spread across approximately 5,400 nodes.<sup><a id="fnr.2" class="footref" href="#fn.2">2</a></sup>
Despite this large number, unwanted messages have not yet become a widespread
problem. It seems inevitable that given the size and breath of the Fediverse,
along with its decentralized architecture that the introduction of unwanted
messages is inevitable.

What exactly constitutes unwanted messages will vary from person and community
but we generally feel these messages fall into one or more of the following
categories: Unsolicited commercial messages (spam), messages designed to commit
fraud (scams, phishing), messages designed to harm or inflame (trolling),
messages designed to harm, intimidate or coerce (bullying), abusive or
threatening speech against a particular group (hate speech), messages
containing deliberate disinformation (fake news), or messages of an
inappropriate nature for community standards (eg violence or pornography). We
do not define these terms further nor do we believe in a universal enforcement
of any one set of community standards, instead we rely on each node and
community to define these standards for themselves.

The techniques described in this paper are generalized and could be used across
multiple domains of messages, regardless of content or whether the messages are
meant for a public or private audience.


<a id="orgb21f688"></a>

# ActivityPub Overview

ActivityPub is an HTTP based messaging system that allows for seamless cross
server communication (aka federation). In ActivityPub, individual accounts
called `Actors` are addressed by unique URN identifiers. Messages between
Actors are serialized using an extension of the Activity Streams
specification<sup><a id="fnr.3" class="footref" href="#fn.3">3</a></sup>. These messages are called Activities. Each Activity is
composed of three parts:: The `Actor` originating the Activity, an `Activity
Type` representing the action being taken and an `Object`. Objects are the core
type in ActivityPub and may represent any noun in the system. Activities and
Objects are referenced by URN as unique identifiers. Activities also have an
audience field, which is a list of Actors which should have access to the
Activity.

Actor to Actor communication vaguely resembles email. Each `Actor`'s URN
resolved to their `Actor Object` which specifies that messages destined to a
specific Actor be delivered to its `Inbox`, a URN that is meant to receive such
messages from external parties. ActivityPub also specifies an `Outbox` where
outgoing messages are posted in a manner similar to RSS/Atom feeds, but using
the Activity Streams vocabulary and reliant on authentication to ensure
messages are only seen by those who have authority to do so. In addition to
these delivery mechanisms, ActivityPub also specifies an optional `sharedInbox`
where either multiple actors may be listed explicitly or where messages to
multiple recipients may be interpreted by the receiving server implicitly.

While not directly part of the standard, HTTP Signatures<sup><a id="fnr.4" class="footref" href="#fn.4">4</a></sup> are most
commonly used with ActivityPub as the authentication mechanism. Actors have a
generated keypair and their public keys are displayed on the aforementioned
Actor Object. Requests made on behalf of that actor are then signed using the
Actor's private key and may be verified against its public key.


<a id="org2158b95"></a>

# The Fediverse Today and Unwanted Messages


<a id="org0327ae3"></a>

# Proposed Suggestions


<a id="org6d76115"></a>

## Mandatory Activity and Object Validation

The ActivityPub standard itself provides only basic guidelines into validation
of messages but does recommend verifying external objects and activities as a
base minimum mechanism against spoofed messages.<sup><a id="fnr.5" class="footref" href="#fn.5">5</a></sup> Based on anecdotes from
operators on the Fediverse, this technique alone has been effective in either
the case of spoofed messages or the case where an account has been created,
sends messages and is then shut down for abuse. In either case, we recommend
that all ActivityPub implementations validate Activities and Objects in order
to eliminate this unwanted message vector.


<a id="org2aecaba"></a>

## HTTP Signature Validation

The HTTP Signatures extension, while not officially part of the ActivityPub
standard has been acting as a de-facto standard for authentication on the
Fediverse. We recommend that unless and until another authentication mechanism
offering the same benefits as HTTP Signatures becomes available and generally
adopted that HTTP Signatures be implemented in ActivityPub software and HTTP
Signature validation of messages should then be assumed.


<a id="org68b0152"></a>

## Enhanced Privacy of Followers/Following Collection

One of the tools of spammers is to collect as many contacts as possible. For a
sophisticated attacker, the connections between contacts could be used to
violate someone's privacy or as part of a sophisticated phishing or scamming
attempt. Due to these and other concerns over sensitive information leaking to
third parties, we suggest that `Followers` and `Following` collections not
generally be made public. Instead, such private information should either never
be disclosed to a third party or only be disclosed insofar as it related to the
actor making the request.


<a id="orga345a07"></a>

## Strict Protocol Adherence

Postel's law states that a protocol implementer should be strict in what they
send and liberal in what they accept.<sup><a id="fnr.6" class="footref" href="#fn.6">6</a></sup>. At the same time, email operators
have found that many spammers' servers do not adhere strictly to the SMTP
protocol. As an example, many mail servers lack a Forward-Confirmed Reverse DNS
record<sup><a id="fnr.7" class="footref" href="#fn.7">7</a></sup> or send a HELO/EHLO that is not a fully qualified domain name or
does not match the sender<sup><a id="fnr.8" class="footref" href="#fn.8">8</a></sup>. Many such servers also lack the ability to
retry messages in the case of temporary failure, a situation that is utilized
in greylisting<sup><a id="fnr.9" class="footref" href="#fn.9">9</a></sup>. Because of this pattern of non-compliance, one common
technique to reduce spam in email is to find the areas of the protocol that are
commonly skipped by spammers and either block access or restrict access based
on non-compliance.

It remains an open question on whether ActivityPub operator should take the
same approach regarding federating with other ActivityPub servers. We do not
believe that at this time such an approach is necessary or desirable. The
approach of being strict in what one accepts from other servers was born out of
necessity by email operators who found correlations between poor
implementations and unwanted messages. While these correlations are undeniable,
they are not causal nor directly associated except in that requiring strict
adherence raised the bar for all email administrators, making it more
challenging to run a mail server. Especially as it relates to PTR records, this
prevented anyone who was not directly in a business relationship with their
upstream provider to be able to operate a mail server. We do not believe that
all ActivityPub servers should be required to keep to such strict standards.
Nonetheless, we mention this method because it has been so effective in email,
and thus may be something to evaluate again in the future.


<a id="orgba8ad07"></a>

## Object-Capabilities Based Inboxes

As per the ActivityPub specification, every `Actor` is required to have an
associated `Inbox`. In most ActivityPub implementations, an Actor's inbox is
simply a URL endpoint specific to the actor, e.g.
`https://example.com/bob/inbox`. While convenient, we propose that servers
should be using Object Capabilities model by which Inboxes are a capability
handed out by a server.

Without delving too far into the theory of object capabilities, we can imagine
that the ability to send a message from one Actor to another is an action that
we can grant explicit access to similarly to the way that access is granted to
an API in a computer system. In order to be able to send a message to the
recipient, the recipient must first provide the sender with a *capability* to
do so. This capability can be represented as a long randomly generated string.
Its length and randomness make it impractical to guess and thus (in OCAP
parlance) unforgeable.

This act of the sender handing out capabilities may be done in a number of
 ways, though we suggest that offering a new Inbox could be performed as a new
 Activity, for example:

    {"@context": "...",
     "type": "Inbox",
     "to": ["https://chatty.example/ben/"],
     "attributedTo": "https://social.example/alyssa/",
     "preferredInbox ["https://social.example/dbgxpggrez", "https://social.example/ptmihemlzj"]

In our example, we show multiple inboxes being offered. As part of the Object
Capabilities model, these capabilities are transferable, which would allow one
actor to send an inbox capability to another actor, for example in a situation
where the recipient is a trusted party.

If one Inbox becomes abused, we are able to trace back to exactly when and for
who the Inbox was generated. We are also able to revoke the Inbox, stopping any
future requests to it. An HTTP request sent to an expired Inbox should ideally
result in an HTTP 410 (Gone)<sup><a id="fnr.10" class="footref" href="#fn.10">10</a></sup>, alerting the sending to the unavailability
of the inbox and prompting it to request a new one if it wishes to resume
communication.

The OCAP Inbox model as described in this proposal would require little or no
changes to existing deployed ActivityPub servers. In the case where an
implementation does not understand the new Inbox being offered, they would
continue to go through a "Default Inbox" route.


<a id="org7937fed"></a>

## MultiBox

`Shared Inbox`<sup><a id="fnr.11" class="footref" href="#fn.11">11</a></sup> provides the ability for server to server communication
traffic to be reduced from R requests, where R is the number of recipients, to
a single HTTP request. This is a desirable property as it reduces the amount of
HTTP round trips for both the sender and receiver. Unfortunately the design of
Shared Inboxes as described in the ActivityPub specification makes it very easy
for a spammer to abuse the system by not requiring explicit delivery
recipients. We propose an alternative to Shared Inbox called MultiBox that
keeps the desirable properties of Shared Inbox while protecting against
scenarios in which the sender uses Shared Inbox to "spam" a server.

Like Shared Inbox, MultiBox consists of a single HTTP endpoint for multiple
Actors. Unlike Shared Inbox, in a MultiBox request, each recipient is
explicitly listed *by Inbox*, requiring both the knowledge of the Actor and a
corresponding Inbox for that actor. This information is transmitted through the
use of an HTTP header `Audience` where each Inbox is listed using comma
separated values<sup><a id="fnr.12" class="footref" href="#fn.12">12</a></sup>.

This has two advantages over Shared Inbox. Used on its own, it eliminates the
vulnerability mentioned previously whereby recipients to a message do not need
to be listed. If this proposal is adopted alongside the Object-Capabilities
Based Inbox proposal ([4.5](#orgba8ad07)), the
advantages multiply as we also gain the ability to appropriately filter
incoming messages according to the criteria set out by the specific Inboxes, as
well as letting us know the origin of each Inbox.

For the sender, the additional computing resources required to send a MultiBox
request are minimal, but doing so would make mass-messages expensive for
senders wishing to abuse the system.

One open question on this proposal is that if we use the HTTP header `Audience`
to store the list of recipients, this may result in a limitation. HTTP header
sizes are not explicitly capped at the protocol level but implementations often
cap them at different lengths- 4Kb for the Nginx web server or 8Kb for Apache.

This would limit the number of per message recipients, though this limitation
 would rarely be reached. An alternative to this proposal would be a new
 `MultiBox` object encapsulating the `Audience` field and the ~Activity.


<a id="org179021c"></a>

## Multiple Inboxes/Message Sorting

The ActivityPub protocol specifies an `Inbox` collection<sup><a id="fnr.13" class="footref" href="#fn.13">13</a></sup> to store
incoming messages for the Actor. This functions similarly to the common Email
Inbox where by default, messages arrive. As thinking regarding email has
evolved, automatic message sorting has been employed using either actual
folders or tagging mechanisms. These same techniques could be applied to
ActivityPub, whereby a message could be placed in an Inbox collection
corresponding to sorting rules.

This extension to the ActivityPub protocol would not have to be visible to any
external entities (ie not accessible through the Server-To-Server
communication) but only through the Client to Server (C2S) communication
protocol dictated in the ActivityPub standard.<sup><a id="fnr.14" class="footref" href="#fn.14">14</a></sup>

A variety of techniques could be employed when sorting messages, including but
not limited to the content based filtering techniques described in previous
sections about filtering based on message content ([4.11](#orga2680be)) or
using OCAP Inboxes ([4.5](#orgba8ad07)) described in this
whitepaper.


<a id="org5dbdd7f"></a>

## Sender Identification and Pet Names

One of the most critical components of reducing unwanted messages is the
identification of the sender of a message. Without verification, a sender may
use their ability to impersonate someone else for a number of purposes, from
spamming, to bypassing security or scamming, often referred to in the
literature as either *Joe Jobbing* or *Phishing*.

In Email, verification is largely achieved by verifying that the email server
is trusted for the domain which it purports to deliver email, often through an
out of band technique, often involving DNS, such as SPF<sup><a id="fnr.15" class="footref" href="#fn.15">15</a></sup> or DKIM<sup><a id="fnr.16" class="footref" href="#fn.16">16</a></sup>.

In ActivityPub, sender identification is performed at the Actor level using the
HTTP Signatures.<sup><a id="fnr.4.100" class="footref" href="#fn.4">4</a></sup> With this extension, each Actor has a public and private
keypair. The public key of an Actor may be retrieved by retrieving its Actor
Object, a JSON-LD object retrievable by HTTP. Since ActivityPub requires Actor
object lookups as part of normal message deliver, this is adds only a minimal
amount of additional work on the receiver's part. Each message sent on behalf
of an Actor is signed at the HTTP level by this key, which can then be verified
by the receiving server for authenticity.

We propose to extend this validation with a second layer of identity validation
through the use of Pet Names. The Pet Names proposal presented in Rebooting Web
of Trust 2018<sup><a id="fnr.17" class="footref" href="#fn.17">17</a></sup> has a secondary property of being able to be used as
simplified trust mechanism. When a sender would like to make contact with a
receiver, the receiver checks its neighbors (Followers or Following) for a pet
name for this sender. If a neighbor has decided to give this sender a Pet Name,
then we know that there is some level of communication between them, thereby
indicating that the communication is more likely to be useful.

We recognize that this proposal may seem in contrast to the previous proposal
of not disclosing connections to third parties as described in the section on
improving privacy of Follower/Following Collections ([4.3](#org68b0152)), but the two can operate in tandem by making
the ability to find a connection to your followers be a query, rather than a
publicly available list. We could further enhance the security of this by
adding additional restrictions onto the query functionality such as rate
limiting queries.

We further recognize that this is not a full Web of Trust system in that webs
of trust extend beyond one hop. It would be possible do so here as well, but we
believe that this would require further examination in order to be done in a
way that protects a user's social graph.


<a id="orgdc263ce"></a>

## Blacklists

A blacklist is a list or searchable collection of entities which should be
distrusted. Blacklists are widely used by many email administrators to prevent
email originating from one or more types of sources that they distrust, such as
mail servers residing on consumer grade Internet connections or mail servers
that have been known to send spam recently.

In ActivityPub an individual Actor or server administrator may choose to create
a custom blocklist, but there is currently no standardized way to distribute or
share blocklists. We propose that this be explored further, though cautiously
by allowing Actors to query each other's either mute or block lists through a
mechanism similar to the proposal described in the section on Pet Names ([4.8](#org5dbdd7f)).

Actors who have agreed to peer with each other in regards to shared mute or
block lists will be given an additional property in their actor object
corresponding to a query endpoint for their blocklists, thus creating
functionality where these lists can be shared between actors. These blocklists
may contain either actor level or server level bans, and could additionally be
shared between server administrators.

We believe that while blocklists may be effective in addressing some types of
unwanted messages, particularly offensive speech, that they carry with them a
number of caveats that give us pause in wholeheartedly endorsing this
mechanism.

Firstly, should a malicious party gain access to a blocklist, this could
potentially create a situation in the originator would be made a target for
attack. We believe that using a query service, rather than a list, mitigates
this concern somewhat, but it would be possible for an a malicious party to
covertly build up such a list and use it to create a list of targets.

Secondly, we are concerned that the transitive properties of block lists may
have unintended consequences or be used as a vector for attack or denial of
service. If services adopt each other's blocklists without review, they may
miss out on messages that they might wish to recieve. The analogy of adblocking
software is often used by those supporting this type of proposal, but in
ad-blocking, it is possible to disable the software selectively when the
functionality of a website does not work. With blocklists, unless they are
paired with another proposal, such as the one about multiple inboxes ([4.7](#org179021c)), they may have the consequence of breaking federation.

Thirdly, the mechanism described precludes the ability to easily remove a
block. If a block is removed, there is no mechanism that allows those who have
previously queried the blocklist to be notified. This problem is made worse if
blocklists are transitive. It would be possible to replace a query based
mechanism with a subscription based mechanism, but doing so would be subject to
the concern raised previously about blocklists being used to target
individuals.

While we believe blocklists may be an effective strategy to block some types of
unwanted messages, unless we can address the concerns raised above, we cannot
endorse their deployment.


<a id="org50fef34"></a>

## Closing the Relay Hole

Message Relaying involves sending a a message on behalf of another entity.
Message relaying is common in Store-and-Forward network designs. In Email, it
was common for servers to be offline some or most of the time, requiring that
other servers acted as relays, either sending or accepting mail on their behalf
cooperatively. In time, spammers began abusing these servers in order to send
messages on their behalf. Because of this, many mail servers block "Open Mail
Relays".

In ActivityPub, message relaying is performed in accordance with Section 7.1.2
of the ActivityPub specification<sup><a id="fnr.12.100" class="footref" href="#fn.12">12</a></sup> in order to mitigate the "Ghost Replies"
problem, where a rely to a message is not seen by everyone watching that thread
because the replier does not send the message to everyone that the original
sender did. Unfortunately this also opens up replies as a vector of abuse in
that a malicious sender may simply reply to an existing message, at which point
the sender of the original message will relay the reply to all their Followers
and any other audience of message. We suggest two methods to address this
problem, one using traditional Access Control Lists and the other using the
Object Capabilities Inbox proposal.

An Access Control Method solution would allow for the recipient of a
`inReplyTo` activity to be presented with a moderator queue of Activities in
reply to their own, which they then may act on. If they accept the reply, the
recipient will then send messages on behalf of the sender to their Followers.
The recipient Actor may also decide on a policy regarding future replies from
the same actor. For example, they may decide that future messages from that
Actor need not be moderated, effectively granting them access to the relay
functionality.

An alternative method using the OCAP model would be to treat replies as a
capability provided to by some Inboxes. An Actor who is then granted access to
reply without moderation is given a new Inbox corresponding to this added
capability.


<a id="orga2680be"></a>

## Content Based Filtering

While the other methods of message filtering address external signifiers of
unwanted messages, content-based filtering looks directly at content of the
messages themselves, either by lists of common terms found in unwanted
messages, by evaluating the probability of messages being unwanted or by
looking for other signifiers such as messages that appear to be phishing
attempts.

Content based filtering can take many forms, from simple rule based filters, to
Baysean text analysis<sup><a id="fnr.18" class="footref" href="#fn.18">18</a></sup>, sentiment analysis or even more complex image
classification.

An exciting area of further exploration may be the use of Federated
Learning<sup><a id="fnr.19" class="footref" href="#fn.19">19</a></sup>, whereby training can be performed in a way that allows
individual data to be kept private but the results may be shared and built
upon.

We offer no specific technique or method for this suggestion but do think that
the benefits of existing "theme based" ActivityPub services may be beneficial
in creating training models that work well based on community standards of
interest and behavior.


<a id="orgdc8155b"></a>

## Whitelists

Another approach to handling unwanted messages is the use of whitelists.
Whitelists as used in email most often simply bypass other measures when the
sender identifies themselves as an entity on the whitelist. Whitelists in email
are almost always a result of missclassification of messages as spam. While
this may have applicability on the Actor level, we believe that the use of
server whitelists in ActivityPub should be limited.

Whitelists have been proposed on the ActivityPub Fediverse as a means of
ensuring that mutual agreements between nodes are enforced. This approach is
akin to an email provider that only explicitly allows messages from large well
known organizations, for example by Google or Hotmail, and does not allow them
from anyone else, including Universities or Non-Profits.

Such whitelists are difficult to curate and more importantly, break the spirit
of communication that as at the heart of the protocol.


<a id="orgfbb0657"></a>

## Message Flagging/Sorting

A simple approach to the issue of unwanted messages is to mark suspicious
messages as such and place them outside of the normal message retrieval- either
in a separate Inbox (eg a Spam Folder) or on another system altogether in
"Quarantine". These same principles could be applied to ActivityPub by
extending a single Inbox to multiple incoming Collections, each containing
some subset of messages based on multiple analysis.

Such collections could be presented to the end user in a number of ways, using
the analogy of Tagging or directly as separate collections. We believe that
separating out the collections has a secondary benefit of allowing the
individual user to be prepared for either irrelevant or offensive content. For
example, an Inbox collection labeled "Warning" may allow for sufficient
emotional distance from the content such that even if a message is offensive
that it could be handled more easily, or possibly allowing those messages to be
screened further.


<a id="org6988e08"></a>

## Postage

All techniques used to identify and either block or sort unwanted messages
exist because there are costs in handling such messages. These costs are
bandwidth, electricity and storage, but also our valuable time and mental
health. Rather than create techniques that place even greater cost on the
receiver, it is possible to assign a cost value of sending messages to the
sender.

By requiring that the sender pay a cost, we shift the decision of whether or
not a message is worth sending to the sender. rather than the recipient. As is
shown by physical "Junk Mail", this does not necessarily eliminate all unwanted
messages, but it does reduce incentive. The fee of sending messages could be
paid in any number of ways, from systems such as with Hashcash<sup><a id="fnr.20" class="footref" href="#fn.20">20</a></sup>, paid
with digital currency, or part of another system, such as requiring a sender to
perform computational or storage tasks on behalf of the sender.

Requiring the message sender to expend resources in terms of either work or
currency has a number of benefits in reducing the incentive to send unwanted
messages, we would encourage that implementers of this idea be focused on
"fees" that that directly benefit the receiver. While proof of work systems
like Hashcash are easy to implement, without adding a direct benefit to the
receiver, they require the sender to expend resources. If extrapolated to a
large scale, this could have a negative environmental impact due to wasted
computing resources.

The issues around "real currency" are far more complex. Issuing a postage fee
based in actual currency more accurately reflects the cost of handling incoming
spam and by virtue of requiring actual money, makes sending out mass
solicitation or scambait email more costly. At the same time, by virtue of cost
of living differences any form of fee whether paid directly or indirectly, will
have a correspondingly different financial impact with greater proportional
cost born by those in poorer countries.

Because of these concerns and the spirit of free communication, we would
encourage any implementation of this technique to be used sparingly and only on
the first message of a new sender, rather than on all messages.


<a id="org3370488"></a>

## Bounce Messages

The ActivityPub specification does not address a situation in which messages
are rejected. While not strictly necessary, providing bounce messages does
allow for well meaning server administrators to have an understanding of why
their users' messages are not being delivered. We recommend an extension of the
HTTP status codes to include a new "Not Accepted" status code representing the
receipt of a request that is properly formatted but not accepted by the server
by a reason not covered by one of the other methods. A textual or JSON
representation of the full error message could then be provided to the HTTP
client, allowing an ActivityPub server administrator the opportunity to see why
messages are failing and take appropriate action.


<a id="org0983769"></a>

## Promises

Because many of the techniques discussed in this proposal are expensive to
perform, we suggest that in some cases a server may wish to handle the
processing of the message asynchronously and return a Promise representing the
status of message delivery which could then be queried at a later time to
determine if the message was delivered successfully or rejected.

These Promise statuses could use the same error codes as discussed in the
section on Bounce Messages ([4.15](#org3370488)) but not be required to keep the
HTTP connection open during the determination of message suitability.


<a id="orge48a42e"></a>

# Combining Techniques

As emphasized previously, the suggestions made in this proposal are meant to be
used in conjunction with one another for maximum efficacy. For example,
MultiBox used in conjunction with Object Capabilities Inboxes allows for
per-Actor filtering to be performed more easily. OCAP Inboxes may also be
granted which allow a sender to bypass other filters, acting effectively as an
Actor Whitelist, whereas a "Default Inbox" may require a postage fee. We
explored ACL vs OCAP inReplyTo functionality in [4.10](#org50fef34), and
either of these techniques could be combined with content analysis.


<a id="org9339e40"></a>

# A Note for ActivityPub Node Operators

During the research for this paper, the author asked ActivityPub node operators
what their experiences were with spammers and we received information that
spammers were signing up for accounts on nodes. This presents a challenge to
all parties involved.

Many of the techniques in this document have been optimized for a scenario in
which a spammer is operating their own servers. Understanding that spammers are
attempting to use existing nodes makes the situation for those node operators
more challenging as blocks may apply to an entire node. Therefore it becomes
imperative for those who run nodes on the Fediverse to do their best not only
to block incoming messages but to monitor their nodes for abusive behavior by
their users.

We have not addressed this issue in this paper but believe that the topic
deserves further research.


<a id="orgde4153c"></a>

# Conclusion

In this paper, we have presented a number of techniques for keeping unwanted
messages off an ActivityPub server. As emphasized previously, the suggestions
made in this proposal are meant to be used in conjunction with one another for
maximum efficacy. For example, MultiBox used in conjunction with Object
Capabilities Inboxes allows for per-Actor filtering to be performed more
easily. OCAP Inboxes may also be granted which allow a sender to bypass other
filters, acting effectively as an Actor Whitelist, whereas a "Default Inbox"
may require a postage fee. We explored ACL vs OCAP inReplyTo functionality in
[4.10](#org50fef34), and either of these techniques could be combined with
content analysis.

We believe that the problem of unwanted messages is addressable and we look
forward to participating in building solutions.


# Footnotes

<sup><a id="fn.1" href="#fnr.1">1</a></sup> <https://www.w3.org/TR/activitypub/>

<sup><a id="fn.2" href="#fnr.2">2</a></sup> <https://the-federation.info/>

<sup><a id="fn.3" href="#fnr.3">3</a></sup> <https://www.w3.org/TR/activitystreams-core/>

<sup><a id="fn.4" href="#fnr.4">4</a></sup> <https://www.w3.org/wiki/SocialCG/ActivityPub/Authentication_Authorization#Signing_requests_using_HTTP_Signatures>

<sup><a id="fn.5" href="#fnr.5">5</a></sup> <https://www.w3.org/TR/activitypub/#obj>

<sup><a id="fn.6" href="#fnr.6">6</a></sup> <https://en.wikipedia.org/wiki/Robustness_principle>

<sup><a id="fn.7" href="#fnr.7">7</a></sup> <https://www.rfc-editor.org/std/std13.txt>

<sup><a id="fn.8" href="#fnr.8">8</a></sup> <https://tools.ietf.org/html/rfc5321>

<sup><a id="fn.9" href="#fnr.9">9</a></sup> <https://www.greylisting.org/>

<sup><a id="fn.10" href="#fnr.10">10</a></sup> <https://tools.ietf.org/html/rfc7231#section-6.5.9>

<sup><a id="fn.11" href="#fnr.11">11</a></sup> <https://www.w3.org/TR/activitypub/#shared-inbox-delivery>

<sup><a id="fn.12" href="#fnr.12">12</a></sup> <https://www.w3.org/TR/activitypub/#inbox-forwarding>

<sup><a id="fn.13" href="#fnr.13">13</a></sup> <https://www.w3.org/TR/activitypub/#inbox>

<sup><a id="fn.14" href="#fnr.14">14</a></sup> <https://www.w3.org/TR/activitypub/#client-to-server-interactions>

<sup><a id="fn.15" href="#fnr.15">15</a></sup> <http://www.openspf.org/>

<sup><a id="fn.16" href="#fnr.16">16</a></sup> <http://dkim.org/>

<sup><a id="fn.17" href="#fnr.17">17</a></sup> <https://github.com/cwebber/rebooting-the-web-of-trust-spring2018/blob/petnames/topics-and-advance-readings/petnames.md>

<sup><a id="fn.18" href="#fnr.18">18</a></sup> <http://www.paulgraham.com/spam.html>

<sup><a id="fn.19" href="#fnr.19">19</a></sup> <https://federated.withgoogle.com/>

<sup><a id="fn.20" href="#fnr.20">20</a></sup> <http://www.hashcash.org/>
