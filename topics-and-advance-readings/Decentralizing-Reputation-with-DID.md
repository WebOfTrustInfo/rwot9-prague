<span class="c5">RWOT9 Topic Paper - Decentralizing Reputation with DID</span>

<span class="c1">Adrian Gropper</span>

<span class="c1"></span>

<span class="c1">To scale decentralized commerce based on self-sovereign identity and decentralized identifiers we will need to provide a practical alternative to centralized reputation managers.</span>

<span class="c1"></span>

<span class="c1">Decentralization is a complex topic and the rubrics that will help formalize our community's approach to decentralization is work that’s just beginning. One way to evaluate decentralization is the absence of essential intermediaries in an otherwise peer-to-peer transaction by self-sovereign peers. For example, a Bitcoin payment between self-sovereign peers is decentralized only to the extent that there’s no practical opportunity for censorship by the miners. As another example, a message between two iPhone users as peers is decentralized only to the extent that Apple has no practical opportunity to censor the user that buys the iPhone. Even without a strict definition of “practical” these examples of decentralization are pretty convincing, but they depend on the peers already knowing each other in some sense.</span>

<span class="c1"></span>

<span>Decentralization is a more nuanced issue when the self-sovereign peers to the transaction are not yet clear.</span> <span class="c6">In the majority of economically valuable real world applications, such as a crypto exchange, dating, or medical referral, practicality currently requires centralized intermediaries to bring the peers together, to reduce the transaction cost, and to reduce the transaction risk.</span><span class="c1"> The transaction cost has traditionally been reduced by introducing a centralized intermediary as technology operator. This avoids lagging open standards and reduces the cost for the peers to operate self-sovereign technology to execute the transaction. However, as technology cost drops with Moore’s law and standards evolve, the transaction case for centralization becomes moot, leaving search and risk as practical barriers to decentralization.</span>

<span class="c1"></span>

<span class="c1">Search for a suitable peer and risk of transacting with that peer are related since a good search experience would consider risk as a major influence in the rankings. We are familiar with the practice of listing the number of comments associated with a particular product on Amazon as proxy for the risk that one might incur with a purchase transaction. The product’s or seller’s reputation, as a number between 1 and 5, is another important proxy for risk. In order to decentralize Amazon, Uber, or Airbnb and return their value to the peers in the transaction, we need to solve the reputation problem in a practical way.</span>

<span class="c1"></span>

<span class="c1">Reputation is highly contextual. My reputation as an Airbnb host has little to do with my reputation as a physician or my FICO score. To scale decentralized commerce based on self-sovereign identity and decentralized identifiers we will need to provide a practical alternative to centralized reputation managers. Lacking this, the market for self-sovereign identity will be small and restricted to niche applications.</span>

<span class="c1"></span>

<span class="c1">A decentralized reputation solution must provide context, a negligible increase in transaction costs, and high resistance to gaming by either the peers to a transaction or their competitors.</span>

<span class="c1"></span>

<span class="c1"></span>

<span>There are no current solutions to the decentralized reputation problem, but Colony</span> <span class="c0">[https://colony.io/whitepaper.pdf](https://www.google.com/url?q=https://colony.io/whitepaper.pdf&sa=D&ust=1565833964344000)</span><span class="c1"> might be a decent example of the state-of-the art. Context is provided at the level of governance entities called colonies. Transaction costs are managed by a combination of off-chain “reputation miners” and a CLNY token. Lastly, gaming is dealt with by the introduction of arbitrators and staking mechanisms that can respond to challenges within the community. Anyone interested in this topic would do well to read the parts of the Colony whitepaper that deal with reputation, sections 6 and 7 in particular. The complexity of their solution is daunting and it begs the question, what else can the SSI community do?</span>

<span class="c1"></span>

<span class="c1">One hint comes from a presentation at RWOT8 about zero-knowledge proofs. (I’d love to have a link to the slides.) ZKPs can protect the privacy of the peers while ensuring that contributors to the reputation score were actually involved in the transaction. This could solve some of the gaming issues but is unlikely to eliminate the need for arbitrators in many cases.</span>

<span class="c1"></span>

<span>Providing and scoping context in a decentralized way is a governance issue. For example, the scope of social credit scoring in China seems to be as broad as the Communist Party might want. The scope of FICO scores in the US is limited by law and governed by a tightly restricted set of private-sector registrars. The scope of Uber or Lyft reputation is governed by their business interests as competitors and mostly a trade secret. One natural way to scope reputation linked to SSI would be at the level of the search engine or directory. The governance entity that brings anonymous peers together based on their attributes and credentials might also supply the formula for calculating reputation when a transaction actually results from the match. The directory governance entity could also be held responsible for securing and posting the reputation results, possibly as a verifiable credential. The HIE of One Trustee self-sovereign technology stack includes support for decentralized governance of self-sovereign directories</span> <span class="c0">[https://dir.hieofone.org/](https://www.google.com/url?q=https://dir.hieofone.org/&sa=D&ust=1565833964345000)</span><span class="c1"> but has not yet implemented any reputation components.</span>

<span class="c1"></span>

<span class="c1">Lastly, the cost of managing reputation must be low relative to the value of the transaction. A medical referral could be worth $thousands and hours of research on the part of the patient. But the decision to allow that same medical record to be used for cancer research might be worth almost nothing and ideally would not require a minute’s thought by a patient depending on the reputation of the researcher. Decentralized solutions to cost reduction might include Merkelization (as in the Colony example) or sampling transactions for relatively expensive audits so that the cost and risk of cheating are aligned. This reputation linkage to the transaction value of a DID will be relevant to the business model and sustainability of almost all DID methods.</span>

<span class="c1"></span>

<span class="c1">In closing, it could be argued that reputation will be primary determinant of market success for a DID method. Once standardized, DIDs will be more or less a commodity and could even be considered a human right to be sponsored as essential infrastructure with negligible cost. Municipal broadband, cellular 911 service, and free postal delivery are potential examples. Competition among DID methods will then shift to secondary factors such as risk reduction and reputation will play a central role.</span>

<span class="c1"></span>

<span class="c5">Additional References</span>

<span>Ethereum and IPFS alternative to FICO  </span><span class="c0">[https://bloom.co/whitepaper.pdf](https://www.google.com/url?q=https://bloom.co/whitepaper.pdf&sa=D&ust=1565833964347000)</span><span class="c1"> </span>

<span class="c1"></span>

<span>NIST - A Taxonomic Approach to Understanding 1 Emerging Blockchain Identity 2 Management Systems</span> <span class="c0">[https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.07092019-draft.pdf](https://www.google.com/url?q=https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.07092019-draft.pdf&sa=D&ust=1565833964348000)</span><span class="c1"> </span>
