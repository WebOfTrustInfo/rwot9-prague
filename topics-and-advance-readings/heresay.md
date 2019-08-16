# Heresay: A Fuzzy Prediction Market for Distributed Reputation
AJ Adams (aj@bydot.app) & Matt Condon (matt@bydot.app) | v0.1 | 15 Aug 2019

## Abstract
As the velocity of human migration across all contexts accelerates, so does the significance of legible, transitive reputation. Reputation systems govern access to communities, credit, and citizenship. Should I download from this seed? Should I buy from the seller? Should I admit this individual? Many existing systems cultivate trust by proxy of a centralizing agent (governments, FICO, Facebook) or a persistent value (TidalTrust, FIRE, NICE). We propose a pattern for distributed, emergent reputation rendered via a fuzzy prediction market. In order to promote scale with resilience, legibility with ephemerality, and transitivity with context, we begin by investigating how identity, trust, and reputation function at intimate scale and under organic constraints.

## Identity, Trust, and Reputation
### Identity is a function
An identity signifies, among other things, a specific behavioral function. Given these inputs, what are the outputs? When this happens, how will this individual react?

| Input | Function | Output |
| :--- | :---: | ---: |
| Stimulus | Behavior | Reaction |

The _function_ of an entity is illegible, often even to itself, but we approximate its contours with terms like behavior, character, nature, personality, temperament, attitude, and disposition.

### Trust is a degree of certainty
Trust is the subjective certainty that an entity will behave predictably in response to specific circumstance. Do I trust this seller to fulfill my order if I pay? Do I trust this person to fulfill their responsibilities if I hire them? This certainty is cultivated through repeated interactions: a large, consistent dataset is indicative of a predictable and therefore dependable entity.

### Reputation is a prediction
Reputation is a prediction of how an entity will behave. Reputation systems, therefor, are designed to foster trust where there is no prior data. When participants in a system have some supplemental certainty of predictable interactions, they will tolerate larger risks and form larger structures in less time.

In this way, well-designed reputation systems enable participants to nucleate into relationships fast, a web phenomenon we refer to as _synthetic serendipity_. It's serendipitous that, as someone who enjoys urban transit, there's a place to connect with other [NUMTOT](https://www.facebook.com/groups/whatwouldjanejacobsdo/) contributors. It's serendipitous that I can connect with a stranger that I share a mutual attraction for. It's serendipitous that I want an [OP-1](https://teenage.engineering/products/op-1) and someone nearby is selling theirs. It's serendipitous that I need to get from A to B, and other individuals on approximate trajectories and a willing driver can coordinate an efficient route. 

### Identity is quantum
Identities are neither fixed nor independent. In many cases, neither is the subject the identity represents (such as an individual, an organization, a device, or an artificial intelligence).

Here's an analog example: the metaphor of a named individual strings together continuous changes of composition, appearance, personality, experience, and expression, which reenforces a perception of continuity (like [The Ship of Theseus](https://en.wikipedia.org/wiki/Ship_of_Theseus)). Your social security number doesn't change, but you do.

However, these linear, causal changes represent only one vector. That same named individual is also adapting to quantum changes contingent on their perceptual context(s). In other words, an entity changes both with time _and within time_, which is why the authors of [Identity Crisis](https://github.com/WebOfTrustInfo/rwot2-id2020/blob/master/final-documents/identity-crisis.pdf) characterize identities as "emergent phenomenon."

There's a Pali phrase for this—_nacha so nacha anno_—that reads "not the same, but not another." This quantum nature of identity is obvious in practice: individuals behave differently when their context is a specific friend than when their context is a different friends or 4 friends or 5 coworkers or 20,000 strangers or 2 cats.

Metaphorically, then, identity is the visible, ephemeral portion of an interaction that etches new data into our understanding of the entities involved. If identity is the fire, reputation is the burn.

When reputation systems are designed without this quantum behavior as a primitive, one outcome is Facebook: a single, rigid, unified presentation identity that attracts global reputation. Another outcome is Sesame, China's nascent social credit system. Combining context isn’t unified context, but no context. DIDs and distributed reputation, however, are poised to subvert this model.

## Risks 
Developing trust is costly, which is why the value of curation increases with abundance in rivalrous environments (a conservation of complexity).

For instance, deciding between 3 available wines is manageable: in short time the most enjoyable bottles will surface. However, in saturated information environments, such as a shelf full of wines, selecting the “fittest” bottle requires predictive derivatives. In this example, trusting a specific winery, vintner, geography, competition, rating system, price point, or branding/aesthetic as derivatives for the bottle’s “fitness” reduce the decision burden. 

By reducing decision burden, reputation systems unlock massive potential across domains, from FICO credit scores to military decorations, torrent ratios, Tinder elo, social media follower counts, Wikipedia credentials, Reddit karma, Stack Overflow upvotes, and Google PageRanks. However, since legible derivatives like these necessarily flatten the rich ambiguity and context underlying them, reputation systems are susceptible to gaming, falsification, Sybill attack, miscorrelation, self-fulfilling prophesy, and other forms of basis risk or uncertainty.

Basis is the relationship between the a derivative and the underlying. In our terms, reputation is a derivative of underlying behavior. Basis risk is the risk associated with variance in that correlation. Basis uncertainty is the risk the basis no longer exists—that the correlation between reputation and behavior is zero.

### Gaming
Wherever it's less costly to inflate a reputation derivative than improve the underlying behavior, participants will do so. For instance, SEO is an entire industry dedicated to exploiting the delta between a website’s PageRank and its actual relevancy to search queries.

### Falsification
Wherever reputation is meaningful, participants will intentionally seed false information to inflate or deflate reputation. This is most effective when outlier data has an equal or outsized influence relative to the median consensus. In many cases, this manifests as defamation.

### Sybil attack
Sybil attack is a falsification strategy. Wherever the cost of creating an identity is less than the value gained from self-rating, participants will spawn additional identities to inflate or deflate reputation.

### Miscorrelation
Whenever reputation is not well correlated with the underlying behavior, such as conflating performance playing a sport with the probability of being a good coach, there is basis uncertainty. For instance, Tala, a credit scoring agency operating in locations such as Kenya and the Philippines, claims to use over 10,000 data points from an individual's smart phone to determine credit worthiness. How much of that is signal versus noise?

### Self-fulfilling prophesy
Even when exotic correlations are meaningful, there’s a risk the map influences the territory. Consider the example of using marital status as a derivative of credit worthiness (as FICO did prior to regulation in the ‘70s): even if unmarried individuals are, in fact, less credit worthy, the positive feedback can reinforce the correlation and thereby increase the prejudice.

## Properties
### Legibility
At intimate scale, trust develops in a fecund morass of ambiguity, inference, innuendo, and gossip. However, digital systems demand discrete data. 

That discrete digital reputation is necessarily lossy is both a bug and a feature. Synthetic serendipity relies on reduction—on legible data and unqualified statements—to initiate new connections, but reputation systems must also recognize the rich, ambiguous data embedded in the context.

**Objective:** generate highly-legible reputation, like a credit score or product rating, while mitigating the risks of decontextualization such as gaming and falsification.

### Transitivity
Moreover, at intimate scale, reputation is accrued and queried on a per-context basis. That’s not to say context-collapse doesn't happen in analog environments—it does—but how an individual is regarded in their gym, for instance, versus how they’re regarded in their church rarely influence one another.

In [Decentralized Identity as a Meta-platform](https://github.com/SmithSamuelM/rwot9-prague/blob/master/topics-and-advance-readings/Decentralized-Identity-Meta-platform.md), Samuel M. Smith Ph.D. discusses the natural benefits of DIDs for "trans-contextual value creation and capture." The difficulty of systems that allow “contextual transitivity,” however, is they often also allow trans-contextual value dissolution and loss. Reputation velocity accelerates omnidirectionally.

That being said, reputation transitivity is a critical feature in a globalized context. Consider the impact on human migrations, where migrant individuals often leave their reputation capital—and much more—behind. The ability to leverage reputation across contexts becomes paramount so long as its context remains intact.

**Objective:** promote reputation transitivity while mitigating risks such as context collapse, miscorrelation, self-fulfilling prophesy, and high-velocity spirals.

## Design Primitives
Holding the aforementioned risks and features in hand, we look first at how reputation problems are solved organically, at intimate scale. When designing resilient, distributed systems, why not consider the most inveterate resilient, distributed systems?

For instance, to determine where to store reputation data, first consider where reputation is stored organically. To determine how to serve reputation data, consider the process at intimate scale.

However, as the features section illuminates, organic systems and intimate scale do not accommodate digital limits. Our heuristic for navigating this balance is to embrace both digital capabilities and organic constraints.

## Heresay Protocol
Heresay operates as a distributed, fuzzy prediction market for reputation claims. Below, we outline the system in broad strokes.

### Data generation and storage
Entities store data on each other as a boolean, discrete value, or continuous value. Each data point is time-hashed with the subject and contexts to substantiate (1) knowledge of subject and (2) recency of interaction. This data is applied to reputation claims (predictions of behavior) for both the data holder and future queriers.

In addition, queriers record meta-reputation data on respondents which represent their predictive ability (trustworthiness predicting the trustworthiness of others). This claim is employed to both select respondents and weight their claims. 

### Subject consent
A query begins when the querier requests consent from the subject to query their reputation in _x_ contexts for _t_ time.

Contexts are typified in descending specificity, much like fonts in CSS. For example, a reputation query about a ride-sharing driver could read `contexts: dService, driver, ride-share, transaction, interaction`. The format of context types is maintained culturally. 

Trustworthy respondents should automatically ignore an unsigned query.

### Query mechanics
Once the subject signs the query, the querier announces the query to their graph. A query is a contract which includes a subject, contexts, query interval, fuzzification function, query horizon, and escrow.

Queries can be routed down-graph, in which case the routers join the contract to receive compensation from the escrow, and meta-reputation is calculated as a function of the intermediary node(s) meta-reputations.

### Response mechanics
Respondents process their data via the fuzzification function to render a reputation claim: a prediction that, given the stated contexts, the subject is `untrustworthy`, `somewhat untrustworthy`, `somewhat trustworthy`, or `trustworthy`. For example, a given fuzzification function might render the crisp data of 3/5 stars as either `somewhat untrustworthy` or `somewhat trustworthy`[^1].

Once the query interval has expired, all submitted, fuzzified claims and their time-hashes are revealed to all members of the contract. The querier aggregates the claims to infer a legible reputation, which can remain fuzzy or be defuzzed into a crisp value.

Moreover, a query can optionally contain a request for additional context, such as a text string (comments) or any other auxiliary data.

### Compensation mechanics
Respondents are compensated according to the accuracy of their prediction. If the querier interacts with the subject after a reputation query and then asserts a reputation for the subject, that reputation claim is an oracle to the query contract. Compensation is then apportioned among respondents accordingly.

However, in several situations, such as when the querier avoids an interaction with the subject based on the query response, there will be no oracle to close the query. In this case, compensation is apportioned among all respondents at the query horizon.

Query members (querier, respondents, routers) can validate the time-hashes and adjust the respondents meta-reputation and compensation accordingly.

All queries, including meta-reputation queries, can be defined as an asymmetric and directed value for that edge (relationship) within a specific context.

## Effects
In the terms laid out by [Bubendorfer et al. in their survey and taxonomy of reputation systems](https://www.researchgate.net/publication/264983117_Reputation_systems_A_survey_and_taxonomy), Heresay features (1) personal history, (2) multiple contexts, (3) indirect individual collection, (4) vector representation, (5) fuzzy aggregation, (6) individual entities, (7) open presence, (8) distributed governance, (9) unstructured fabric, (10) open interoperability, (11) incentivized control, (12) holistic evaluation, (13) selected subset data filtering, and (14) decay data aging.

Additionally, Heresay is designed to:

### Minimize disclosure
Queries are associated with hard costs. Risk is an arithmetic of consequences and probability, and therefore some actions require more trust (certainty) than others. To increase certainty, a querier can increase the escrow and query interval to amass a larger prediction market, or vice versa. 

### Discourage centralization
Moreover, queries with non-zero cost also discourage an entity from aggregating (centralizing) reputation data for sale.

### Reduce reputation permanence
Reputation is ephemeral, not persistent. Two identical queries should generate consistent but non-identical results. Reputation is durable in that the data underlying the prediction is present and enduring, but it only renders legibly when queried. In some sense, reputation is liquid until the pressure of a query makes it solid for that exact instant, like a non-Newtonian fluid.

Furthermore, since reputation claims (predictions) are judged based on a (potential) future interaction, respondents will likely optimize toward some form of data decay to trim off crusty data points and thereby improve their accuracy.

### Discourage gamification
Ephemeral reputation adds layers of difficulty to system gaming by obscuring and obfuscating reputation. The most reliable, low-cost method to improve reputation is to walk-the-walk.

### Discourage falsification
Since reputation emerges from the querier's graph, it is necessarily incomplete. This is a bug and a feature: one beneficial side-effect of incomplete data is noise cancellation, trimming outlier data points and thereby reducing the probability of falsified data entering the results.

### Discourage Sybil attacks
Similarly, searching the querier's graph reduces the probability of including Sybil identities among respondents. Moreover, even when identity creation is frictionless, acquiring meta-reputation is not, which allows queriers to identify and mute potential Sybil identities.

### Interoperate with centralized systems
Heresay is designed to facilitate trust without a centralized entry, but it's capable of bootstrapping off existing graphs or reputation systems. In fact, any platform can act as a respondent. Consider the potential for reputation transitivity among various accommodation services, such as Airbnb, Couchsurfing, and some decentralized alternative.

### Encourage cooperative behavior
Subjects are blind to both the respondents and their reputation claims. There's a non-zero probability that a significant entity in the subject's graph is included among the query respondents. Since the subject's behavior will be relayed back to all respondents if the querier rates the subject, this cultivates a form of transitive accountability. 

Moreover, when a subject fails to behave in accordance with a respondent's prediction, they materially injure the meta-reputation the respondent staked on them. In this way, subjects are incentivized to make even intentionally false reputation claims true.

### Discourage miscorrelation and feedback loops
There is no "source of truth" on reputation and no limits to what contexts can be queried. However, it's in the best interest of the querier to query contexts that best correlate with the behavior they're predicting. Even then, all reputation queries are ephemeral, which limits the damage a miscorrelation or self-fulfilling prophesy can inflict on the subject.

### Discourage fabricated claims
A distributed ledger is employed to time-stamp when a respondent recorded data on a subject in _x_ contexts. In this way, data cannot be generated opportunistically as all data time-stamped after the query begins should be discarded.

### Ensure transparent consent
All trustworthy entities should automatically ignore unsigned queries.

## Further Considerations
### Hybrid machine and human answerable queries
Fuzzy inferences map vague, uncertain values with good accuracy and lend themselves to human-significant values. What would the reputation prediction market look like with t=18000ms human answerable queries, such as, "How trustworthy is `subject` at babysitting?".

### Open (full trust) relationships
Entities with high-trust could allow zero-cost querying between each other, fluidly sharing reputation claims without sharing the underlying data.

### Subject identified respondents
By searching only the querier's graph, Heresay necessarily sacrifices the completeness a subject or centralizer could provide. Is there a functional way to allow the subject to route to respondents, similar to how applications require subject-assigned references?

### Ephemeral group reputation
Organizations operate as single entities, but can reputation by rendered as a function of the group members' combined reputation?

### Resource reputation
How might Heresay render distinct reputation for both the seller (entity) and their goods/services (resources)?

[^1]: These values correlate with the model articulated by Griffiths et al. in _[Fuzzy Trust for Peer-to-Peer Systems](https://www.dcs.warwick.ac.uk/people/academic/N.E.Griffiths/publications/assets/daks-2006.pdf)_ where fuzzy trust values include distrust, undistrust, untrust, and trust.
