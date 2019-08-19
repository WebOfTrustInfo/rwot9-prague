# Gently introducing DIDs to the Mastodon/ActivityPub Fediverse

by [Paul Fuxjaeger](https://twitter.com/fuxjaeger), [Michael Pimmer](http://michael.pimmer.info/about/) and [Markus Sabadello](https://danubetech.com/about.html) 

Our goal is to bring self sovereign identity concepts to the current ActivityPub fediverse as soon and as securely as possible.

The hypothesis behind that goal is that long term stability of a federated service crucially depends on persistent trust relations across all participants (developers, admins, users) that are not *distorted* by the implicit hierarchical structure of a centralized reference system, such as DNS.


## Context:

The application of DIDs within ActivityPub based services has already been sketched by Christopher Lemmer-Webber (co-auther of ActivityPub) back at RWoT5:

> ActivityPub implementations at the present moment rely on HTTPS as their transport, which in turn relies on two centralized systems: DNS and SSL certificate authorities. Is there any way to bring self-sovereignty to the federated social web?

> https://github.com/WebOfTrustInfo/rwot5-boston/blob/master/topics-and-advance-readings/activitypub-decentralized-distributed.md

It demonstrated the feasiblity and power of this new combination. 

But it left us wondering how to turn this into reality - how to change the base reference system of a large federated network, e.g. within the current mastodon fediverse?

## Augmenting The Fediverse

Instead of a radical approach we would like to propose to gradually introduce DIDs to Mastodon/ActivityPub in a backwards compatible manner:

1) **DNS-based actorIDs are kept as primary reference**
2) **Users are enbabled to attach DIDs to their actor object and exchange them in a structured way**
3) **Conflicts between DID/DNS reference are resolved at the receiving end, based on a generic decision logic that minimizes attack surface**

So, we start by allowing actors to attach DIDs to the actor object:

```
{"@context": "https://www.w3.org/ns/activitystreams",
     "type": "Person",
     "id": "https://social.example/alyssa/",
     "name": "Alyssa P. Hacker",
     "preferredUsername": "alyssa",
     "summary": "Lisp enthusiast hailing from MIT",  
-->  "also_known_as": ["did:sov:123hsf456dfg", "alyssa@old-server"],
     "inbox": "https://social.example/alyssa/inbox/",
     "outbox": "https://social.example/alyssa/outbox/",
     "followers": "https://social.example/alyssa/followers/",
     "following": "https://social.example/alyssa/following/",
     "liked": "https://social.example/alyssa/liked/"}
```

What does that offer?

- **Verification of accounts**, [similar to keybase or blogs](https://github.com/tootsuite/mastodon/pull/10414) but free of a centralized authority.
- **Persistence & discoverability**
  - DIDs are built to persist - they could live longer than DNS service endpoints or the first mastodon accounts/servers, by pointing the DID document to a new account (the DID always stays the same, even when service pointers change)
  - DIDs can be used to exchange contact information and point to various services/accounts like a mastodon account: https://uniresolver.io/#did:sov:builder:9xsh5imsp9UMVbsX4sn2Cz
- **Migration of accounts**: already partly solved without DIDs, but DIDs could be an additional trigger for a 'move' activity that even works when the old server is not available anymore https://github.com/tootsuite/mastodon/issues/177#issuecomment-455547349

## Technical considerations
### Multiple DIDs
We plan to allow using multiple DIDs to support multi-source identities. When a `move` activity can be triggered by a DID, such a change could also be triggered by a malicious server operator who introduces a DID to an actor object and then changes the DID Document. In some cases it might be necessary for Followers to decide how to react to a DID change:

![](topics-and-advance-readings/media/fediverse-did-integration.png)

### Using `also_known_as`
The `also_known_as` attribute is used for the ´move´ activity, pointing to an old actor object. These entries are not DIDs and will thus not interfere.

### Cooldown Periods
To avoid server/network overloads, the cooldown periods applied on Mastodons `move` activity should be followed when triggering a move by a DID document change, too.
