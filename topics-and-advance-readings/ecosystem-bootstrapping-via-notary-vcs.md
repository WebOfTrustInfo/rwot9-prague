# Ecosystem Bootstrapping Via Notary VCs

In this paper I explore the possibility of building a web-of-trust
via a slight abuse of SSI tools.  The goal is to improve the
footprint of deployed WoT and SSI technologies through
verifiable credentials issued without the expectation that the subject
maintains a wallet, controls a DID, or manages private-keys, and
where the issuer of the credential is not the originator of the data.
Using VC and SSI technology in this way weakens the chicken-and-egg problem
facing SSI adoption and improves the chances that we will see widespread
adoption of full and proper SSI.

## Piles and Piles of Documents

My thinking is based on several three recent experiences:
- Applying for Schengen visas for my wife, a Thai national
- Changing my expatriate status in Thailand (as a U.S. national)
- Establishing Texas residency for my daughter (a U.S. national, from Oregon)

In all of these cases I found myself assembling pools of documents corresponding
to different legal processes and presenting said documents to officials charged
with implementing the legislation's conditions.  In each case the officials
operated with a degree of autonomy and authority in vetting the document set
and determining compliance.  The autonomy and authority is rooted
in a legislative clause like "_at the discretion of the official_"
which allows the official to make a judgement call based on their
experience and their consideration of the document pool as a whole.

The standard vision of an SSI-enabled future deals with the above and
similar scenarios as follows:
1. The applicant holds several credentials, which were issued to a DID they
   control, stored in some wallet application (or agent, or hub, etc.)
2. The issuers are all well known actors whose identity is tied to
   publicly registered DIDs
3. When using the credentials the applicant provides the official with some
    verifiable presentation or some zero-knowledge-proof engine, allowing the
    official to satisfy the conditions of the legislation they are trusted with
    enforcing.

This is an ideal case - and some day, when individuals and organizations
have DIDs as surely as they now have phone numbers and email addresses, and
when there are ubiquitous applications that make navigating the web of
issuers, subjects, and verifiers as simple as sending an email or making
a phone call, then this process will be second nature and obvious to
all.  In fact, the first-order _trust_ is the _faith_ in the engineering
of the system and the technology itself.  It is within this framework that
second-order trust flows emerge, such as when an official trusts that a
credential issued by an issuer satisfies the conditions of the legislation.

However, as of today there is *no* trust in this technology and there is
near zero adoption of SSI and WoT technologies. We are, at the moment,
operating in and designing systems for a future state of affairs but perhaps
are not paying enough attention to the current zero-penetration reality.
The danger of not paying attention to the active identity-tech reality
is that the first-order trust in legislative compliance tools will go
first to another style of technology, such as state-sanctioned credentials
issued and managed fully by our glorious leaders and our benevolent
corporate overlords.  Once legislated processes begin to adapt to an
alternate trust environment it will become even more difficult to switch
to SSI and decentralized WoT technologies.

I suggest a sense of urgency by noting that the current state of
legislated document-vetting is in dire need of improvement.  Current processes
are, at best, frustrating, inefficient, invasive,
chock full of irrelevant data, invite fraud, sanction identity theft, and
are based on security theater which is tremendously easy to bypass.  Most
governments and agencies are well aware that they could, and need to, do
better, but there are not yet any realistic and SSI-friendly options
for improving these document vetting and compliance processes.

In general, these processes take one of two approaches:
- paper with security features or significant security ceremony
- documents which contain pointers to information that "could be checked"

The use of documents with high levels of security features is out of scope
for this paper, keeping in mind that such documents are generally required
only by processes that are low in volume (i.e. adoption, petitioning for
citizenship) or high in perceived security threat (i.e. validation of passports
at borders).  More common are cases like the three mentioned in the introduction.  These are much higher in volume and much lower in perceived
risk.  As such, document
security features are usually waived in favor of photocopies and security
ceremony is limited to "stamp-theater" along with, and most importantly,
the reference to information which could, in theory, be cross-checked.

Cross-checks take time and cost money and are only warranted if the
application looks suspicious or problematic in the
aggregate.  This is one of values of the "_discretion of the official_",
which taps experience, judgement, and allows common sense to be applied on
a case-by-case basis so that reasonable, although imperfectly vetted,
judgements are made and, most importantly, cross-check costs are optimized
so that cross-checks are performed only when justified.

An advantage of SSI-style technology is that the cross-checks can be
pre-computed and handed to the official in the form of a proof.  In the
fully-formed SSI case, the issuer of a credential makes a claim about
a subject, and the official can quickly, ballistically, and without any
contact with the issuer, verify that the claim was, in fact, made by
the issuer about the subject.  However, given that there is near-zero
penetration of SSI and WoT technology, this is only theoretical.

Can we use SSI-like technology to get to a half-way point that begins
to integrate WoT processes and existing document-vetting without
requiring that a mature ecosystem emerge fully formed before it is first
useful?  I believe the answer is yes - so let's look at an example in
a bit more detail.

## Insurance proof for a Schengen Visa

Consider the Schengen visa requirements from the Czech republic[^schengen-visa].
All Schengen visas carry the same basic skeleton of requirements,
but they vary in specific details depending upon itinerary.  For example,
when determining if the applicant has sufficient funds to support their
visit, the itinerary matters - Paris is more expensive than Prague.
Other requirements are EU-wide, such as the requirement to demonstrate

  ```
  Travel medical insurance confirmation of minimum 30,000 €
  coverage within Czech Republic and the entire Schengen area
  ```

This is so common that it is readily available through online vendors and
can be purchased in a matter of minutes.  In our case we purchased the
insurance at https://www.axa-schengen.com/ and included, in our
application, a printed receipt of purchase.  There were no
security features in place - but, in theory, the approving officer could
contact the agency and use the policy number to verify the policy was genuine
and met the specific requirements for travel in the EU.

This is a classic opportunity for a cryptographic proof or verifiable
presentation where, instead of a printed receipt with a policy number
and the *potential* for verification, and actual digital signature could
be provided such that the verifying official would know, without any
additional action, that the policy was genuine and met the requirements.

It is worth noting that, by-and-large, this is an eyeball-able test.  One
can easily imagine a consular officer seeing yet-another receipt from one
of the same standard companies.  The officer would not be out of line to
simply trust that the policy was genuine as long as the receipt looked like
all of the other receipts from the same company.  Likewise, when faced
with an unfamiliar receipt or company referenced is unknown.  A reasonable
receipt from "AIG Travel Insurance" might be accepted with less
scrutiny than a receipt from "Ministry of Silly Walks Spot Insurance".

This is where the "_discrection of the official_" comes into play, since
it is the official who is responsible for making the call as to how closely
to investigate the claim represented by the photocopied document.  I
think it is worth asking, "_What, if anything, can we do *today* to make
the official's job easier_"?

So what is missing and why isn't it done already?  Well..... let us look
at some of the pragmatic obstacles today:
- **Individual DIDs**
  The applicant does not yet have a DID, does not run any identity-tech
  software (as there is no mature wallet software suitable for non-technical
  users), and the user is unlikely to take a deep-dive into identity-tech
  when there are alternatives.
- **Fear and Paranoia**
  Some consulates and embassies do not allow people to bring digital assets
  across the threshold - the united states is particularly paranoid in this
  regard but many civilized consular offices allow both officials
  and applicants to access internet resources.
- **Issuance Infrastructure**
  There are almost no insurance issuers with DIDs nor are digital credentials
  integrated into their existing business processes.
- **Training** - businesses, consular officials, and other players in the
  chain must have the appropriate training to understand how digital
  credentials work, how to to use technology like QR codes or wallet apps,
  and to understand the UX.  A general level understanding, such as is common
  in our community, is vastly above and beyond what can expected of people
  in general, especially front line officials and visa applicants.
- **Entrenched Processes** - there is extensive preexisting knowledge,
  training, and capital investment for dealing with the paper items,
  including archiving and other reporting processes - and the integration
  of a new technology is simply an expensive, time consuming, political
  process.

These are just some of the obstacles which need to be overcome in order to
transition to the target universe of fully SSI mediated process, for something
as simple as confirming that a Schengen visa applicant has appropriate
insurance coverage using SSI-technology.  Given that this is only one
element of the application process you can imagine the scale of the integration
required for a complete visa application vetting to be SSI-driven.

The same general rules apply, in various degrees, to other organizations,
institutions, and processes.  The other two examples provided earlier, the
establishment of Texas residency and the transitioning of a visa
classification in Thailand, are qualitatively very similar although
the quantitative impact of each risk is different.  For example, it *is*
currently possible to bring your cell phone or a USB stick into the Texas
Department of Public Safety offices and into a Thailand Department of
Immigration Office, but bringing that same USB stick into an American
consulate is considered an act of terrorism.

As we transition from a pre-SSI-world to a world which is heavily mediated
by SSI and WoT mechanics, we need to provide middle ground alternatives.
These alternatives would have properties like:
- **Individual DIDs** and the requirement to begin with
assuming responsibility for lifetime management over a private key
must not be required
- **Fear and Paranoia** should be used to make an early decision to abort
or proceed, as some institutions are inherently paralyzed
- **Issuance Infrastructure** must be optional and add value when present
- **Training** should be minimal, and should be optional.  No existing process
should break if those implementing the process prove unwilling or unable to adapt.
- **Entrenched Processes** need to be augmented rather than replaced.  Augmentation should be optional and at minimal cost.

## Alternative

I would like to focus on the government driven processes mentioned above
and explore how a variant of the "pure-SSI pathway" might be used to get an
"SSI-lite" pathway running in parallel with the existing pathway.  The hope
is that by using the same ceremony and credential technology we can bias
the field of government document vetting in favor of SSI, and introduce the
concept of a DID-based WoT for trust in place of the soft comparison done
today.  In other words, the consular officer would use DID-mediated trust
rather than relying on familiarity with common vendors.
We will appeal to the insurance-verification for Schengen visas for
specific details although the issues are almost identical for all three
cases mentioned and for many, many more.

### No Wallets, Agents, or Subject DIDs

The pathway envisioned replaces strongly held credentials such as those
capable of supporting zero-knowledge proofs or otherwise requiring the holder
to also manage some essential private key, with simple files.  Ideally they
would follow the W3C CCG's VC model, but ultimately would play the roll only
of a signed document and use a very minimal number of features.

Consider the case of my wife's Schengen Visa to accompany me to Prague for
RWoT 9.  Because there does not yet exist a robust SSI-infrastructure, she
does not carefully manage a set of private keys nor an identity wallet.  For
this case, using SSI requires engaging a massive new technology and
beginning a lifelong commitment to carefully guarding keys that define
her digital life.  This is simply
unrealistic.  It would be as if obtaining a black-belt in Judo was suddenly
slipped in as line item for opening a bank account.

What might be possible is a "disposable DID" that is used once and thrown
away after the application process.  That is the expected lifetime of the
wallet, app, or other infrastructure as well.  This is, in a way, the
concept of a pair-wise DID, but extended so that the *entire scaffold* for
SSI can be jetisoned after about 3 weeks, the time it took to acquire the
visa soup-to-nuts.

From the perspective of the applicant (assuming all of the other issuance
and verification problems are solved) we have 3 options for the
insurance validation (or document validation in general):
1. simplest - save the receipt PDF to a thumb drive, take it to the
  copy shop two blocks over, and pay the copy shop about $0.02 to print
  the PDF - this is the state of affairs today and does not involve
  any credentials or SSI-friendly tech.
2. hardest - onboard onto a digital identity platform, set up lifelong
  keys that will define the user, purchase wallets and apps to help
  with key rotation and recovery as well as credential storage, then
  somehow use the new apps to "get the
  receipt into the wallet" - total cost would be substantially higher than
  $0.02 - both in money, but also in time, research, platform evaluation,
  and figuring out how to get it all to work
3. medium - save a PDF of the receipt with a QR code that points to
  some digitally signed asset or credential with the option of downloading
  the digital asset.  Cost remains about $0.02 or could cost more for
  different formats or hosting, or for the service in general.  Most
  importantly there is no lifelong
  commitment to guarding private keys, and no training required.

Eventually - when enough of the world has SSI-driven technology and it
becomes *worthwhile* and *convenient* to have an identity wallet and
to take responsibility for keys - (guarding them like a passport, or a
gold necklace) - *then* and *only then* is it reasonable to talk about
real world SSI technologies that assume the subject "has/can-get a DID"
to which multiple credentials can be issued - which is what would be
required if
we were to pool the credentials together to form a digital Schengen visa
application.  Until such time, DIDs, if required
*at all*, should be disposable, single-use, free, and not require special
storage - the "private key" should play no role in the user's life.

For the envisioned SSI-like pathway the first step towards a viable
full SSI infrastructure would require the individual only to download or
print files, and would not require special wallets, apps, or a lifelong
commitment to a private key.

### Fear, Paranoia, Entrenchment, and Verification

Entrenchment rules government processes and even small, helpful changes
and adaptations can be difficult to implement.
For this reason, fundamental changes to *the way things are done* can be
nearly impossible to achieve and the only real hope for the adoption of
SSI technology is via options that do not *require change* but
rather *orthogonally augment* the way things are done.  The key to this is
the "_discretion of the officer_" and providing SSI and WoT technologies that
enable such officials to arrive at the same decisions they would make today,
but to arrive at them faster and with more safety and strong defensive
auditability than before.

For example, let's again look at the insurance verification problem for
a Schengen visa.  Since we've ruled out the final-form SSI case and must
not alter the existing process - the applicant must still provide some
physical document providing proof of insurance coverage - and it is up
to the officer to determine if the support is genuine.

Now, imagine if the existing document were simply augmented with a QR code
that linked to a digital record of the same document and possibly provided
some other supporting information which extended the level of trust and
security available to the evaluating officer.  In this case, the same minimal
level of security is provided, but the ability of the officer to obtain
that information may be as simple as scanning a QR code.

The envisioned credential is not a matter of public record, nor is it a
matter of strict privacy - but rather is more like walking nude through
a hotel room with a pool view.

The presumption is that you are "mostly private" in your hotel room, and
the presumption is that your actions are "aggressively public"
if you stand on the balcony
and call out to the other hotel patrons.  However, it is not clear that
your intention is public, or that your are clearly private, if you
absentmindedly forget to draw the curtain and thus accidentally
moon the entire Holiday Inn poolside while picking up your socks after
a shower.

Disclosure of the credential outside of the intended audience is
equivalent and all you can do is
count on people's discretion not to post the video they just captured on
social media.  And just as modern biometric identification
techniques render such a post more dangerous that mere humiliation, the
use of automated search software can turn a credential posting into potentially
dangerous doxing.

For this reason direct, personal transmission of the credentials via a
USB stick submitted with the application (or transferred in some similar
pathway) is preferred over internet delivery - however, in some countries
fear and paranoia rise to the foreground and hamper progress.  For example,
at present you might get shot trying to bring a USB stick to a united
states consular officer.  Likewise, if you fall back to internet delivery,
it is likely that some officials are not allowed to access the internet
or use QR codes in this manner.

This is one reason why the optional nature of this style SSI roll-out is critical.  It does not challenge contexts dominated by fear and paranoia,
but instead augments and enhances processes when possible.  The suggested
pathway is fully optional, requires minimal specialized software and thus
training, yet provides the scaffold around
which first-order trust in SSI-mediated document vetting can be grown.

### Avoiding the Issuance Problem

The final component of SSI-lite for official document verification is
the role of the issuer.  The problem we face with SSI-classic is that
the issuers need to specialized software and registered DIDs in order
to issue credentials to subjects.

In the context of a Schengen visa application the vendors of the policies
all need to alter their business processes to provide this offering.  This
means alterations to web sites, alterations of internal databases, a lot
of contract coding to tie it all together, and despite the fact that the
core is almost identical, the integration with the insurance provider back
end needs to be performed over and over - and it needs to be paid for by
each vendor.

This investment is not likely to happen until there is an established
demand for these credentials.  Under our assumptions, with the verifier
starting out as optional with only occasional users, the demand is simply not
enough to justify the massive capital outlay.

For this reason, the credential issuer, ideally, should *not* be the
insurance provider.  This applies, in general, for all of the documents
required in the Schengen visa application, the establishment of Texas
residency, or the migration of visa classification in Thailand.  In all
of these cases, the total cost to create first-order issuers is completely
unreasonable.

Thankfully, there is an institution which *is* in place, globally - and
that institution is the office of a *Notary*.  In the united states, notary
functions are often handled by someone known as a Notary Public[^notarypublic].
Notaries Public have very limited abilities, but they specialize in
witnessing and vetting documents - providing a cross-check record of their
involvement and engaging in a little bit of "stamp-theater".  In other
jurisdictions, Notaries have a
broader range of powers[^notary] - in some cases operating like peers
within the judicial theater.

Focus on the notary changes the nature of the credential which is issued.
The credential is no longer a direct, first-class claim by an issuer about
a subject - it is a claim of observation, by a registered professional,
of a document issued to a subject.  The credential does not claim anything
about the subject, it simply records that some piece of information was
observed, relative to the subject, at some point in time - and, as such, the
notary becomes the issuer.

In the cases where the primary issuer *does* provide full SSI-support,
then those credentials can be used in lieu of the notary issued credentials,
or the notary can include a reference to that credential in their
issued credentials (presumably the notary is witnessing more than one
document in a pool of documents supporting a legislated process)

## Bringing it all together

In the envisioned pathway, the only DIDs required are the DIDs of those
capable of "notary action".  If we take a united states Notary Public as
the lowest bar for the skill set, we have a set of individuals who may
reasonably be expected to
- acquire and responsibly manage a DID
- responsibly operate issuance software
- voluntarily undergo training and licensing

Furthermore, such agents are not currently participants in any of the
existing processes - they are not the first line officers responsible for
implementing legislated process conditions, and they are not culpable for
mistakes and violations - as such, it makes little sense to bribe them
and so they are not, yet, epicenters for corruption.

More interesting is the fact that this actually develops a WoT - Notarial
DIDs can be trusted by officials as "quality recommendations" for data
in their packets.  It is easy to imagine that digital applications from
a notary with a long history of not making mistakes might stand a greater
chance of rapid turn-around.  To see this, consider the processing of
an application rife with QR codes or other access to digital assets - if
the consular official sees that "Eddie, the Trusted Vetter" provided *his*
stamp over the documents - then perhaps the consular official can quickly
leaf through the documents and safely issue the visa (or grant Texas
residency, or change a visa classification) - because all of the supporting
documents (which are submitted in the same fashion as before) do, in fact,
stand up to scrutiny.

Likewise, if the notarial DID is new to the game, no trust has been
established and the consular officer must do a first order analysis until
such time as the new DID becomes trusted.

Most importantly, what we have established, in the realm of intransigent
government processes, is a footprint for WoT and SSI technology - and one
that opens the door to finally getting rid of all of that paper, and finally
letting us just use SSI and ZKPs to achieve real world actions.

#### References

[schengen-visa] https://www.schengenvisainfo.com/czech-republic-visa/
[notarypublic] https://en.wikipedia.org/wiki/Notary_public
[notary] https://en.wikipedia.org/wiki/Civil_law_notary
