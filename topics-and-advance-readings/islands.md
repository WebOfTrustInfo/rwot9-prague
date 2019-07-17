# Islands, Tigers, and Bears, Oh My!
Daniel C. Burnett

## Is there a risk of VC islands?

The [Verifiable Credentials Data Model specification](https://w3c.github.io/vc-data-model/) was specifically designed to allow for JSON-based credentials that
1. could be, but need not be, JSON-LD
2. could use JSON-LD proof formats
3. could use JWT signatures (JWS)
4. could use zero knowledge proof systems

Many of the properties in VCs are optional, and of the ones that are mandatory there is often flexibility in how they can be used.  It is very likely that credentials written assuming use of JSON-LD for vocabularies and semantics will have semantics that basic JSON processors will ignore.  It is likely that VCs using zero knowledge proofs will be unverifiable by processors that do not understand zero knowledge proofs.  In short, the syntax is generic enough to support all these options, but it is NOT the case that every VC in existence will be verifiable, or even understandable without verification, by every processor.

This leads to a question that has frequently arisen in the VCWG:  what level of interoperability can we expect, and is there a risk of the VC ecosystem devolving into islands of incompatible VCs?

In short, the answer is yes.


## If so, does it matter?

Here's where the discussion gets interesting.  The federation argument says that without universal interop there is no value.  This argument was used around another W3C standard, WebRTC, where some in the community believed that true peer-to-peer communication, without federated identity, would be useless.  However, this has turned out not to be necessary for most use cases.  The same thing may be true here.  A VC ecosystem essentially requires only pairwise trust; this is the value of the approach, that no global, centralized credentialing system is needed.


## If it does, what can/should we do about it?

One could counter the pairwise trust argument by pointing out that credentials using one proof format, for example, can still only be used by processors that support that format, encouraging a marketplace race for dominance of one format over another.  This may yet happen.

The question for this paper, and for RWOT, is what, if anything, can or should be done about it?  Stopping it is difficult, so one possibility is to consider ways to enable easy conversion from one format to another, or to enable low-cost converters.  But is that the only possibility?
