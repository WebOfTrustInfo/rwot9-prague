Why we must ask the Why of Identity
===========================

By Ian Grigg &lt;iang@iang.org&gt;

Identity continues to be bedevilled by conflicting language and definitions of what should be simple and understandable terms. An understandable reaction to this is to define or catalogue the various terms, in the hope that confusion disappears and consensus emerges (Andrieu 2017)(Young 2019). Yet even this has not seemingly aided the sector.

Why is this? One possible cause is a focus on WHAT and HOW rather than WHY.  _“As engineers and system designers, we’re concerned with how things work.”_ (Andrieu 2018) For technical people this focus is admirable, but it leaves the WHY unsaid. _“These different perspectives are valid views of identity’s impact on our lives. More than valid. _Vital_.”_

Without a focus on WHY, we techies are left interpreting it from our own biases. An indicator of own-bias is the suggestion that our attempts to communicate with more accurate language and definitions should be inclusive. On the face of it, how can this be challenged? We are all in this together, and if we don’t work together, we’ll fail, right!?

Such a consensual approach should be obviously good, but I have a nagging doubt. When I formulated the 4 schools or types of identity (state, self, corporate, community), I was not thinking of _inclusion_, I was expressly intending to _exclude_ (Grigg 2015).

Why exclude? From my position, it is because many of the views or designs or schools or what-have-you are simply wrong. Let me be flagrant in explanation:

- I first came across Identity as a topic in 1992 with _pretty good privacy_ (PGP) and its _web of trust_ (WoT). Since then, I’ve spent 2 decades using it, building it, and being involved in its standardisation community. During that time, I had ample visibility over it, and for all its benefits, I never saw anything lived up to the rhetoric of _web of trust_. Which is no small critique as WoT was the magic that drew people in. So much so that by the end of the 2000s I had declared both WoT and PGP dead (to myself at least).

  Why did it fail? Because PGP does not standardise the semantics (meanings) of its links.

- Likewise its competitor _public key infrastructure_ (PKI), which does standardise the meaning of its links, was also dead. My visibility this time came from auditing a Certification Authority (Grigg 2008). The commercial industry of CAs is flawed because it does not allocate the liability correctly, and the consequence was that although it standardised its semantics, it did so at a zero level - semantically null. Its certificates were therefore worthless to a relying party in a legal context. So why bother? And few did.

-  Which led to building CAcert right - so it could do the job that PGP and PKI failed at, and do it properly and fairly.  Sadly, death also - the aspirations and efforts of a volunteer community were not enough to light the fire. CAcert was too large and too unwieldy, and it was not able to competitively shift with its changing fortunes, because it lacked an economic model to guide itself to the future.

We could talk about this for days, or write a book about it (Grigg 2016), but perhaps my point is clear:  many of these designs were simply flawed, and fatally so. If we are to move forward, it behooves to identify these failures, understand the WHY of their flaws and eliminate them.  Both the flaws and the WHY that led us to those flaws.

Therefore when I struck on an inspiration of these four different ways of seeing identity, I was not inspired at all by inclusivity, I was expressly trying to be exclusive:

**(1) The state** - has a hierarchical process that is deeply constrained by legal, constitutional, political and historical restrictions. It can only build something of minimal nature, and only for a clear and unchallengeable purpose. Therefore the state’s identity system - passports, identity cards - typically supports itself, the state, and anyone else is incidental and unsupported. This fundamental flaw means that the people always come second, either as subjects or reliers. For crude example, it doesn’t work across borders, because the state is only concerned within its own borders! It is therefore fundamentally a poor fit for a future borderless Internet Identity concept. Excluded!

**(2) Our Self** - is the core and root of what we think of as identity. At a definitional level, computer scientists have stolen the term and misused it, which means that all ordinary mortals will be confused by this mangling, resulting in that modern oxymoron “your identity has been stolen.” In that basic conflict the individual rejects the system even as the liable party rejects the liability. But more fundamentally, people don’t want their very self to be part of someone else’s system; the privacy of our minds is integral to our sense of self, and to have anyone pretend to have our identity in their system is an insult so deep we can’t explain it. Our upbringing as identity-as-self is fundamentally at odds with the notion of a system controlled by others. And such a system must therefore be excluded, even if it only means using a better term.

**(3) Corporates** - as is now obvious the big social media and sales corps step into the gap not inhabitable by the state, and collect vast reams of all data on everyone. In contrast to the restrictions that forces the state to undersell its system, the corporates oversell. Both happiness and fear in turn, as long as a buck can be made, resulting in the slow and steady corruption of people as individuals, turning us into farm animals. It isn’t hard to exclude this approach.

**(4)** Finally, we arrive at **community** identity:  we are who our friends and peers think of us. This is a difficult notion too, as we face technical challenges in data collection, providence, privacy and security. As well societal challenges such as size, discrimination and power. But this school unlike the others doesn’t exclude itself. It is possible to collect that information, it is possible to protect it, and possible to use it, once protected.

My purpose in constructing this simple list was informed by some 30 years observing the world of identity. There is abundant information on why a lot of it is plain bad. I suggest it is necessary to avoid the errors of the past, and that only happens when we recognise the errors of the past and put our foot down:  Exclude!

This is also a discussion on WHY:  why are these approaches wrong? If so we need to exclude them. Why is an approach based on community and relationships right? Or, recognising the difficulties inherent in such a proposal, why is it plausible, and representing of fertile ground?

Which allows me to close on my original point - without a strong narrative as to WHY, we are ungrounded. It doesn’t help to know HOW to build it if our foundations are sand. The castle of Identity, to be of any use whatsoever, must be founded on the strongest rock of understanding, of WHY, for it to survive even the first squall let alone a war.



----
(Andrieu 2018) Joe Andrieu, “A Primer on Functional Identity,” RWOT9-prague??? https://github.com/WebOfTrustInfo/rwot9-prague/blob/master/topics-and-advance-readings/functional-identity-primer.md  
(Andrieu 2017) Joe Andrieu, “Five Mental Models of Identity,” RWOT7-toronto https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/mental-models.md  
(Grigg 2008) Ian Grigg, “An Open Audit of an Open Certification Authority,” 22nd Large Installation Systems Administration Conference (LISA 2008).  
(Grigg 2015) Ian Grigg, “Identity,” Robin Hood Coop London Open Office, 2015 https://www.youtube.com/watch?v=2ITif1OBVX8  
(Grigg 2016) Ian Grigg, “My Identity,” Identity Cycle, 2016-. forthcoming  
(Young 2018) Kaliya Young, “The Domains of Identity,” https://identitywoman.net/domains-of-identity/  
