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
[Juan Caballero Ph.D.](mailto:caballerojuan@pm.me) (Editor), and
[Matt G. Condon](mailto:mattgcondon@gmail.com) 

version 0.8, 2019/10/21

github:  https://github.com/SmithSamuelM/rwot9-prague.git

## Abstract

A meta-platform is a platform that enables and fosters participant-controlled value transfer across and among other platforms and participants [[1]]. Because platforms are a type of network, a meta-platform enables a network of network effects. This cooperation among platforms may be advantageous in comparison to centralized power (non-cooperation) in some context, particularly where a new network scaling law for meta-platforms can be argued to apply directly [[1]][[2]]. An *open, interoperable, portable, decentralized identity framework* is a prime candidate for a meta-platform leveraging this aggregate network effect.

Significant momentum has been developing behind a universal decentralized identity system based on open standards, including the W3C-supported decentralized identifier (DID) and verifiable credential (VC) standards [[14]][[21]]. Associated industry groups supporting this open standard include the Decentralized Identity Foundation (DIF), Sovrin Foundation, and the HyperLedger Foundation projects Indy, Aries, and Ursa [[15]][[16]][[18]][[19]][[20]].

The purpose of this paper is to foster awareness of the economic benefits of cooperation and the crucial role decentralized identity may play in unleashing new sources of value creation and transfer among cooperating platforms.


## Introduction

*(introducing the concept of meta-platforms, key features, key value propositions, enabling technology. Then outline the paper - exploration of triangulation, transfer and trust, examples of existing networks of networks where meta-platforms can demonstrate their value, counter forces (Malthusian Trap), summary)* to be removed later

*Edited Content* (*Further-edited by Juan 10/15/19 only for style and clarity, not content)

We are all familiar with many of the existing software platforms that are used today: in a consumer context, we speak of Google for searching, Amazon for purchasing goods, and Facebook or Twitter for social media exchanges.  In an enterprise/business context, the platforms are different: Salesforce for CRM, TradeLens for containerized shipping and logistics, and Amazon AWS for cloud-based IT services.  What drives the growth of a platform is the reduction the platform offers in transactions costs that accrue value to the platform via Metcalfe's law network effects. These transaction costs include triangulation, transfer, and trust [[5]]. For example these include the costs of matching buyers to sellers and facilitating interactions and payment.   Buyers and sellers on the platform get a significant reduction in transaction costs, The platform owners get a fee on each transaction, as well as market-wide access to large amounts of transaction data.

To date,  in order to maximize network effect driven value, the "platform game" has been defined by a "winner takes all" rule book. The solitary focus of the platforms has been to grow the network as large as possible as fast as possible. In a "winner takes all" world, this is the only road to survival. And the winner's are few and powerful (centralized) and therefore able to exploit their participants. Oddly, as the world has become dominated by a few powerful centralized platforms entire industries have grown suspicious of this value proposition, and hence trust has diminished.  

We are no longer in a centralized world.  

With a proper meta-platform counterbalancing these centralizing tendencies, a "winner takes all" approach is no longer the only, or even perhaps, the most sustainable model for establishing platforms.  This paper examines one blockchain-enabled technology and market driver for decentralization: an identity meta-platform. It describes how identity can provide the connective pathways (in software terms, the "protocol") that unlocks the potent force of data-flow decentralization and provides the foundation for the creation of a platform-of-platforms (what we call the "meta-platform") that provides its participants with a new level of control and portability.  By making their participation portable to other platforms structured around the same protocol, these platforms empower the individual actor vis-a-vis the platform.

We will first discuss how the network scaling law for meta-platforms differs from the network scaling traditionally seen on platforms today, and we will examine why the cooperating members of a decentralized identity meta-platform may "eat" (out-compete) centralized identity platforms [[1]]. A centralized identity is controlled by the platform such as login with Facebook or Google.

We will outline how participant control means that participants may form customized or bespoke virtual platforms of their own choosing. These virtual platforms aggregate and/or amplify their value across multiple platforms. Participant control better balances the interests of participants and platform operators. It provides a check on exploitation while increasing the value of the platform to both participants and operators due to increased attractiveness [[7]][[13]].

![](https://i.imgur.com/dzgLuu1.png)

We will then review examples of industry ecosystems where this kind of identity meta-platform will address existing inter-operability problems and provide real value, today.

We will close with a summary of what has been presented, and the closing argument that by establishing identity functions on a decentralized meta-platform protocol, many other technological and economic processes can develop powerful resistance against technological tendencies which "centralize" data power.

## Cooperative Network of Networks Effect

A network scaling law describes how some property of the network changes as a function of the size of the network. In the case of platform networks, the relevant property is network value and the size is measured by the number of participants.  The most well-known network scaling law is Metcalfe's Law [[11]], according to which the value of the network to a single participant is proportional to the total number of participants. If we let ***a*** represent the average proportionality constant and ***N*** the number of participants then we have the following expression for the average value to a participant, ***v***, that is,

*v* = *a*⋅*N*

Furthermore the total value of the network, ***V***, is just the sum of the values from each of the ***N*** participants. This gives the following expression:

*V = v⋅N = a⋅N⋅N = a⋅N²*

Any property or trait of the network that scales by the square of the size of the network greatly amplifies even minor advantages accruing to relative size. This naturally creates a "race to scale" between competitors in any market that values highly such a network trait.  For this reason, the software industry values "network effects" highly, often applying the term anywhere Metcalf's Law applies, even with major caveats, in calculations of valuation or market position. (For a discussion of the quantitative validation of this effect, See Smith, 2019[[1]]). 

### Metcalfe law scaling of cooperative networks

The exponential increase in value described by Metcalfe's law poses the question: *What happens if two competing networks cooperate so that the combined network has a larger N than either network on its own*? To put it another way, can cooperations between two networks be as valuable as mergers or acquisitions between them?

Suppose that two networks of size ***N₁*** and ***N₂*** respectively were to combine. by making their services interoperable (cooperate). Individually the *N₁* network's total value is,

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

This is a very valuable benefit of cooperation.  The total value of the combined network is just the sum,

*V = V₁ + V₂ = a⋅N₁²+2⋅a⋅N₁⋅N₂+a⋅N₂² = a⋅(N₁+N₂)²*,

which is the same as one larger network of size *(N₁+N₂)*. The two networks can be of any size relative to each other. Suppose for example that *N₂* is twice the size of *N₁* The following diagram shows graphically the increased value due to cooperation, at this level of abstraction:


![](https://i.imgur.com/BWV1KSe.png)

The same analysis can be extended to multiple cooperating networks [[1]]. In the above example, the cooperative effect came from making the networks interoperable. This may (and traditionally does) pose a problem if both network's products are competitive. The lifetime value of cooperation for competing network products is discussed here [[1]]. It is a function of relative network size and degree of market saturation. 

Despite the cooperative increase in total value, there may still be aversion to cooperation due to the competitive nature of the products, culture, momentum, or other counterveiling tendencies. Economic "brute force" may still win out in many real-world contexts, where eliminating the risk of later antagonisms or conflicts or other benefits unrelated to network effects outweigh the costs and risks entailed by acquiring, eliminating, or predatorily subordinating a competitor.  But all other things being equal, cooperation might present most of the benefits of expansion with none of the costs or risks, when connecting two networks has more net gains than net losses.  Most economics of cooperation and sustainable competition (including between nations and industries, not just corporations and markets) require an accounting for scale that is not reductive and unidirectional, but include incentives to stay small, and disincentives (like bad public relations or regulatory consequences) to overambitious mergers.  For instance, in a situation where each network's  governance and maintenance are optimally manageable and efficient at a given size, yet both accrue all the benefits of expanding just by freely networking their domains, the latter is a natural choice. Our goal should be the nurturing of these kinds of contexts, where data flow and interoperability can be maximized while still preserving the necessary privacies and rights of all players.  

This free value transfer across networks (intra-network value transfer) is largely the focus of this paper, and the building block of a valuable meta-platform.   However this poses the question: What about cooperating networks where participants are free to transfer value between networks, yet must use different, non-interoperable products to do so? Is that even possible, and if so, can one call that value transfer "free"? We call this type of value transfer trans- or inter-contextual value transfer, because it incurs additional costs in traversing single-network products. Emphasizing this categorical distinction and a holistic accounting for these non-interoperability costs in strategic planning might disincentivize or otherwise reduce some barriers to cooperation. In the next section we will talk about value transfer than may occur between contexts and context-specific products.


## Trust transaction costs in current systems

A common approach to understanding business processes is via the model of transaction costs; business value comes from reducing net transaction costs. Transaction costs may be grouped into three classes: triangulation, transfer, and trust [[4]][[5]]. Of these, trust may be the most important, especially for a meta-platform. Without trust, platforms as well as physical and digital value chains cannot exist.

However, the requisite level of trust for most business processes has been historically difficult, and costly, to establish. Trusted suppliers are thoughtfully selected and managed, as well as monitored and certified for quality, reliability and consistency. Regulators demand certifications and audits to ensure that best practices are followed, and companies such as TÜV, Underwriters Laboratories or Intertek conduct inspections and provide quality certifications. At the end of the value chain, customers purchase products because they trust the quality of the brand, which is the key differentiator for many companies. The difference in price between a widely-known and a lesser-known brand, or between a national brand and a more local brand, illustrates how at every point in the chain, higher levels of trust come at a notable premium.

This premium or “trust tax” that consumers pay to trusted global brands is passed all the way upstream, throughout the brands' supplychains to their suppliers. From the use of “conflict-free” raw materials, to Six Sigma manufacturing practices, to Independent Standards Organization (ISO) certifications, to the validity of shipping or purchase orders – the work of verifying all these characteristics "end to end" ("**E2E**") requires reams of paperwork, endless e-mails and phone calls, and costly site visits and audits. These cumbersome activities reduce productivity and efficiency throughout the economy, costs which are ultimately passed down to consumers.  

The immense volumes of data generated by global supply chains – if properly mined in a verifiable way – has other effects as well, though.  The resulting analysis helps to establish the trustworthiness of an entire value chain process and its resulting products. However, assembling and cleaning the requisite data set for such an analytical process requires numerous manual interventions and the involvement of many parties across multiple platforms. Furthermore, these kinds of audits are usually done by neutral consortia or by outside firms whose incentives do not touch the competition in the relevant markets, either of which centralize data access across a market. Competition for control of such consortia, or distrust of such profit-driven centralized firms, can slow down integration of such audits, which adds yet more costs. In few cases is this kind of deep business intelligence analysis practicable. 

We believe there is a simpler, less costly and more efficient way to establish trust in value chains, using block-chain and decentralized identity and reputation to establish credential-based trust among participants that have never met before. Identity and reputation are hand in glove. A reputation is meaningless without an underlying identity and an identity is valueless without a credible reputation. Because identity systems typically include credentials (which are a form of reputation) the industry usually refers to credentialed identity systems as simply identity systems, not identity and reputation systems. When the reputations become behavior based not merely credential based then the associated system is typically referred to as a reputation system not an identity system (but it always dependent on an underlying identity system). We view identity and reputation systems as existing on a spectrum of trust conveyance. Organizing and conveying the trust or credibility of data enables **E2E** verifiable audit trails along a given value chain even if it crosses many organizational boundaries, as long as all parties can be incentivized to minimally uphold data and control interoperability. 

Decentralized identifiers and verifiable credentials of the sort standardized by the W3C consortium, in combination with consequently interoperable agents, interaction protocols and credential-storing wallets, define a system wide trust mechanism along these lines.  We call this as a "meta-platform," because it enables participants to engage in trusted interactions in a wider ecosystem and maximizes intra-network value transfers. This approach can slash the “trust tax,” starting with participants agreeing to implement and follow the existing decentralised identity standards and their future developments. This decentralised approach does not build another aggregator platfom or another proprietary blockchain solution but rather a participant-controlled decentralized meta-platform. Opinions vary as to what this participant control could or likely would look like, but some proponents of decentralization argue that bottom-up governance is easier to institute in these kinds of meta-networks.

Because the primary value of a platform is to reduce transactions costs for all parties, a decentralized identity and reputation system has the potential to significantly reduce average, net, and/or aggregrate trust transaction costs in many different marketplaces and other industrial contexts. This may make whole families of transactions viable that were not viable before, or create new kinds of commerce (and perhaps even self-regulating ones). This increases the value of the associated platforms per particpant and lowers the critical platform size (see below). This further accelerates network-of-network effects.

## Example Trust Transaction Cost Reductions from Cooperation

### On-boarding costs

The original use of Metcalfe’s law was to show that even large upfront network connection costs would eventually be overcome by the exponential increase in value due to network size. The break-even point where the value of the network due to network effects to a participant is equal to the cost of joining the network is called the critical network size. Typically the major upfront cost of connecting to a platform is not the internet connection itself but the on-boarding cost of creating an account with login credentials and provisioning electronic payment.
One of the problems with decentralized blockchain technology is that in general it has increased the on-boarding costs of participants because of the difficulty in managing keys, increased regulatory friction, and more complexity. The plethora of competing (non-cooperative) blockchain platforms only heightens confusion. The result is that critical platform size may be significantly increased and the outcome that many blockchain platforms may never reach their critical size (break-even point).
A decentralized identity meta-platform allows those on-boarding costs to be amortized across every platform a participant chooses to join. This potentially lowers the critical platform size (break-even point) for the participant on each of the sub-platforms. This should accelerate network of network effects.


  
### IoT Combinatorics 

Today, the Internet is probably best described as a network comprised of all interconnected objects, traditionally referring to human users and computers. When you add in the so-called Internet of Things (IoT), the number of addressable elements is reaching the tens of billions already, with many analyses predicting a tenfold increase within a decade. 

The resulting combinatorics of possible connections between any given subgroup is an impossibly large number. Yet in today’s user journeys or business environments, agents (whether human, machine, or software) increasingly need to access, control or transact with a diverse group of these interconnected objects to achieve their goals in both the digital and physical worlds. This requires a straightforward and ubiquitous method to address, verify and connect these elements together.

> There are about 30 billion devices connected to the internet already. These devices are managed by thousands and thousands of different platforms. For the majority of the devices, it is quite unpredictable in which context they will be used: changes of ownership, geography, use case, machine-to-machine interactions, and other factors are inherently unpredictable. There are (N×(N-1))/2 possible peer-to-peer (P2P) connections among the devices possible, i.e. O(n²). This results in ~10^21 possible connections. There are O(n³) possible connections for connecting three systems and so forth. 

At some point, this staggering network-of-networks complexity will be equally pertinent in all business verticals, but today it most keenly felt in businesses dependent on supply chain management because of the large number of actors and multi-vendor components likely to be involved there. The main impediment is that it is cumbersome for each agent to have innate knowledge of the wide assortment of different addressing nomenclatures and protocols. At some point, it could go from impracticable to categorically impossible.

Human or object identities are stored in multiple centralised or federated systems such as a government, ERP, IoT or manufacturing systems. From the standpoint of cryptography-based systems of trust and/or verification, each of these centralised authorities serves as its own root of trust, tightly controlling all identities' access to one another's credentials and trust information. An object trailing along a supply chain is interacting with multiple systems and platforms. Consequently, a new actor in any give value chain has no method to independently validate credentials of a human or attributes of an object, except through the locally-governing central authority.  Even then, the audit trail they can access rarely extends back much further than the jurisdiction of that authority unless data has been forwarded along in parallel to the human or object's trajectory. 

Therefore, a trust verification system and associated interoperable meta-platform protocol, built on some kind of universal addressing system must be utilised. To be a truly global solution, easy-to-use and still safe from hacking and sovereign interference, such a meta-platform scheme must be independent from any vendor-defined naming API or otherwise centralized namespace, yet they usually need to be one-to-one mappable onto such APIs and namespaces. 

A participant controlled meta-platform based on decentralised idenitity solves the problem of addressability and trust verification across participants involved in a given value chain transaction. The potential of enabling these devices to interact is across a network-of-networks is inconceivably broad in scope.  It may well prove to be many orders of magnitude broader than Facebook as an aggregator for human interactions and an enabler of new connections and networks.
  

### Secure Logistics Systems

Multiple global logistics consortia are trying to establish so-called secure logistics systems for verifiable shipment tracking, process automation and verifiable business transactions across multiple entities.

Despite the fact that global logistics companies are attempting to leverage  decentralized technology, they are still constrained by their confined partner-system/ecosystem boundaries that prevent full decentralisation in their implementations. 

Let's assume the following scenario for verifiable logistics transactions which is based on a real world example:
- UAE logistics is using a decentralised Hyperledger implementation
- EU logistics is using a consortium-governed Ethereum Quorom system  
- Nordic logistics is using Maersk/IBM's TradeLens 

In this scenario, the three logistics companies have challenges to establish transactions across entities on the three different platforms. A typical approach is either A.) to convince the other partners to join one's own platform or, B.) to implement complex federation gateways between platforms.  This latter, it's worth noting, adds another player (the gateway) to the list of parties that need to be trusted, and potentially more transaction costs.

An identity-based meta-platform has the potential to solve this problem as it can establish trust among the participant entities, verifiability along the supply chain and trusted business transactions:
- Credential-based trust for on-boarding a previously-unknown actor
- Verifiable consent and business transactions
- Data provenance for trace-and-track along a logistics supply chain

## On Competition in Meta-platform Ecosystems

A participant-owned meta-platform has mechanisms or "antibodies" that deter a single entity from controlling it, creating a lock-in, or monetizing transaction data. The value transfer within the interoperable meta-platform ecosystem is controlled by the  participants. There is no administrator or aggregator that controls value and monetizes transaction margins. 

As a consequence, there is no real foothold at the core of the meta-platform for a single party to monetize or establish monopolistic control.  Instead, these kind of organic, cooperation-incentivized conditions are favorable to:
- Authentic sharing economy
- Interoperability, whereby previously unknown parties can transact in a trusted way
- Economically viable nano-transactions (lower overheads and transaction costs)
- Secure, business transactions, verifiable to a relatively high degree to outside parties without special access or permissions

One illustrative example can be seen in this projection about the mobility ecosystems of the near future:
![](https://i.imgur.com/fQpyvCz.png)

It’s important to note how different this model is from current models for example the ride-sharing platforms of Uber and Lyft. Autonomous vehicles eliminate the cost of human drivers, while decentralized meta-platforms eliminate the middleman that matches customers with rides, charges a transaction fee and sets terms and conditions.

Corporations will establish successful business models at the edge of this kind of meta-platform not by competing on margins or efficiency or proprietary IP, but by instead competing on
- User Experience
- Algorithms and Analytics
- Implementation and Services
- Hardware and Infrastructure

![](https://i.imgur.com/3Z15EQk.png)

Mobility on a decentralized meta-platform may also become one of the most visible examples of a zero-marginal-cost economy in which owners of everything from homes to cars rent them out when they are not in use, driving the marginal cost of most overnight stays or trips closer and closer to zero over time. 

In such a world, with cooperative economic drivers, trust, reputation and sustainablity become valuable and monetizable as a less zero-sum form of capital. 

At a macro level, the cooperative approach using portable and trans-contextual trust as the primary vehicle for trans-contextual value transfer also makes the associated economic systems more resilient in the event of shocks to sub-segments. Multiple independent but cooperating networks contribute network-effect value to each other. This contributed value bolsters the network and smooths out the effect of a shock to a given sub-network. This is a decentralized version of so-called "ergodic" economics [[22]], in that it leverages participant-controlled cooperative network-of-network effects to reallocate or share value.  

## Identity Meta-platform for the Circular Economy - Verifiable Identity for Circular Things

The ultimate ecosystem is developing as humanity begins to transition to a more circular economy. In a circular economy, identity for things along their entire life-cycle and among all potential actors involved is of utmost importance.

A circular economy is an economic system aimed at eliminating waste and the continual use of resources. Circular systems employ recycling, reuse remanufacturing and refurbishment to create a closed system, minimizing the use of resource input and the creation of waste. This regenerative approach is in contrast to the traditional linear economy, which has a 'take, make, dispose' model of production.  As extraction and disposal costs both climb, we will need more verbs than just "make".

Lowering trust transaction costs is a critical enabler for extending a sharing economy to lower-value transactions, which in turn leads to more reuse and less waste. These economic drivers to more reuse, less waste and spare unused capacity are the drivers/enablers for moving towards more circularity throughout the economy.

To enable truly restorative and regenerative economy by design, circular systems need a digital representation, a ***"digital twin"*** of any given entity. The term comes originally from iterative design processes in military and aerospace engineering, where prototypes, data models, and other kinds of information have to be painstakingly versioned and tracked to allow more iteration, more testing, and more data modelling within a finite budget, particularly for precise and critical components.  It has come to mean various ways of linking, bundling, or making persistent diverse forms of big and small data and metadata, particularly in a decentralized context where that data might be generated and stored across many networks and contexts with little persistant access to one another.  To enable circularity, this kind of persistent digital twin must be accessible by any (permissioned) actor along a supply chain to provide verifiable data provenance.  This provenance needs to include legible and complete information about materials and lifecycle that enable safe, exhaustive, and efficient recycling or refurbishing. To be a truly "circular" artefact, its would-be recyclers and refurbishers need access to a "verifiable story for every thing". 

Of course, this takes place at an atomic level, and scoping the process of getting from individual things being circular to all things being circular requires another combinatoric tour of infinitesimal potential interactions.  But along the way from first circular things to entire circular economy, that unthinkably large transition could also be sped along by the same infrastructure described above: a nurturing of cooperative networks effect, and a trust framework in form of an identity meta-platform for circular things.

The cryptographically secure digital twins provided by the meta-platform enable a systemic, algorithmic digital fabric to orchestrate the circular system. All kinds of knock-on effects and organic marketplaces could arise from such a regime of materials tracking:
- Everything with a Decentralized Identifier is connected to a persistent data store hosting verifiable life cycle data.
- Any random actor can independently verify the life cycle assertions of a thing, literally “its complete story”.
- Back-to-birth traceability of manufactured things is needed to minimize avoidable pollution and to design out waste from manufacturing processes while keeping materials in use as long as possible
- Monetization and incentivization of existing problems could begin in the short term, addressing machine life cycle, supply chain provenance or 3rd party risk management through an automation of audit processes on demand.
- Orchestration of circular systems with algorithms running on top of the digital twins for monitoring, optimization and transitioning to a restorative and regenerative economy.

![](https://i.imgur.com/bssYXRT.png)


We believe that a connection between the meta-platform's cooperative network effects and a circular economy delivers a lot of value for society as a whole, and perhaps enough immediate value for governments and huge corporations that building it could appeal to them.



## Conclusion

In this paper we layed out that there is a economic reason for corporations to join the cooperative meta-platform in question and perhaps many other such meta-platforms yet to come.  At first glance, it might seem to some an impractical upfront infrastructural investment that would run counter to the incentives of existing power structures. Others might see such decentralization as unrealistic in a time when the biggest companies in the world are low-overhead tech conglomerates dominating platforms that didn't exist twenty years ago. But from another perspective, this recent excess of monopolistic tendencies and winner-take-all platform plays might be a growing pain, or a pendulum swing, after which we return to a drastically different mood and set of economic norms.

Indeed, many would argue the pendulum has been swinging throughout the history of technology.  Many leveling technologies, such as communication networks, first started as decentralized but then become more centralized over time with the associated value capture eventually becoming concentrated into a few very large business entities with higher rates of value extraction. This historic cyclic behavior is well documented in The  Square and the Tower and the Master Switch [[9]][[10]]. One can argue that the internet which started as a great leveler due to decentralized networking has now resulted in most of its value being concentrated in a handful of companies, namely, Google, Apple, Facebook, Amazon, and Microsoft each with valuations near one trillion dollars. Once centralization occurs, innovation and value creation decrease and value extraction increases to the detriment of the average user, according to either price or diversity metrics.

One way to combat such centralization is with regulation. The breakup of AT&T and the injunction against Microsoft's predatory bundling are two largely successful examples of a regulatory approach to restoring more decentralization.  Both debatably resulted in demonstrably more innovation, lower costs and overall greater benefits to telecommunication users and operating system ecosystems. Regulatory approaches, however, often come with deleterious or unpopular side-effects. Many prefer more market-driven decentralization when multiple approaches are available. While the technology and its comcomitant economics are still largely immature, appropriate applications of blockchain technology may enable such market drivers. The authors agree that blockchain-anchored decentralized identity infrastructure is one such application.

## Glossary

A. Platform - A platform is a business based on enabling value-creating interactions between external producers and consumers.  The platform provides an open, participative infrastructure for these interactions and sets governance conditions for them. 

The platform’s overarching purpose: to consummate matches among users and facilitate the exchange of goods, services,  or social currency, thereby enabling , value creation for all participants.

Platforms create value by using resources they don’t own or control, as such they can grow much faster than traditional organizations.

(Source: Platform Revolution)

B. Intra-context - transfer of value within the same set of applied products, services and network of participants.

C. Inter-context - transfer of value across different applied products, services and networks of participants. (transcontext)

D. E2E - entity to entity


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

[17]. S. Conway, A. H., M. Ma et al., “A DID for Everything,” RWOT Fall 2018, 2018/09/26 https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/A_DID_for_everything.pdf

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