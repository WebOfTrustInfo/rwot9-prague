# Preventing Transferrability with ZKP-based Credentials

Daniel Hardman and Lovesh Harchandani

## Abstract

Some in the digital credential movement have claimed that ZKP-based credentials are inherently unsafe because they can be shared by a malicious holder. The reasoning is that ZKPs guarantee perfect anonymity, and are therefore transferable by simply sharing the link secret. This is a misunderstanding of how ZKP-based credentials work. In fact, ZKPs can provide the same sorts of transfer protections as any other type of credential.

## What is a ZKP?

"ZKP" is often used in digital credential circles without careful definition, and this leads to confusion. Here is how the concept of zero-knowledge proofs (ZKPs) was defined by its inventors:

>Zero-knowledge proofs are defined as those proofs that convey no additional knowledge other than the correctness of the proposition in question. (Goldwasser, Micali, Rackoff, "The knowledge complexity of interactive proof-systems", SIAM J. Comput., 18, 1989, pp. 186-208)

The wikipedia article summarizes the zero-knowledge property in a similar way:

>If the statement is true, no verifier learns anything other than the fact that the statement is true. (https://en.wikipedia.org/wiki/Zero-knowledge_proof, retrieved 29 July 2019)

In other words, a ZKP proves a statement or proposition without leaking anything extra.

The wikipedia article correctly notes that a “zero-knowledge proof of knowledge is a special case when the statement consists only of the fact that the prover possesses the secret information.” However, other parts of the wikipedia article conflate the more general ZKP concept with the more specific ZKP-of-K concept, and this conflation is common in other treatments of the topic online. This can lead to the assumption that ZKPs are only useful for proving predicates while hiding the identity of the prover and providing perfect repudiation. This is a mistake. ZKPs can prove other propositions besides the fact that the prover knows something. They are therefore NOT synonymous with anonymity. What defines a ZKP is its conformance to the exact need of the circumstances--leaking zero information beyond that line.

A proof of “over 21” is not zero-knowledge if the actual necessary proposition that needed proving was “over 18”--no matter what technique is used and what its mathematical guarantees might be. This is because 3 extra years of precision were leaked about the age.

A non-repudiable proof of “over 18” is zero-knowledge if (and only if) circumstances demand both “over 18” and non-repudiation. Proving in a non-repudiable way when repudiable would suffice leaks a signature that isn’t strictly required.

A proof that discloses Alice’s social security number is a ZKP if (and only if) the only fact that’s proved is the value of Alice’s social security number, and if that disclosure, and nothing more, was exactly what circumstances required.

The “over 18” use case is often mentioned as a convenient illustration of ZKP use, but what is proved in a ZKP-based credential ecosystem in that scenario is not a single fact. Instead, it approximates this:

```
I possess a credential A,
matching schema B,
containing field C,
where C contains a numeric value > 18,
and the credential contains a cryptographic commitment to a link secret D that I know,
and the credential has an revocation index, E, which I know,
  in revocation registry F,
and the credential’s status in F is unrevoked
and I know a signature G,
from issuer H,
endorsing that value C in the context of A, B, D, E, and F.
```

Notice that propositions D, E, and G are ZK proofs of knowledge; the rest are ZK proofs, but not ZK proofs of knowledge.

The remainder of this paper explores how the rich--not trivial--embodiment of ZKPs can prevent abuse by putting safeguards around improper transfer. These safeguards do not constitute an abandonment of the ZKP ethos; they simply satisfy additional constraints that fall within the scope of reasonable zero knowledge goals in various circumstances.

## Anonymity != Transferability

ZKP-based credential solutions have many options to add constraints to a proving interaction to adjust anonymity, vulnerability, and transferability. These techniques can be used together, as circumstances demand. The following list of 8 is only a sample.

#### Technique 1: Richly contextualized presentation requests

This technique appears first, not because it’s the most powerful in our arsenal, but because it’s so easy to implement, so frictionless for innocent actors, and so understandable for the non-technical.

Although a verifier may be interested in a single primary fact, they can require a ZKP to prove the existence of many auxiliary pieces of context around that fact, in a way that makes malicious sharing far more difficult or risky. For example, instead of just proving that a person holds a registered voter credential (the primary fact), the proof request could be:

>Prove you hold a registered voter credential, and that you also hold a driver’s license that has the same name on it, and that you also hold an unexpired credit card in that same name. 

Note that this richly contextualized presentation request doesn’t ask the user to reveal any extra attributes like a name from any credential, or a credit card number. It’s just asking to demonstrate the existence of unrevealed but linked context that an innocent holder would have.

By itself, this technique is not a panacea. If a voter registration is transferable, then other credentials could be, too. However, a richly contextualized presentation request increases the amount of material that must be shared to collude, and therefore the cost and friction of fraud. It also requires all the transferred information to be coherent and coordinated. A malicious Alice can’t buy 3 independent credentials to satisfy this request; she has to get all 3 from the same holder (same link secret). And such a request increases the stakes for transferring; now whoever shares credentials fraudulently with Alice must also be willing to let Alice spend their money by giving her control of their credit card.

Notice how the credit card makes the prover vulnerable in a way that human trust demands, but does so in a way that doesn't erode privacy. Colluders become vulnerable to each other rather than to the verifier. And notice that the vulnerability must only be potential, not actual, to enable trust. The verifier and the prover both know that it is only real if the prover is colluding. An innocent Alice is not vulnerable in any way--but the fact that she _would be vulnerable if she were malicious_ is enough to justify the verifier’s trust. 

#### Technique 2: Prevent Link Secret Reuse

It is possible for a verifier to detect that a link secret has been reused, and to reject a ZKP because of it, without knowing what the link secret value is. This could be used to preserve privacy while making it impossible to vote twice with the same ZKP credential--or to prevent a single driver’s license from admitting multiple teens to a restricted venue, for example.

A very sophisticated implementation of the technique is discussed in the “Clone Wars” paper mentioned in the [Further Reading section below](#appendix-further-reading). Among other things, it allows detection after n reuses in a given time period, where n is an arbitrary number > 1. A simpler variation of the technique is described here.

The normal way to prove possession (knowledge) of a link secret is to prove knowledge of committed messages in a vector Pedersen [Commitment](https://en.wikipedia.org/wiki/Commitment_scheme). PCs are of this form <var>g</var><sub>1</sub><sup>x</sup><var>g</var><sub>2</sub><sup>y</sup><var>g</var><sub>3</sub><sup>z</sup>.... and knowledge of <var>x</var>, <var>y</var> and <var>z</var> can be proved without revealing <var>x</var>, <var>y</var> or <var>z</var> (zero knowledge) by using [Sigma protocols](https://en.wikipedia.org/wiki/Proof_of_knowledge#Sigma_protocols). It is also possible to prove equality of committed messages in different commitments using these techniques. So given <var>g</var><sub>1</sub><sup>x</sup><var>g</var><sub>2</sub><sup>y</sup><var>g</var><sub>3</sub><sup>z</sup> and <var>h</var><sub>1</sub><sup>x</sup><var>h</var><sub>2</sub><sup>r</sup>, it can be proved that x in both of them is same without revealing <var>x</var>, <var>y</var>, <var>z</var> or <var>r</var>. Now, the credential is also a vector Pedersen commitment, hence has form Z<var>g</var><sub>1</sub><sup>m1</sup><var>g</var><sub>2</sub><sup>m2</sup><var>g</var><sub>3</sub><sup>m3</sup>...<var>g</var><sub>n</sub><sup>n</sup><var>h</var><sup>r</sup> where Z is derived from signer's secret key and each of <var>m</var><sub>i</sub> is a credential attribute (including link secret) and r is the randomness.

Now, for the prover to produce proofs that are correlatable, it enables the verifier to detect link secret reuse. It does so by requiring the verifier to have a unique identifier and then providing a binding of its link secret to that identifier. The binding is unique to the combination of the verifier's identifier and link secret. The binding is done by hashing the verifier's to get a generator <var>g</var> and then giving the verifier <var>g</var><sup>l</sup> where <var>l</var> is the link secret alongside the proof that the <var>l</var> in <var>g</var><sup>l</sup> is same as the <var>l</var> in the credential.  When prover sends <var>g</var><sup>l</sup> multiple times, the verifier will be able to recognize that they have seen it before, without being able to reverse <var>g</var><sup>x</sup> into <sup>x</sup>. (This non-reversability is given by the fact that in modular arithmetic, finding a discrete logarithm is computationally “hard.”)

Verifiers can set arbitrary bounds to the context in which they detect link secret reuse. If they want to see whether the link secret is reused twice in an hour, then that’s trivial. If they want to detect reuse twice in an election, that’s trivial as well. Provers see that verifiers are doing this, and can choose not to prove anything if they are unwilling to be vulnerable to the verifier in this way.

This technique can be extended to other attributes besides link secrets, where the prover derives multiple generators by hashing the verifier's identifier and some integer like <var>g</var> = Hash(verifier id || 1), <var>h</var> = Hash(verifier id || 2) and so on. Now if the verifier wanted to detect reuse of the (link secret, credential id) pair, the prover will send <var>g</var><sup>l</sup><var>h</var><sup>cid</sup> where <var>l</var> is the link secret and <var>cid</var> is the credential id. The reason for not letting verifiers pick those generators is that many colluding verifiers can choose generators that are multiple of each other and thus correlate the prover.

This technique should not be overused, because it allows a limited form of correlation (though it is correlation where provers opt in). Nevertheless, it is a useful tool for specific circumstances.

#### Technique 3: Require Link Secret Continuity

A verifier can require a given holder to demonstrate that they’re using the same link secret in all their proving interactions. Without fancy crypto, this is done by simply asking Alice to re-prove a minor fact that she proved before, using the same credential she used before, as part of a later request for proof. Alice can’t do this if she’s buying credentials on the black market, because the link secrets will differ.

For an example of how this technique provides value, suppose that a loan prequalification process requires much evidence about financial matters, but is deliberately kept anonymous to guarantee equal opportunity lending. Then, at a later stage of engagement, the actual loan application process requires the disclosure of strong correlators like name, tax ID number, birthdate, and so forth.

It might be tempting for Alice to prequalify for a minimal interest rate using false credentials, and then to finalize the process using her own. If the evidence from the two phases is disjoint, she might think she could get away with this. However, using link secrets, it is possible to require the second phase of proving to be performed using credentials bound to the same link secret as the proving in the first, anonymous phase.

There is a cryptographic mechanism to do this more simply than by requiring re-proof. The same mathematical properties that allow a verifier to detect reuse of a particular link secret value can be used to prove consistent link secret on a per-holder basis. However, because this mechanism for proof-of-same-link-secret is correlating, the simple reproving is generally preferred. 

Whichever mechanism is used, forcing consistent link secret use is yet another way of creating the vulnerability to foster trust. It makes Alice vulnerable to future context controlled by the verifier. This vulnerability does not require that the future context be strongly identifying. It could also be a richly contextualized presentation that still preserves Alice’s privacy. A verifier can ask at any time for any amount or subset of context connected to credentials Alice has already used; this is a serious problem for a malicious Alice in ongoing relationships, but it doesn’t inconvenience innocent Alice in the slightest. 

#### Technique 4: Commit a DID to a Link Secret

A Pedersen Commitment to a link secret can be shared by the owner of a DID at the inception of a relationship. This forces the owner of a DID to use the same link secret from that point forward. They cannot go out on the black market and acquire credentials at their pleasure to prove whatever they like, because the credentials won’t be bound to the same link secret they already committed to. This is another manifestation of the same vulnerability to future context that was discussed in Technique 3 above.

A variation on this technique actually allows the keys for a DID to be provably derived from a link secret, still without disclosing the link secret itself. This may further raise the bar for would-be fraudsters, in certain circumstances.

Both variations prevent unpremeditated maliciousness from Alice. However, they do not prevent narrow maliciousness that’s planned ahead of time. Alice could choose a particular fraudulent credential, establish a relationship, commit to the link secret used by that fraudulent credential, use the credential, and then abandon the DID. Therefore, this technique should not be used by itself.

#### Technique 5: Biometrics

Biometrics can be used in conjunction with ZKP credentials in at least 3 different ways to prevent fraud.

##### 5.1 Strong disclosure

This is the most obvious biometrics usage pattern: A photo or fingerprint is embedded in (or referenced by) a credential. On credential use, the prover shows that they are the legitimate holder by disclosing the biometric and matching it.

This pattern of usage has obvious problems for privacy, because the biometric in the credential is a strong identifier for the holder. However, its privacy can be improved by introducing the role of a biometric service provider (BSP). The BSP doesn’t need to know the context of the interaction; their role is limited to attesting the relationship between prover and biometric. This separation of responsibilities isn’t perfect; a BSP and verifiers could collude. Nonetheless, it embodies the principle of diffuse trust and may be worth doing in some cases. This technique is described in a paper submitted to the upcoming <cite>IEEE Spectrum</cite> special issue scheduled for December 2019.

Even without a BSP, using biometrics in full disclosure mode can be helpful when combined with deferred identification, as in the earlier example of loan prequalification followed by an actual loan application. If a fraudster knows that they will eventually have to disclose strong identifiers, and that one of them is a biometric, they are disincented from engaging in fraud during the earlier, anonymous stage of the interaction.

##### 5.2 Weak disclosure

In this approach, a biometric is embedded in a credential, but its precision is deliberately made quite low, such that it matches a larger-than-normal target cohort. For example, a biometric might be made to match 1 out of 100 people in the general population, instead of 1 out of a billion. On credential use, the prover shows that they are probably the legitimate holder by disclosing the biometric and matching it.

In some cases, this technique is usable without sophisticated crypto. Embedding in a credential a note that the holder is female, has a butterfly tattoo on her left wrist, and is a native speaker of Spanish is a weak disclosure strategy that could make the credential unusable by the vast majority of the population, in face-to-face contexts, without destroying privacy.

Of course, the assurance is much weaker here than in the strong disclosure example. By itself, this may not block fraud enough for full trust, and it may not seem interesting. However, remember that this can be combined with other techniques. Notice how this changes casual collusion: Alice is far less able to share her driver’s license with any of her college roommates. It also changes the economics of professional, premeditated collusion: the addressable market for every credential is now 1/100th the size that it was before. (That’s a shrinking of both supply and demand, not just supply; it doesn’t drive up price.). And it preserves a greater cushion for privacy than strong disclosure does.

##### 5.3 Permuted disclosure

With permuted disclosure, a biometric is embedded in the credential, and is tested and matched in the same way as the strong disclosure technique. The difference is that each time the biometric is disclosed, it is different. Thus, there is no correlator, but there is still strong assurance based on a biometric.

There are various ways to do permuted disclosure. The most sophisticated involves the holder permuting the embedded biometric using verifiable computation (e.g., ZKSNARKs or similar)--the verifier knows that the matched biometric differs from the embedded and signed one in some insignificant way that they can’t reverse-engineer (e.g., a handful of randomly chosen pixels in a photo). It can also be done far more simply, by having an issuer capture dozens of copies of the biometric data, signing all of them, and letting the prover select a different one each time they use the credential.

#### Technique 6: Provisional Anonymity

Using a technique called verifiable encryption, a prover can put strong identifiers in escrow as security against their good behavior, and can prove to a verifier that they’ve done so. This creates vulnerability without disclosure. The keys to unlock the verifiably encrypted data can be sharded and given to peers, sent to a third party that will adjudicate claims of bad behavior, or similar. The escrowed identifiers can provably derive from a verifiable credential.

For example, an online forum can offer anonymity as long as members respect a code of conduct; if someone engages in trolling, the mailing address, phone number, and full name on their driver’s license can be revealed.

#### Technique 7: Link Secret Bond

It is possible to publicly post a bond against a link secret, such that anyone who knows the link secret can confiscate the bond. This is direct proof that the link secret is not publicly known, as it creates an incentive for anyone who knows it to confiscate the money and compromise the link secret. It can be delivered without compromising the zeroness of zero knowledge.

#### Technique 8: Financial Escrow as Vulnerability

A simpler form of vulnerability can be used: the prover can put money in escrow as a security against their good behavior. This is really a variation of Technique 6--but what is confiscated is money rather than strong identifiers.

## Conclusion

Credential fraud has been with us as long as we’ve had credentials, and will no doubt continue to manifest in new ways as technology evolves. A holder lying about credential ownership at proving time--the specific scenario that motivates a lot of ZKP FUD--is only one of the hundreds of fraud variations in the [taxonomy enumerated so far by the credential fraud discussion group](https://docs.google.com/document/d/1yX2-wKPxKPUTGEyxIQKK_Z-azT2A_AykIfPEB1cW-d0/edit). Thus, we must think carefully about whether credentials of all types--not just ones based on ZKPs--are susceptible to fraud. We recommend a serious effort by the digital credential community to tackle this issue in a formal way. We will be proposing more efforts in this vein at RWOT.
 
ZKP-based approaches to credentials are undoubtedly imperfect, because they are young. However, there is no evidence, either anecdotal or rigorous, to suppose that ZKPs are inherently, uniquely vulnerable to trust problems. Expert literature has a long and rich history of clever solutions. This paper only mentions a handful.

The best way to serve community interests with respect to ZKPs and credentials is not to fear them. It’s to embrace them, and get on with the business of making them better and using them well.

<hr>

## Appendix: Further Reading

This topic has been explored in great detail by cryptologists in the expert literature over the past 30 years. A few highlights include:

* [“An efficient system for non-transferable anonymous credentials with optional anonymity revocation"](http://cs.brown.edu/people/alysyans/papers/cl01a.ps.gz) (Camenisch and Lysyanskya, 2001)
* [“How to Win the Clone Wars”](https://eprint.iacr.org/2006/454.pdf) (Camenisch et al., 2006)
* ["Balancing Accountability and Privacy Using E-Cash"](http://www.dia.unisa.it/conferences/SCN06/) (Camenisch et al, 2006)
* [“Making P2P Accountable without Losing Privacy"](http://cs.brown.edu/people/alysyans/papers/bcplus.pdf) (Bilenkiy et al, WPES 2007)
* [“One TPM to bind them all: Fixing TPM 2.0 for provably secure anonymous attestation”](https://ieeexplore.ieee.org/abstract/document/7958616/) (Camenisch et al., IEEE Symposium on Security and Privacy, 2017)
* [“Privacy-preserving attribute-based credentials in cooperative intelligent transport systems”](https://ieeexplore.ieee.org/abstract/document/8275631/) (Neven et al., IEEE 2017)
