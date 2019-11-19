---
tags: RWOT9, Meta-Platforms, Cooperative Economics
linkedin: www.linkedin.com/in/samuel-m-smith
email: sam@samuelsmith.org
---
# Decentralized Identity as a Meta-platform: How Cooperation Beats Aggregation

Authors:
[Michael Shea](mailto:michael.shea@thedinglegroup.com), 
[Samuel M. Smith Ph.D.](mailto:sam@samuelsmith.org), 
[Carsten Stöcker Ph.D.](mailto:carsten.stoecker@spherity.com)
, Collaborators:
[Juan Caballero Ph.D.](mailto:juan.caballero@spherity.com) (Editor), and
[Matt G. Condon](mailto:mattgcondon@gmail.com) 

version 1.6, 2019/11/19

github:  https://github.com/SmithSamuelM/rwot9-prague.git

## Abstract

A meta-platform is a platform that enables and fosters participant-controlled value transfer across and among other platforms and participants [[1]]; because platforms are a type of network, a meta-platform enables a network of network effects. This cooperation among platforms may be advantageous in comparison to centralized power (non-cooperation) in some contexts, particularly where a new network scaling law for meta-platforms can be argued to apply directly [[1]][[2]]. An *open, interoperable, portable, decentralized identity framework* is a prime candidate for becoming such a meta-platform and for leveraging this aggregate network effect.

Significant momentum has been developing behind a universal decentralized identity system based on open standards, including the W3C-supported decentralized identifier (DID) and verifiable credential (VC) standards [[14]][[21]]. Associated industry groups supporting this open standard include the Decentralized Identity Foundation (DIF), Sovrin Foundation, and the HyperLedger Foundation projects Indy, Aries, and Ursa [[15]][[16]][[18]][[19]][[20]].

The purpose of this paper is to foster awareness of the economic benefits of cooperation and the crucial role decentralized identity may play in unleashing new sources of value creation and transfer among cooperating platforms.


## Introduction


We are all familiar with many of the existing software **platforms** that are used today: in a consumer context, we speak of Google for searching, Amazon for purchasing goods, and Facebook or Twitter for social media exchanges.  In an enterprise/business context, the platforms are different: Salesforce for CRM, TradeLens for containerized shipping and logistics, and Amazon AWS for cloud-based IT services. In economics terminology, we could state generally that what drives the growth of a platform is the progressive reduction that platform offers its operators in transactions costs.  These transaction costs include triangulation, transfer, and trust [[5]]. For example, these costs include those incurred in matching buyers to sellers and in facilitating interactions or executing payments. This progressively lower per-transaction overhead accrues not just profitability but other forms of value to the platform itself via Metcalfe's law of network effects. Buyers and sellers on a platform get a significant reduction in transaction costs as well, from their point of view. The platform owners typically levy a fee on each transaction, as well as gaining market-wide access to large amounts of transaction data.

To date, in order to maximize network-effect-driven value, the "**platform game**" has been defined by a "winner takes all" rule book. The solitary focus of the platforms has been to grow the network as large as possible as quickly as possible. In a "winner takes all" world, this is the only road to survival. And the winners are few and powerful, and typically highly centralized, so they are therefore readily able to exploit their participants. Oddly, as the world has become dominated by a few powerful centralized platforms, entire industries have grown suspicious of this value proposition, and hence trust has diminished in would-be platforms and maneuvers to become one.  

We are no longer in a centralized world.  

With a proper meta-platform **counterbalancing** these centralizing tendencies, a "winner takes all" approach is no longer the only, or even, perhaps, the most sustainable model for establishing platforms.  This paper examines one blockchain-enabled technology and market driver for decentralization: an identity meta-platform. It describes how identity can provide the connective pathways (in software terms, the "protocol") that unlocks the potent force of data-flow decentralization and provides the foundation for the creation of a platform-of-platforms (what we will call a "meta-platform") that provides its participants with a new level of control and portability.  By making their participation portable to other platforms structured around the same protocol, these platforms **empower** the individual actor vis-a-vis the platform.

We will first discuss how the network scaling law for meta-platforms differs from the network scaling law traditionally seen on platforms today, and we will examine how the cooperating members of a decentralized identity meta-platform may out-compete traditional, centralized identity platforms (such as *login in with Google/Facebook* through which end-users access other services but in the process outsource control over their identity, data, metadata, and online relationships)[[1]].

Not only do macro-level advantages emerge for the cooperating platforms themselves, but it is also hard to overstate the micro-level **impact** decentralization of identity infrastructure can have for the **individual consumer**, who increasingly,  is hungry for ways to take back control. 

We will outline how participant control means that participants may form customized or bespoke virtual platforms of their own choosing. These virtual platforms could aggregate and/or amplify their identity's value across multiple platforms. Participant control better balances the interests of participants and platform operators. It provides a check on exploitation while increasing the value of the platform to both participants and operators due to increased attractiveness and cooperation [[7]][[13]]. Key points of this analysis at the participant/consumer level are outlined by this diagram:

![](https://i.imgur.com/dzgLuu1.png)

After this analysis, we will then return to the macro- and industry level to overview some concrete examples of **industry ecosystems** where this kind of identity meta-platform could address existing interoperability problems and provide real value, today. 

We will close with a summary of what has been presented, and make the **closing argument** that by establishing identity functions on a decentralized meta-platform protocol, many other technological and economic processes can develop powerful resistance against technological tendencies which have "centralized" data power into so few hands over the last two decades.

## Sidebar: The Cooperative Network of Networks Effect

A network "scaling law" describes how some property of the network changes as a function of the size of the network. In the case of platform networks, the relevant property is network value and the size is measured by the number of participants.  The most well-known network scaling law is **Metcalfe's Law** [[11]], according to which the value of the network to a single participant is proportional to the total number of participants. If we let ***a*** represent the average proportionality constant and ***N*** the number of participants then we have the following expression for the average value to a participant, ***v***, that is,

*v* = *a*⋅*N*

Furthermore the total value of the network, ***V***, is just the sum of the values from each of the ***N*** participants. This gives the following expression:

*V = v⋅N = a⋅N⋅N = a⋅N²*

Any property or trait of the network that scales by the square of the size of the network greatly amplifies even minor advantages accruing to relative size. This naturally creates a "race to scale" between competitors in any market that values highly such a network trait.  For this reason, the software industry values "**network effects**" highly, often applying the term anywhere Metcalfe's Law applies, even with major caveats, in calculations of valuation or market position. (For a discussion of the quantitative validation of this effect, See Smith, 2019[[1]]). 

### Metcalfe's scaling law of cooperative networks

The exponential increase in value described by Metcalfe's law poses the question: *What happens if two competing networks **cooperate** so that the combined network has a larger N than either network on its own*? To put it another way, can cooperation between two networks be as valuable as mergers or acquisitions between them?

Suppose that two networks of size ***N₁*** and ***N₂*** respectively were to combine by making their services interoperable (or ideally going further: cooperating and actively minimizing friction across the two networks). Individually, the *N₁* network's total value is,

*V₁ = a⋅N₁²*, 

and the *N₂* network's total value is

*V₂ = a⋅N₂²*.

After combining, the average value to a participant of either network *N₁* or *N₂* is due to the combined size of the new network, *N₁+N₂*. This becomes,

*v₁ = v₂ = a⋅( N₁+N₂)*.

The total value of network *N₁* becomes,

*V₁ = a⋅N₁⋅( N₁+N₂) = a⋅N₁²+a⋅N₁⋅N₂*.

Likewise the total value of network *N₂* becomes,

*V₂ = a⋅N₂⋅( N₁+N₂) = a⋅N₂²+a⋅N₁⋅N₂*.

We can thus imagine network-based business contexts where, merely by cooperating, each of the two networks has increased its total value by 

*a⋅N₁⋅N₂*.

This is a very valuable benefit of cooperation. The total value of the combined network is just the sum,

*V = V₁ + V₂ = a⋅N₁²+2⋅a⋅N₁⋅N₂+a⋅N₂² = a⋅(N₁+N₂)²*,

which is the same as one larger network of size *(N₁+N₂)*. The two networks can be of any size relative to each other. Suppose for example that *N₂* is twice the size of *N₁* The following diagram shows graphically the increased value due to cooperation, at this level of abstraction:

![](https://i.imgur.com/HI1uWIk.png)


The same analysis can be extended to multiple cooperating networks [[1]]. In the above example, the cooperative effect came from making the networks interoperable. This may (and traditionally does) pose a problem if both network's products are **competitive**. We discuss in detail elsewhere the lifetime value of cooperation for competing network products[[1]], but in broad strokes we could say it is a function of relative network size and degree of market saturation. 

### Cooperation in the calculus of business strategy

Despite the cooperative increase in total value, there may still be an **aversion to cooperation** due to the competitive nature of the products, culture, momentum, or other counterveiling tendencies. Economic "brute force" may still win out in many real-world contexts, where eliminating the risk of later antagonisms or conflicts or other benefits unrelated to network effects outweigh the costs and risks entailed by acquiring, eliminating, or predatorily subordinating a competitor.  But all other things being equal, cooperation might present most of the benefits of expansion with none of the costs or risks, when connecting two networks has more net gains than net losses.  Most economics of cooperation and sustainable competition (including between nations and industries, not just corporations and markets) require an accounting for scale that is not reductive and unidirectional, but include incentives to stay small, and disincentives (like bad public relations or regulatory consequences) to overambitious mergers.  For instance, in a situation where each network's  governance and maintenance are optimally manageable and efficient at a given size, yet both accrue all the benefits of expanding just by freely networking their domains, the latter is a natural choice.  

This "free" (and low-friction) value transfer across networks within the same context is what is normally considered when using the term '**cooperation**'. By 'context' we mean similar types of products and services. We call 'intra-contextual' this cooperation that results in intra-contextual value transfer between networks. Our goal should be the nurturing of these kinds of contexts, where data flow and interoperability can be maximized while still preserving the necessary privacy and rights of all players. 

The focus of this paper, however, is to address the question: What about cooperating networks where participants are "free" to transfer value between networks from different contexts? To be more explicit, what about networks that provide different, non-interoperable products and services? This is what we call inter-contextual (or more easily pronounced trans-contextual) network value transfer. **Trans-contextual value transfer**, when possible, has the potential to remove barriers to cooperation among perceived competitors. One might well pose the question, is trans-contextual value transfer even possible? And if so, to what extent can that value transfer be called "free"?  Emphasizing this categorical distinction (intra- vs inter-contextual) and accounting wholistically for the costs of overcoming non-interoperability in strategic planning might make a pivot towards more cooperative tactics more feasible in the short-term. 

In the next section, we will address these value transfers that may occur between contexts and context-specific products in terms of an analysis of benefits and costs for a business.


## Accounting for trust in current and future systems

A common approach to understanding business processes is via the model of **transaction costs**. In this tradition, business value is seen to come directly from reducing net transaction costs. Transaction costs may be grouped into three classes: triangulation, transfer, and trust [[4]][[5]]. Of these, trust may be the most important, especially for a platform or meta-platform. Without trust, platforms, as well as physical and digital value chains, cannot develop to maturity.  Trust and reputation are truly paramount to commerce as we know it; they are the currency of brands and the building blocks of marketplaces.

### The "trust tax" stabilizing and structuring value chains today

The requisite level of trust for most commercial and business processes has been historically difficult, and costly, to establish. Trusted suppliers are thoughtfully selected and managed, as well as monitored and certified for quality, reliability and consistency. Regulators demand certifications and audits to ensure that best practices are followed, and companies such as TÜV, Underwriters Laboratories or Intertek conduct inspections and provide quality certifications. At the end of the value chain, customers purchase products because they trust the quality of the brand, which is the key differentiator for many companies. The difference in price between a widely-known and a lesser-known brand, or between a national brand and a more local brand, illustrates how at every point in the chain, higher levels of trust come at a notable **premium**.

This premium or “trust tax” that consumers pay to trusted global brands is levied all the way upstream, throughout the brands' supply chains to their suppliers. From the use of “conflict-free” raw materials, to Six Sigma manufacturing practices, to Independent Standards Organization (ISO) certifications, to the validity of shipping or purchase orders – the work of verifying all these characteristics "entity to entity" requires endless chain-letters of paperwork, endless e-mails and phone calls, and costly site visits and audits. These cumbersome activities reduce productivity and efficiency throughout the economy, costs which are ultimately passed down to consumers.  

The immense volumes of data generated by global supply chains has other effects as well, though. If such data were properly mined and analyzed in a verifiable way, the resulting analysis would help to establish the trustworthiness of an **entire** value chain process and its resulting products. However, assembling and cleaning the requisite data set for such an analytical process requires numerous manual interventions and the involvement of many parties across multiple platforms. Furthermore, these kinds of audits are usually done by neutral consortia or by outside firms whose incentives do not touch the competition in the relevant markets, either of which could feasibly centralize data access across a market without triggering competitive defenses. Competition for control of such consortia, or distrust of such profit-driven centralized firms, can slow down integration of such audits, which adds yet more costs. In few cases is this kind of deep business intelligence analysis practicable. 

### Identity and reputation systems as trust brokerages

What makes the kind of end-to-end analytics described above so rare is that too much of the requisite data is **horded** and **guarded** in siloes, without much concern for the best interest of a healthy trust market, or for that matter any other market-wide concern.  Trust is rarely studied at market scale, and relevant data sets for doing so have been hard to amass. It is our belief that if such a bird's-eye perspective could be attained, there would be many net benefits to empowering individual data subjects to hold and reuse more of the data on which their reputation is calculated. Doing so would allow "credential-based" (or, to use a buzzword du jour, "data-driven") trust among participants that have never met before.   

But doing so requires loosening the grip most identity systems currently have on the **credentials** they already use (*internally*) to gage and estimate the trustworthiness of their participants, i.e., to **calculate "reputations"** for all participants in their networks.  The same credentials that identity systems use to do this, if handed over to the participants, would allow them to prove their trustworthiness to other participants of their own choosing or on other platforms.  In this way, the raw material of reputation systems would take on a different kind of value, circulating more widely and being reused again and again anywhere a given subject can prove the validity of those credentials, i.e., anywhere they can prove their own identity.

Traditionally, **identity and reputation** are seen as **interdependent functions** of one system, or even as two sides of one coin. After all, a reputation is meaningless without an underlying identity and an identity is valueless without a credible reputation. After a few decades of increasingly centralized digital identity systems, we have come to take it for granted that identity companies should naturally keep a close grip on reputation services which they are especially positioned to provide for others.  Indeed, the colloquial terminology can even be an impediment to grasping this division of labor where credentials and tracking add up to valuable user analytics sold to the highest bidder. Because identity systems typically include credentials of some form that encode reputation as data, the software industry usually refers to credentialed identity systems simply as "identity" systems, not as "identity and reputation" systems. When the calculation of reputations becomes primarily behavior-based rather than credential-based, these systems are typically referred to as "reputation systems" rather than identity systems, even though they are still dependent on an underlying identity system and its credentials. 

For our purposes here, we view all of these traditional identity and reputation systems as existing on a spectrum of **trust conveyance**. While making credentials more portable across organizational boundaries can incur its own costs and complications, it has a curious network-of-networks effect whereby all parties benefit from more information and more possible *because trustworthy* connections. Maximizing trust conveyance works out best for everyone except for today's monopolists of trust. 

Most importantly, a decentralized identity and reputation system enables trust to be **transitive between contexts** to some degree. This additional dimension of cooperative network-of-network effects brings trust transaction costs down generally.  This "knock-on effect" can be quantified by adding a transitivity factor to the equations above. This transitive formulation is provided in detail in [[1]].

What's more, organizing trust in a conveyance-maximizing way for individual participants also allows for the trust or credibility of all data for auditors and platforms. Situations where trust data is maximally portable enables end-to-end (**E2E**) verifiable audit trails along a given value chain even if it crosses many organizational boundaries. "Maximally portable" might sound like a high bar or systemwide buy-in, but it is readily attainable anywhere (and for as long as) all parties can be incentivized to minimally uphold data and control interoperability.  

### Imagining a trust landscape where reputation data flows more freely

A system-wide **trust mechanism** along these lines can be seen at work in the decentralized identifiers and verifiable credentials of the sort standardized by the W3C consortium, in combination with consequently interoperable agents, interaction protocols and credential-storing wallets.  We call this as a "meta-platform," because it enables participants to engage in trusted interactions in a wider ecosystem and maximizes intra-network value transfers. 

This approach can **slash the “trust tax”** at every level, starting with participants agreeing to implement and follow the existing decentralized identity standards and their future developments. This decentralized approach does not build another aggregator platfom or another proprietary blockchain solution, but rather a participant-controlled decentralized meta-platform. Opinions vary as to what this participant control could or likely would look like, but some proponents of decentralization argue that bottom-up governance is easier to institute in these kinds of meta-networks [[1]].

Because the primary value of a platform is to reduce transactions costs for all parties, a decentralized identity system makes the building-blocks of reputation more portable and has the potential to **significantly reduce** average, net, and/or aggregrate trust transaction costs in many different marketplaces and other industrial contexts. This may make whole families of transactions viable that were not viable before, or create new kinds of commerce (and perhaps even self-regulating ones). This increases the value of the associated platforms per participant and lowers the critical platform size (see below). This further accelerates network-of-network effects.

## Concrete examples of trust savings from different scales and contexts

### On-boarding costs

One early application of Metcalfe’s law in the business models of the ascendant communications industries was to show that even large upfront network connection costs would eventually be overcome by the exponential increase in value due to network size. The "**break-even point**" was the point in time where the growing network's value to a participant overcame (due to network effects) the cost of joining the network.  The size a network has reached at this point is called the "**critical network size**". 

We could adapt this terminology to today's platform economics by pointing out that the major upfront cost of connecting to a platform is not the internet connection itself but the **on-boarding cost** of creating an account with login credentials and provisioning electronic payment, with concomitant identity verification needs. Unbeknownst to most users, this requires the participation of many companies and market-wide mechanisms (from insurance to credit cards to underwriters to regulatory bodies to infrastructure providers), all of whose costs are baked into our current networks of global commerce. But also baked into this system is a unified user experience of convenience and relative simplicity.

One of the problems with decentralized blockchain technology is that in general it has a ways left to go before it can compete with this simple and convenient **user experience**. In terms of "on-boarding" a user to a new platform or network, many radically peer-to-peer digital networks or blockchain systems  have quite high on-boarding costs. In the case of peer-to-peer technologies, there can be a very steep learning curve and "UX deficit" relative to increasingly convenient and intuitive commercial software.  In the case of blockchain and cryptocurrencies networks, participants have to contend with difficulty in managing keys, increased regulatory friction, and a level of  complexity quite high by contemporary standards. The plethora of competing (and thus, at least to date, largely non-cooperative) blockchain platforms only heightens the confusion. The result is that critical platform size may be significantly increased, with the worrisome effect that many blockchain platforms may never reach their critical size (or even a "break-even point" at which their scale and overhead are practical for their intended use cases).

A decentralized identity meta-platform allows those on-boarding costs to be **amortized** across every platform a participant chooses to join. This potentially lowers the critical platform size (and the break-even point) for the participant on each of the sub-platforms. None of this directly helps to unify user experience, but perhaps on the whole this "transitive onboarding" can offer some incentives towards cooperation between platforms, in design terms at least. All of this could readily accelerate network-of-network effects and overcome some of the inefficiencies created by competition.
  
### IoT Combinatorics and the 4th Industrial Revolution

We have been speaking about a network-of-networks effect in positive terms, but from the perspective of communications, it is also a dizzying escalation of the scale of some technical problems, in particular that of **addressability**. Today, the Internet is probably best described as a network comprised of all interconnected objects, of which the lion's share were traditionally human users and computers. When you add in the so-called Internet of Things (IoT), the number of addressable elements is reaching the tens of billions already, with many analyses predicting a tenfold increase within a decade. 

The resulting "combinatorics" (or "matchmaking complexity") of possible connections between any given subgroup is an impossibly large number. Yet in today’s user journeys or business environments, agents (whether human, machine, or software) increasingly need to access, control or transact with a diverse group of these interconnected objects to achieve their goals in both the digital and physical worlds. This requires a straightforward and ubiquitous method to **address, verify and connect** these elements together.

> There are about 30 billion devices connected to the internet already. These devices are managed by thousands and thousands of different platforms. For the majority of the devices, it is quite unpredictable in which context they will be used: changes of ownership, geography, use case, machine-to-machine interactions, and other factors are inherently unpredictable. There are (N×(N-1))/2 possible peer-to-peer (P2P) connections among the devices possible, i.e. O(n²). This results in ~10^21 possible connections. There are O(n³) possible connections for connecting three systems and so forth. 

At some point, this staggering network-of-networks **complexity** will be equally pertinent in all business verticals, but today it most keenly felt in businesses dependent on supply chain management because of the large number of actors and multi-vendor components likely to be involved there. The main impediment is that it is cumbersome for each agent to have innate knowledge of the wide assortment of different addressing nomenclatures and protocols. At some point, it could go from impracticable to categorically impossible.

Human or object identities are stored in multiple centralized or federated systems such as a government, ERP, IoT or manufacturing systems. From the standpoint of cryptography-based systems of trust and/or verification, each of these **centralized authorities** serves as its own **root of trust**, tightly controlling all identities' access to one another's credentials and trust information. An object trailing along a supply chain is interacting with multiple systems and platforms. Consequently, a new actor in any give value chain has no method to independently validate credentials of a human or attributes of an object, except through the locally-governing central authority.  Even then, the audit trail they can access rarely extends back much further than the jurisdiction of that authority unless data has been forwarded along in parallel to the human or object's trajectory. 

Therefore, a trust verification system and associated interoperable meta-platform protocol, built on some kind of **universal addressing system** must be utilized. To be a truly global solution, easy-to-use and still safe from hacking, censorship, and other sovereign interference, such a meta-platform scheme must be independent from any vendor-defined naming API or otherwise centralized namespace, yet they usually need to be one-to-one mappable onto such APIs and namespaces. 

A participant-controlled meta-platform based on decentralized identity solves the problem of addressability and trust verification across participants involved in a given value chain transaction. The potential of enabling these devices to interact across a network-of-networks is inconceivably broad in scope.  It may well prove to be many orders of magnitude broader than Facebook as an **aggregator** for human interactions and an **enabler** of new connections and networks.
  
Such a platform will be of particular value for the **Fourth Industrial Revolution** (4IR), i.e. the fusion of technology bridging the biological, physical and digital spheres across industrial domains and societies. 4IR is moving our world into one big convoluted cyber-physical system in which everything is connected with everything else. In this digital fabric there is ubiquitous network connectivity among IoT devices and digital agents establishing dynamically defined cooperation across interlinked digital value chains. We believe that an identity meta-platform is a prerequisite to establish trust and cyber-physical security for dynamically defined cooperation in the 4IR. 

### Secure Logistics Systems

Multiple global logistics consortia are trying to establish so-called "**secure logistics systems**" for verifiable shipment tracking, process automation and verifiable business transactions across multiple entities. In many ways, this hinges on a similar problem of scale and addressability: how can all these actors across the world find each other, verify each other, and share information securely and intelligibly?

Despite the fact that global logistics companies are attempting to leverage  decentralized technology, they are still constrained by their confined partner-system/ecosystem boundaries that prevent full **decentralization** in their implementations or substantial **cooperation** on a global scale to foster interoperable standards. 

Let's assume the following scenario for verifiable logistics transactions which is based on a real world example:
- UAE logistics is using a decentralized Hyperledger implementation
- EU logistics is using a consortium-governed Ethereum Quorom system  
- Nordic logistics is using Maersk/IBM's TradeLens 

In this scenario, the three logistics companies have challenges to establish transactions across entities on the three different platforms. A typical approach is either A.) to convince the other partners to join one's own platform or, B.) to implement complex federation gateways between platforms.  This latter, it's worth noting, adds another player (the gateway) to the list of parties that need to be trusted, and potentially more transaction costs.

An identity-based meta-platform has the potential to solve this problem as it can establish **trust** among the participant entities, **verifiability** along the supply chain, and **externally** trustworthy business transactions:
- Credential-based trust for on-boarding a previously-unknown actor
- Verifiable consent and business transactions
- Data provenance for trace-and-track along a logistics supply chain

Here, as throughout this paper, the importance of **open standards** (arrived at by transparent governance) is hard to overstate. An identity meta-platform structured by such standards might well encourage and incentivize similar standards to develop as "on-ramps" to such a system, of the kind the accelerate information-sharing elsewhere in the international supply chains that are the economic basis of international logistics.

## On Competition in Meta-platform Ecosystems

A participant-owned meta-platform governed by open standards has **mechanisms** or "**antibodies**" that deter a single entity from controlling it, creating a lock-in, or monetizing transaction data. The value transfer within the interoperable meta-platform ecosystem is controlled by the  participants. Furthermore, there is no **administrator** or **aggregator**, at least not at the meta-platform level, that controls value and monetizes transaction margins. 

As a consequence, there is no real foothold at the core of the meta-platform for a single party to monetize or establish monopolistic control.  Instead, these kind of organic, cooperation-incentivized conditions are favorable to:
- Authentic sharing economy
- Interoperability, whereby previously unknown parties can transact in a trusted way
- Economically viable nano-transactions (lower overheads and transaction costs)
- Secure, business transactions, verifiable to a relatively high degree to outside parties without special access or permissions

One illustrative example can be seen in this projection about the mobility ecosystems of the near future:
![](https://i.imgur.com/fQpyvCz.png)

It’s important to note how different this model is from current models (for example, the centralized ride-sharing platforms of Uber and Lyft). Autonomous vehicles eliminate the cost of human drivers, while decentralized meta-platforms eliminate the middleman that matches customers with rides, charges a transaction fee and sets terms and conditions.

Corporations will establish successful business models **at the edge** of this kind of meta-platform not by competing on margins or efficiency or proprietary IP, but by instead competing on
- User Experience
- Algorithms and Analytics
- Implementation and Services
- Hardware and Infrastructure

![](https://i.imgur.com/3Z15EQk.png)

Mobility on a decentralized meta-platform may also become one of the most visible examples of a true sharing economy. It might be more precise to call this a **zero-marginal-cost economy**, because the owners of everything from homes to cars could, with less effort and risk, rent them out when they are not in use; this would naturally drive the marginal cost of most overnight stays or trips closer and closer to zero over time.  In a world so molded by **cooperative economic drivers**, trust, reputation and sustainablity become valuable and monetizable as a less zero-sum form of capital. 

At a macro level, the cooperative approach using portable and trans-contextual trust as the primary vehicle for trans-contextual value transfer also makes the associated economic systems more **resilient** in the event of shocks to sub-segments. Multiple independent but cooperating networks contribute network-effect value to each other. This contributed value bolsters the network and smooths out the effect of a shock to a given sub-network. This is a decentralized version of so-called "ergodic" economics [[22]], in that it leverages participant-controlled cooperative network-of-network effects to reallocate or share value.  

## Identity for all things in a circular economy

The resilience mentioned above might seem a macroeconomic abstraction, but it is also linked to a more literal kind of resilience: that of a more **sustainable economics**. As humanity begins to transition to a more circular economy, identity for manufactured things along their entire life-cycle and among all potential actors involved comes to be of utmost importance. As alternatives to a **circular economy** grow more scarce, unreliable, and progressively more expensive, circularity will rapidly pivot from abstract virtue to concrete value, and the circular economy's *data* needs will similarly accrue urgency.

A circular economy is an economic system aimed at **eliminating waste** and the maximally **continuous use** of resources. Circular systems employ recycling, reuse remanufacturing and refurbishment to create a closed system, minimizing the use of resource inputs and the output of waste. This regenerative approach is in contrast to the traditional linear economy, which has a 'take, make, dispose' model of production.  As extraction and disposal costs both climb, we will need more verbs than just "make".  

Lowering trust transaction costs is a critical enabler for extending a sharing economy to lower-value transactions, which in turn leads to more reuse and less waste. These **economic drivers** to more reuse, less waste and spare unused capacity are the drivers/enablers for moving towards more circularity throughout the economy.

To enable truly restorative and regenerative economy by design, circular systems need a digital representation such as a ***"digital twin"*** for any given entity. The term comes originally from iterative design processes in military and aerospace engineering, where prototypes, data models, and other kinds of information have to be painstakingly versioned and tracked to allow more iteration, more testing, and more data modelling within a finite budget, particularly for precise and critical components.  In the 21st century, it has come to mean various ways of linking, bundling, or making persistent diverse forms of big and small data and metadata, particularly in a decentralized context where that data might be generated and stored across many networks and contexts with little persistant access to one another. Enabling this kind of global and persistent form of digital twin was a key goal of an earlier paper worked on by some of this paper's author, which called for the creation of a "DID for everything" [[17]].

To enable circularity, this kind of persistent digital twin must be accessible by any (permissioned) actor along a supply chain to provide verifiable data provenance.  This **provenance** needs to include legible and complete information about materials and lifecycle that enable safe, exhaustive, and efficient recycling or refurbishing; it needs to outlive the utility of the artefect, and in many cases even the company that manufactured it. To be a truly "circular" artefact, its would-be recyclers and refurbishers need access to a "verifiable story for every thing".

Of course, this takes place at an atomic level, and scoping the process of getting from individual things being circular to all things being circular requires another combinatoric tour of infinitesimal potential interactions.  But along the way from first circular things to entire circular economy, that **unthinkably large transition** could also be sped along by the same infrastructure described above: a nurturing of cooperative networks effect, and a trust framework in the form of an identity meta-platform for circular things.

The cryptographically secure digital twins provided by the meta-platform enable a systemic, algorithmic **digital fabric** to orchestrate the circular system. All kinds of knock-on effects and organic marketplaces could arise from such a regime of materials tracking:
- Everything with a Decentralized Identifier is connected to a persistent data store hosting verifiable life cycle data.
- Any random actor can independently verify the life cycle assertions of a thing, literally “its complete story”.
- Back-to-birth traceability of manufactured things is needed to minimize avoidable pollution and to design out waste from manufacturing processes while keeping materials in use as long as possible
- Monetization and incentivization of existing problems could begin in the short term, addressing machine life cycle, supply chain provenance or 3rd party risk management through an automation of audit processes on demand.
- Orchestration of circular systems with algorithms running on top of the digital twins for monitoring, optimization and transitioning to a restorative and regenerative economy.

![](https://i.imgur.com/BlujaPM.png)


We believe that a connection between the meta-platform's cooperative network effects and a broader circular economy should be explored as it could deliver new forms of value for society as a whole. It might even garner enough immediate value for governments and huge corporations that infrastructural investments in that direction could appeal to them today.


## Conclusion

In this paper we layed out some compelling **economic reasons** for corporations to join the cooperative meta-platform in question and perhaps many other such meta-platforms yet to come.  At first glance, it might seem to some an impractical upfront infrastructural investment that would run counter to the incentives of existing power structures. Others might see such decentralization as unrealistic in a time when the biggest companies in the world are low-overhead tech conglomerates dominating platforms that did not exist twenty years ago. But from another perspective, this recent excess of monopolistic tendencies and winner-take-all platform plays might be a growing pain, or a pendulum swing, after which we return to a drastically different mood and set of economic norms.

Indeed, many would argue the **pendulum** has been swinging throughout the history of technology.  Many *leveling technologies*, such as communication networks, first started as decentralized but then become more centralized over time with the associated value capture eventually becoming concentrated into a few very large business entities with higher rates of value extraction. This historically cyclical behavior is well-documented in *The  Square and the Tower* and *the Master Switch* [[9]][[10]]. One can argue that the internet which started as a great leveler due to decentralized networking has now resulted in most of its value being concentrated in a handful of companies, namely, Google, Apple, Facebook, Amazon, and Microsoft, each with valuations near one trillion dollars. Once centralization occurs, innovation and value creation decrease and value extraction increases to the detriment of the average user, according to either price or diversity metrics.

One way to combat such centralization is with **regulation**. The breakup of AT&T and the injunction against Microsoft's predatory bundling are two largely successful examples of a regulatory approach to restoring more decentralization.  Both debatably resulted in demonstrably more innovation, lower costs and overall greater benefits to telecommunication users and operating system ecosystems. Regulatory approaches, however, often come with deleterious or unpopular side-effects. Many prefer more market-driven decentralization when multiple approaches are available. While the technology and its comcomitant economics are still largely immature, appropriate applications of blockchain technology may enable such **market drivers**. The authors agree that blockchain-anchored decentralized identity infrastructure is one such application. The transcontextual cooperative network-of-networks effects enabled by a participant controlled identity meta-platform may provide sufficient market force to forever break this cycle of centralization.

## Glossary

A. Platform - A platform is a business based on enabling value-creating interactions between external producers and consumers.  The platform provides an open, participative infrastructure for these interactions and sets governance conditions for them. 

The platform’s overarching purpose: to consummate matches among users and facilitate the exchange of goods, services,  or social currency, thereby enabling , value creation for all participants.

Platforms create value by using resources they don’t own or control, as such they can grow much faster than traditional organizations.

(Source: Parker, Alstyne & Choudary, Platform Revolution [[6]])

B. Intra-context - transfer of value within the same set of applied products, services and network of participants.

C. Inter-context - transfer of value across different applied products, services and networks of participants. (aka "transcontext")

## References

[1]. Smith, Samuel M., Meta-Platforms and Cooperative Network-of-Networks Effects: Why Decentralized Platforms Will Eat Centralized Platforms. 2019/03/25 https://medium.com/selfrule/meta-platforms-and-cooperative-network-of-networks-effects-6e61eb15c586

[1]: https://medium.com/selfrule/meta-platforms-and-cooperative-network-of-networks-effects-6e61eb15c586

[2]. Thomson, Ben, Aggregation Theory. https://stratechery.com/aggregation-theory/

[2]: https://stratechery.com/aggregation-theory/

[3]. Cameron, Kim, The Laws of Identity. http://www.identityblog.com/stories/2005/05/13/TheLawsOfIdentity.pdf

[3]: http://www.identityblog.com/stories/2005/05/13/TheLawsOfIdentity.pdf

[4]. EconTalk Blog Sharing Transactions Costs and Tomorrow 3.0. http://www.econtalk.org/michael-munger-on-sharing-transaction-costs-and-tomorrow-3-0/

[4]: http://www.econtalk.org/michael-munger-on-sharing-transaction-costs-and-tomorrow-3-0/

[5]. M. C. Munger, “Tomorrow 3.0: Transaction costs and the sharing economy,” Cambridge University Press, 2018.

[5]: https://www.amazon.com/Tomorrow-3-0-Transaction-Cambridge-Economics/dp/1108447341

[6]. Geoffrey G. Parker, Marshall W. Van Alstyne & Sangeet Paul Choudary, Platform Revolution: How Networked Markets Are Transforming the Economy—and How to Make Them Work for You.

[6]: https://www.amazon.com/Platform-Revolution-Networked-Markets-Transforming/dp/B01DDX6VB2

[7]. Google's paid search ads are a 'shakedown' Basecamp CEO says. https://www.cnbc.com/2019/09/04/google-paid-search-ads-shakedown-basecamp-ceo-says.html

[7]: https://www.cnbc.com/2019/09/04/google-paid-search-ads-shakedown-basecamp-ceo-says.html


[8]. C. Anderson, “The Long Tail,” Wired, 2004/10/01 https://www.wired.com/2004/10/tail/

[8]: https://www.wired.com/2004/10/tail/


[9]. N. Ferguson, “The square and the tower: Networks and power, from the freemasons to Facebook,” Penguin Books, 2019.

[9]: https://www.amazon.com/Square-Tower-Networks-Freemasons-Facebook/dp/0735222932

[10]. Wu, T. “The Master Switch: The Rise and Fall of Information Empires” Random House, 2010. 

[10]: https://www.amazon.com/Master-Switch-Rise-Information-Empires-ebook/dp/B003F3PKTK

[11]. B. Metcalfe, “Metcalfe’s law after 40 years of ethernet,” Computer, vol. 46, no. 12, pp. 26–31, 2013

[11]: https://ieeexplore.ieee.org/document/6636305


[12]. T. Pearson, “Markets Are Eating The World,” RibbonFarm, 2019/02/18 https://www.ribbonfarm.com/2019/02/28/markets-are-eating-the-world/

[12]: https://www.ribbonfarm.com/2019/02/28/markets-are-eating-the-world/

[13]. K. J. Erickson, “The Future Of Network Effects: Tokenization and the End of Extraction,” Medium.com, 2018/07/17 https://medium.com/public-market/the-future-of-network-effects-tokenization-and-the-end-of-extraction-a0f895639ffb

[13]: https://medium.com/public-market/the-future-of-network-effects-tokenization-and-the-end-of-extraction-a0f895639ffb

[14]. “Decentralized Identifiers (DIDs),” W3C Draft Community Group Report 23 August 2018, https://w3c-ccg.github.io/did-spec/

[14]: https://w3c-ccg.github.io/did-spec/

[15].Decentralized Identity Foundation (DIF) http://identity.foundation

[15]: http://identity.foundation

[16]. “Sovrin: A Protocol and Token for Self- Sovereign Identity and Decentralized Trust,” Sovrin.org, 2018/01/01 https://sovrin.org/wp-content/uploads/2018/03/Sovrin-Protocol-and-Token-White-Paper.pdf

[16]: https://sovrin.org/wp-content/uploads/2018/03/Sovrin-Protocol-and-Token-White-Paper.pdf

[17]. Shaun Conway, Andrew Hughes, Moses Ma, Jack Poole, Martin Riedel, Samuel M. Smith Ph.D., and Carsten Stöcker. “A DID for Everything: Attribution, Verification and Provenance for Entities and Data Items,” written at RWOT 7 but finalized 2018/09/26.  https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/A_DID_for_everything.pdf

[17]: https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/A_DID_for_everything.pdf

[18]. HyperLedger Indy Project. https://www.hyperledger.org/projects/hyperledger-indy

[18]: https://www.hyperledger.org/projects/hyperledger-indy

[19]. HyperLedger Aries Project. 
https://www.hyperledger.org/projects/aries

[19]: https://www.hyperledger.org/projects/aries

[20]. Hyperledger Ursa Project. https://www.hyperledger.org/projects/ursa

[20]: https://www.hyperledger.org/projects/ursa

[21]. W3C Verifiable Credentials Data Model. https://www.w3.org/TR/vc-data-model/

[21]: https://www.w3.org/TR/vc-data-model/

[22]. Ergodic Economics. https://ergodicityeconomics.com/lecture-notes/

[22]: https://ergodicityeconomics.com/lecture-notes/