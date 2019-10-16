---
tags: RWOT9, Meta-Platforms, Cooperative Economics
linkedin: www.linkedin.com/in/samuel-m-smith
email: sam@samuelsmith.org
---
# Decentralized Identity as a Meta-platform: How Cooperation Beats Aggregation

Authors:
[Michael Shea](mailto:michael.shea@thedinglegroup.com), 
[Samuel M. Smith Ph.D.](mailto:sam@samuelsmith.org), 
and [Carsten Stöcker Ph.D.](mailto:carsten.stoecker@spherity.com)


Collaborators:
[Matt G. Condon](mailto:mattgcondon@gmail.com) and 
[Juan Caballero Ph.D.](mailto:caballerojuan@pm.me)

version 0.7, 2019/10/16

github:  https://github.com/SmithSamuelM/rwot9-prague.git

## Abstract

A meta-platform is a platform that enables and fosters participant-controlled value transfer across and among other platforms and participants [[1]]. Because platforms are a type of network, a meta-platform enables a network of network effects. This cooperation among platforms may be advantageous in comparison to centralized power (non-cooperation), suggested by a new network scaling law for meta-platforms [[1]][[2]]. An *open, interoperable, portable, decentralized identity framework is a prime candidate for a meta-platform leveraging this aggregate network effect*.

Significant momentum has been developing behind a universal decentralized identity system based on open standards which include the W3C supported decentralized identifier (DID) and verifiable credential standards [[14]][[21]]. Associated industry groups include the Decentralized Identity Foundation (DIF), Sovrin Foundation, and HyperLedger-Indy/Aries/Ursa [[15]][[16]][[18]][[19]][[20]].

The purpose of this paper is to foster awareness of the economic benefits of cooperation and the crucial role decentralized identity may play in unleashing new sources of value creation and transfer among cooperating platforms.


## Introduction

*(introducing the concept of meta-platforms, key features, key value propositions, enabling technology. Then outline the paper - exploration of triangulation, transfer and trust, examples of existing networks of networks where meta-platforms can demonstrate their value, counter forces (Malthusian Trap), summary)* to be removed later

*Edited Content* (*Further-edited by Juan 10/15/19 only for style and clarity, not content)

We are all familiar with many of the existing software platforms that are used today: in a consumer context, we speak of Google for searching, Amazon for purchasing goods, and Facebook or Twitter for social media exchanges.  In an enterprise/business context, the platforms are different: Salesforce for CRM, TradeLens for containerized shipping and logistics, and Amazon AWS for cloud-based IT services.  What drives the growth of a platform is the reduction the platform offers in transactions costs that accrue value to the platform via Metcalfe's law network effects. These transaction costs include triangulation, transfer, and trust [[5]]. For example these include the costs of matching buyers to sellers and facilitating interactions and payment.   Buyers and sellers on the platform get a significant reduction in transaction costs, The platform owners get a fee on each transaction, as well as market-wide access to large amounts of transaction data.

To date,  in order to maximize network effect driven value, the "platform game" has been defined by a "winner takes all" rule book. The solitary focus of the platforms has been to grow the network as large as possible as fast as possible. In a "winner takes all" world, this is the only road to survival. And the winner's are few and powerful (centralized) and therefore able to exploit their participants. In a world now dominated by a few powerful centralized platforms entire industries have grown suspicious of this value proposition.  

We are no longer in a centralized world.  

With a proper meta-platform counterbalancing these centralizing tendencies, a "winner takes all" approach is no longer the only, or even the most sustainable, model for establishing platforms.  This paper examines one blockchain-enabled technology and market driver for decentralization: an identity meta-platform. It describes how identity can provide the connective pathways (in software terms, the "protocol") that unlocks the potent force of data-flow decentralization and provides the foundation for the creation of a platform-of-platforms (what we call the "meta-platform") that provides its participants with a new level of control and portability.  By making their participation portable to other platforms structured around the same protocol, these platforms empower the individual actor vis-a-vis the platform.

We will first discuss how the network scaling law for meta-platforms differs from the network scaling traditionally seen on platforms today, and we will examine why the cooperating members of a decentralized identity meta-platform may "eat" (out-compete) centralized identity platforms [[1]].

We will outline how participant control means that participants may form customized or bespoke virtual platforms of their own choosing. These virtual platforms aggregate and/or amplify their value across multiple platforms. Participant control better balances the interests of participants and platform operators. It provides a check on exploitation while increasing the value of the platform to both participants and operators due to increased attractiveness [[7]][[13]].

![](https://i.imgur.com/dzgLuu1.png)



We will then review examples of industry ecosystems where this kind of identity meta-platform will address existing inter-operability problems and provide real value, today.

We will close with summary of what has been presented, and the closing argument that by establishing identity functions on a decentralized meta-platform protocol, many other technological and economic processes might develop powerful resistance against technological tendencies which "centralize" data power.





## Cooperative Network of Networks Effect

A network scaling law describes how some property of the network changes as a function of the size of the network. In the case of platform networks the relevant property is network value and the size is the number of participants.  The most well known network scaling law is Metcalfe's Law [[11]] where on average the value of the network to single participant is proportional to the total number of participants. If we let *a* represent the average proportionality constant and *N* the number of participants then we have the following expression for the average value to a participant, *v*, that is,

*v* = *a*⋅*N*

Furthermore the total value of the network, *V*, is just the sum of the values from each of the *N* participants. This gives the following expression:

*V = v⋅N = a⋅N⋅N = a⋅N²*

Any property or value of the network that scales with the square of the size of the network will eventually dominate. This is why network effects can be so valuable. See this article for a discussion of the quantitative validation of this effect [[1]]. 

### Metcalfe law scaling of cooperative networks

The exponential increase in value with Metcalfe's law scaling poses the question: *What happens if two competing networks cooperate so that the combined network has a larger N than either network on its own*? 

Suppose that two networks of size *N₁* and *N₂* respectively were to combine. by making their services interoperable (cooperate). Individually the *N₁* network's total value is,

*V₁ = a⋅N₁²*, 

and the *N₂* network's total value is

*V₂ = a⋅N₂²*.

After combining, the average value to a participant of either network *N₁* or *N₂* is due to the combined size of the new network, *N₁+N₂*. This becomes,

*v₁ = v₂ = a⋅( N₁+N₂)*.

The total value of network *N₁* is becomes,

*V₁ = a⋅N₁⋅( N₁+N₂) = a⋅N₁²+a⋅N₁⋅N₂*.

Likewise the total value of network *N₂* becomes,

*V₂ = a⋅N₂⋅( N₁+N₂) = a⋅N₂²+a⋅N₁⋅N₂*.

Merely by cooperating, each network has increased its total value by 

*a⋅N₁⋅N₂*.

This is a very valuable benefit of cooperation.  The total value of the combined network is just the sum,

*V = V₁ + V₂ = a⋅N₁²+2⋅a⋅N₁⋅N₂+a⋅N₂² = a⋅(N₁+N₂)²*,

which is the same as one larger network of size *(N₁+N₂)*. The following diagram shows graphically the increased value due to cooperation.


![](https://i.imgur.com/BWV1KSe.png)

The same analysis can be extended to multiple cooperating networks [[1]]. In the above example the cooperative effect came from making the networks interoperable. This may pose a problem if both network's products are competitive. Despite the cooperative increase in total value there may still be aversion to cooperation due to the competitive nature of the products. With interoperability,  participant's may freely transfer value between the networks. We call this intra-contextual value transfer. But this poses the question: What about cooperating networks where participant's are able to transfer value but the networks have different non-interoperable products? Is that even possible? We call this type of value transfer inter-contextual value transfer (trans-contextual). If this were possible it would remove a perceived barrier to cooperation. In the next section we will talk about value transfer than may occur inter-context.


## Trust Transactions Cost in current Systems

One common approach to understanding business processes is via the model of transaction costs. Business value comes from reducing net transaction costs. Transaction costs may be grouped into three classes, these are triangulation, transfer, and trust [[4]][[5]]. Of these trust may be the most important, especially for a meta-platform. Without trust, platforms as well as physical and digital value chains can not exist.

However, that trust has been historically difficult, and costly, to establish. Trusted suppliers are thoughtfully selected and managed, as well as monitored and certified for quality, reliability and consistency. Regulators demand certifications and audits to ensure that best practices are followed, and companies such as TÜV, Underwriters Laboratories or Intertek conduct inspections and provide quality certifications. At the end of the value chain customers purchase products because they trust the quality of the brand, which is the key differentiator for many companies.

The immense volumes of data generated by global supply chains – if properly mined in a verifiable way – can help to establish the trustworthiness of a given value chain processes and its resulting products. However, the process requires numerous manual interventions and the involvement of many parties and its facilitation across multipe platforms. 

Providing such assurances in today’s world imposes a hidden (and growing) “trust tax” on either local or worldwide supply chain participants. From the use of “conflict-free” raw materials, to Six Sigma manufacturing practices, to Independent Standards Organization (ISO) certifications, to the validity of shipping or purchase orders – the work of verifying all these characteristics requires reams of paperwork, endless e-mails and phone calls, and costly site visits and audits. These cumbersome activities reduce productivity and efficiency throughout the economy, making it more expensive, complex and time-consuming for customers and suppliers to find and do business with one another.

We believe there is a simpler, less costly and more efficient way to establish trust in value chains, using blockchain and decentralised identity to establish credential based trust among participants that have never met before and **E2E** verifiable audit trails along a give value chains . 

With W3C decentrlised identitifiers and verifiable credentials in combination with agents, interaction protocols and wallets define a "meta-platform" enables participants to engage in trusted interactions in a wider ecosystem. This approach can slash the “trust tax,” starting with participants agreeing to implement and follow the existing decentralised identity standards and their future developments. This decentralised approach does not to build another aggregator platfom or blockchain solution but a participant controlled decentralized meta-platform. 

Because the primary value of a platform is to reduce transactions costs, a decentralized identity and reputation system has the potential to significantly reduce average trust transaction costs across different contexts. This may make whole families of transactions viable that were not viable before. This increases the value of the associated platforms per particpant and lowers the critical platform size. This further accelerates network of network effects.

## Example Trust Transaction Cost Reductions from Cooperation

### On-boarding costs

The original use of Metcalfe’s law was to show that even large upfront network connection costs would eventually be overcome by the exponential increase in value due to network size. The break-even point where the value of the network due to network effects to a participant is equal to the cost of joining the network is called the critical network size. Typically the major upfront cost of connecting to a platform is not the internet connection itself but the on-boarding cost of creating an account with login credentials and provisioning electronic payment.
One of the problems with decentralized blockchain technology is that in general it has increased the on-boarding costs of participants because of the difficulty in managing keys, increased regulatory friction, and more complexity. The plethora of competing (non-cooperative) blockchain platforms only heightens confusion. The result is that critical platform size may be significantly increased with the result that many blockchain platforms may never reach their critical size (break-even point).
A decentralized identity meta-platform allows those on-boarding costs to be amortized across every platform a participant chooses to join. This potentially lowers the critical platform size (break-even point) for the participant on each of the sub-platforms. This should accelerate network of network effects.


  
### IoT Combinatorics 

Today, the Internet is probably best described as a network comprised of all interconnected objects, traditionally referring to human users and computers. When you add in the so-called Internet of Things (IoT), the number of addressable elements is in the tens of billions. 

The resulting combinatorics of possible connections between any given subgroup is an impossibly large number. Yet in today’s user journeys or business environments, agents (whether human, machine, or software) increasingly need to access, control or transact with a diverse group of these interconnected objects to achieve their goals in both the digital and physical worlds. This requires a straightforward and ubiquitous method to address, verify and connect these elements together.

> There are about 30 billion devices connected to the internet already. Today the 30 billion devices or managed by thousands and thousands of diffrent platforms. For the majority of the devices it is unpredictable in which context they will be used (owner, geography, use case, machine-2-machine interactions). There are (N×(N-1))/2 possible peer-to-peer (P2P) connections among the devices possible, i.e. O(n²). This results in ~10^21 possible connections. There are O(n³) possible connections for connecting three systems and so forth. 

At some point, this will be equally true in all business vertical areas but is especially paramount today for businesses dependent on supply chain management because of the large number of actors and multi-vendor components likely to be involved. The main impediment is that it is cumbersome for each agent to have innate knowledge of the wide assortment of different addressing nomenclatures. At some point it will become impossible.

Human or object identities are stored in multiple centralised or federated systems such as a government, ERP, IoT or manufacturing systems. From the standpoint of cryptographic trust verification, each of these centralised authorities serves as its own root of trust. An object trailing along a supply chain is interacting with multiple systems and platforms. Consequently, a new actor in any give value chain has no method to independently validate credentials of a human or attributes of an object (audit trail). 

Therefore, a universal addressing, trust verification system and associated interoperable meta-platform protocol must be utilised. To be a truly global solution, easy to use and still safe from hacking and sovereign interference, such a meta-platform scheme must include: addressing standards, reliable trust verification and independence from any vendor-defined naming API, yet still be one-to-one mappable onto it. 

> A participant controlled meta-platform based on decentralised idenitity is solving the problem of addressability and trust verification across participants involved a given value chain transaction. The potential of enabling these devices to interacte is massivley huge, many orders of magnitude bigger then Facebook as an aggregator for human interactions.
  

### Secure Logistics Systems

Multiple global logistics consortia are trying to establish so called secure logistics system for verifiable shipment tracking, process automation and verifiable business transactions across multiple entities.

Despite the fact that global logistics companies are attempting to leverage  decentralized technology they are still constrained by their confined partner system boundaries that prevent full decentralisation. 

Let's assume the following scenario for verifiable logistics transactions which is based on a real world example:
- UAE logistics is using their a decentralised Hyperledger implementation
- EU logistics is using a consortium Ethereum Querom system UAE logistic platform 
- Nordics logistics is using IBM's TradeLens 

In this scenrio the three logistics companies have challenges to establish transactions across entities on the three different platforms. A typical approach is either to convince the other partners to join my own platform or to implement complex federation gateways (which need to be trusted) among the platforms. 

A identity-based meta-platform has the potential to solve this problem as it can establish trust among the participant entities, verifiability along the supply chain and trusted business transactions:
- Credential based trust for on-boarding a previously unknow actor
- Verifiable consent and business transactions
- Data provenance for trace and track along a logistics supply chain



## On Competition in Meta-platform Ecosystems

A participant owned meta-platform neither allows a single entity to control it, to create a lock-in nor to monetize transaction data. The value transfer within the interoperable meta-platform ecosystem is controlled by the  participants. There is no administrator or aggregator that controls value and monetizes transactions margins. 

![](https://i.imgur.com/fQpyvCz.png)

As a consequence there is no monetization at the core of the meta-platform for a single party resulting in
- Authentic sharing economy
- Interoperability, previously unknown parties can transact in a trusted way
- Economically viable nano-transactions
- Secure, verifiable business transactions

It’s important to note how different this model is from current models for instance such as ride-sharing platforms such as Uber and Lyft. Autonomous vehicles eliminate the cost of human drivers, while decentralized meta-platforms eliminate the middleman that matches customers with rides, charges a transaction fee and sets terms and conditions.

Corporations will establish successful business models at the edge of the metplatform by competing on
- User Experience
- Algorithms and Analytics
- Implementation and Services
- Hardware and Infrastructure

![](https://i.imgur.com/3Z15EQk.png)

Mobility on a decentralized meta-platform may also become one of the most visible examples of a zero marginal cost economy in which owners of everything from homes to cars rent them out when not in use, driving the marginal cost of each overnight stay or trip close to zero. 

In such a world with cooperative economic drivers, trust, reputation and sustainablity become valuable and monetizable capital. 

At a macro level, the cooperative approach using trust as the primary vehicle for trans-contextual value transfer also makes the associated economic systems more resilient in the event of shocks to sub-segments. Multiple independent but cooperating networks contribute network effect value to each other. This contributed value bolsters the network and smooths out the effect of a shock to a given sub-network. This is a decentralized version of ergodic economics [[22]] that leverages participant controlled cooperative network-of-network effects to reallocate or share value.  

## Identity Meta-platform for the Circular Economy - Verifiable Identity for Circular Things


The ultimate ecosystem is developing when humanity transitions to a circular economy. In a circular economy identity for things along their entire life-cycle and among all potential actors involved is of utmost importance.

A circular economy is an economic system aimed at eliminating waste and the continual use of resources. Circular systems employ recycling, reuse remanufacturing and refurbishment to create a closed system, minimizing the use of resource input and the creation of waste. This regenerative approach is in contrast to the traditional linear economy, which has a 'take, make, dispose' model of production.

Lowering trust transaction costs is a critical enabler for extending a sharing economy to lower value transactions which leads to more reuse and less waste. These economic drivers to more reuse, less waste and spare unused capacity are the drivers/enablers for moving towards more circularity.

To enable truly restorative and regenerative economy by design circular systems need a digital representation, a digital twin of any given entity. This digital twin must be accessible by any (permissioned) actor along a supply chain to provide verifiable data provenance about the life-cycle of the respective circular object: "A verifiable story for every thing". 

Combinatorics of the unimaginable large number potential interactions and the required cooperative networks effect that are needed to transition towards a circular economy requires a trust framework in form of an identity meta-platform for circular things.

The cryptographically secure digital twins provided by the meta-platform enable a systemic, algorithmic digital fabric to orchestrate the circular system.
- Every things with a Decentralized Identifier is connected to a data store hosting verifiable life cycle data.
- Any random actor can independently verify the life cycle assertions of a things, literally “its entire story”.
- Back to birth traceability of things for avoiding pollution and designing out waste while keeping materials in use.
- Immediate monetization by starting with existing problems in machine life cycle, supply chain provenance or 3 rd party risk management through automating audit processes on demand.
- Orchestration of circular systems with algorithms running on top of the digital twins for monitoring, optimization and transitioning to a restorative and regenerative economy.

![](https://i.imgur.com/bssYXRT.png)


We believe that a connection between the meta-platform cooperative network effects and circular economy delivers a lot of value for .



## Conclusion

In this paper we layed out that there is a economic reason for corporates to join the cooperative meta-platform. ...

 (from intro section, needs to be integrated)
A concern comes from the fact that other leveling technologies, such as communication networks, first started as decentralized but then become more centralized over time with the associated value capture eventually becoming concentrated into a few very large business entities with higher rates of value extraction. This historic cyclic behavior is well documented in The  Square and the Tower and the Master Switch [[9]][[10]]. One can argue that the internet which started as a great leveler due to decentralized networking has now resulted in most of its value being concentrated in a handful of companies, namely, Google, Apple, Facebook, Amazon, and Microsoft each with valuations near one trillion dollars. Once centralization occurs innovation and value creation decrease and value extraction increases to the detriment of the average user .

One way to combat such centralization is with regulation. The breakup of AT&T is a largely successful example of a regulatory approach to restoring more decentralization that resulted in more innovation, lower costs and overall greater benefits to telecommunication users. Regulatory approaches, however, often come with very large deleterious side effects. What would be better instead is market driven decentralization. Appropriate applications of blockchain technology may enable such market drivers.

## Glossary

[1]. Platform - A platform is a business based on enabling value-creating interactions between external producers and consumers.  The platform provides an open, participative infrastructure for these interactions and sets governance conditions for them. 

The platform’s overarching purpose: to consummate matches among users and facilitate the exchange of goods, services,  or social currency, thereby enabling , value creation for all participants.

Platforms create value by using resources they don’t own or control, as such they can grow much faster than traditional organizations.

(Source: Platform Revolution)

[2]. Intra-context - transfer of value within the same set of applied products, services and network of participants.

[3]. Inter-context - transfer of value between different applied products, services and networks of participants.

[4]. E2E - entity to entityy


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