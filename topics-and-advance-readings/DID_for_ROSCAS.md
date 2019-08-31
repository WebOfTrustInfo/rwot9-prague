## Using DID for use of Rotating Savings and Credit in Developing/ Emerging Economies

Submitted by Vineet Singh (Independent Identity Enthusiast)
Submitted to Rebooting Web Of Trust 9
August 16, 2019

## Abstract

Rotating Savings and Credits Association are a type of Micro finance option. They have played an important role for lower income level group in the developing/emerging economies. While the legislation to regulate them and a formal study of the economic value they add is fairly recent, these have been around for more than 1000 years. Some researchers have also called ROSCAS as poor man’s banker. They provide a win-win situation for both borrowers and people who want to save without intervention of a central authorities like banks. However, the quick good return has often been used as bait for unsuspecting and gullible investors, resulting in very high value financial scandals that has often have political repercussions. In this paper we present the kind of scandals that take place in these schemes and how scaling them up digitally is extremely risky. How Decentralized Identifiers and Verifiable claims along with biometrics on mobile phone can be used to create a trust framework.

## Introduction

ROSCAS (Rotating Savings and Credit Association) are popular in different countries by different name: Chit Fund/ Committee in India, Hui in China, Tanda in Latin America, Susu in West Africa and Carribea. At its core, lies a simple model of community based saving and borrowing based on simple rules and trust within the group which is typically managed by a person with good social standing. ROSCAS model work in a very simplistic way, N number of people will meet N times and pool in a fixed money every time creating a pot. In this case, let’s say they pool in 100 units of respective currency every time, so they will create a pot of 100N every time. Next, they conduct auction on the discount for the collected amount, the person who needs money most will opt for the highest discount and get the discounted money from the pot. In our example, if he/she opts for a discount of d%, the money that individual gets is (100-d-f)*N. The organizer may charge a nominal fee, f% for carrying out the operations. So, the remaining people will each get (d+f)*N/(N-1) amount as dividends. The person who wins the auction once is not allowed to auction again but has to participate in all the rounds.

The elegance of ROSCAS lie in the fact that the one in need of money gets access to the credit and the one who wants to save money for now gets extra interest. A very important feature in ROSCAS is also the voluntary nature of taking part in the system without having any centralized authority in between. The economic benefits can be understood as someone paying (d+f)*N amount of interest on 100*N money in this period (assuming the later auctions are zero discount). The easy access to credit is as important as the timely deliverable of credit. There are certain additional rules like capping the maximum discount and in case of draw, splitting the pot. ROSCAS has supported credit requirement in the rural sector and has also benefited women who generally take care of the household finances. 

## Possible Fraud/ Attacks
It is important to understand that the group can be small as well as large. In a smaller group, there is an inherent social trust and the organizer is typically a person with social stature who is respected and acts as trust anchor in case of disputes. If there is an organization running the ROSCAS, they act as trust anchor and manage the group. However, as the group has to meet exactly the same number of  times as the number of people, the group size becomes limitation. In such a case, multiple groups of individuals is formed. With these multiple groups, the management of funds become increasingly difficult with fund value increasing.

There are various kinds of fraud that can take place in this case and therefore, in some Countries like India there is legislation to regulate which also differ slightly from State to State and one of the requirements is to register the Chit fund with Registrar of Chits.  However, the legislation has not made chit fund scandals zero.

One of the most common attacks is if the person having secured the pot doesn’t turn up next time. This is typically mitigated by having Due diligence and KYC for every participant that can then be taken to appropriate authorities in case of such occurrence and also acts as a deterrent. The challenges faced are lack of proper identity or forged identity by rogue participant with improper unstructured address to track the individual. Further, the defaulter has to be sent a mail and then taken to court and legal proceedings take their own sweet time. 

The second attack could be from the organizer where the auctions can be rigged by discounting too much by using proxies or agents of the organizer so that the participant who is actually needy and deserves money is not able to get the required amount which leads to more discount in subsequent turns. In this setting, the organizer typically charges a fee on the amount of dividends (unused money) paid and increasing the dividends can work to organizer’s benefit. The organizer can also balance out the agent that are coming as investor who will bid in later turn and take the entire pot. To curtail such practise, the government has imposed a limit to the maximum discount.

A third and the most rampant type of scam is similar to multi level marketing, having a hierarchy of agents to pool in people. In many cases, chit fund is simply a name to attract people which in reality is a ponzi scheme.

There could be even more sophisticated attacks by organizers by deliberately not collecting proper documents and injecting malicious actors that would default after taking the pot. The money trail is lost as the mailcous known attacker takes the pot not to return back. If done in multiple groups, the size of pot could be significant.

## SCALE/ DIGITIZATION - use of DID
In the current way of managing things, the scale of ROSCAS is limited as the attacks become common and increasingly more sophisticated. Digitization can help ROSCAS achieve larger scale. DID in this particular case can answer the question of maintaining trust without having to be physically present. The DID needs to be mapped against an account that is accessible using biometric/ liveness detection and some authentication mechanism. 

The requirements for a digital ROSCAS could be:
Anonymity: Not being able to know who the person is makes it highly unlikely that the auction or any process can be rigged through collusion
One - One relationship: Being able to prove that a person owns the DID by giving a certificate of binding with some biometric (owned on the device by individual)  without revealing the biometric. In an ideal case scenario, Alice can have as many DIDs as desired but every time she logs in a ROSCA account a certificate proving her relationship with an unknown biometric is shown. All the DIDs will have same certificate, the certificates themselves not being on blockchain and owned by Alice to be shown only when asked for.
Self Sovereign: the identifier should be owned by individuals and can’t be created by any other entity. 

Decentralized Identifiers provide all the requirement to be an effective identity layer for successfully running the ROSCAS digitally and help achieve even a global scale. The best of the scenario could be if a farmer from India is able to participate in a ROSCAS run in West Africa, thereby helping borrowers and in turn making earning. 




