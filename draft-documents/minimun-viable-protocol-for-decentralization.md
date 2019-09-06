# Minimum viable protocol for decentralization

### Authors

Snorre Lothar von Gohren Edwin, Adrian Gropper, Victor Martinez

# Abstract

Alice wants to become self-sovereign. Alice’s needs vary, but to get into decentralization she needs an agent. This agent is an operator that she can prove the control over her self sovereignty. This agent can be smartphones, cloud devices or something else that can prove the right to the identity.

Alice’s agent then controls access to one or more components that are typically separate from her agent.

We will be defining a couple contexts for agents and needed components to make Alice self-sovereign, creating a minimum viable protocol for decentralization. Making it clear to the community how one can enable self-sovereignty where there is a differentiation of agent capabilities.

# Introduction

Self-Sovereign Identity is, at best, an abstract concept and, at worst, hopelessly naive. Our work on technology related to self-sovereign identifiers goes beyond the VC standard (yay!) and the DID standard working group (yay!) to protocols for interoperability. Our community shares a common goal to accelerate adoption while accommodating the core principles of our community and respecting the diversity and generativity we value.

This contribution presumes decentralization as a goal even as the rubrics for decentralization are being worked on in other groups at RWoT and around the world. It approaches from the perspective of a Minimum Viable Protocol (an abuse of the MVP acronym) that will help inform our terminology, our protocol development, and our communication efforts.

The case of an educational credential in a low-resourced country was used as our top-level inspiration for design of the MVP. The student, Alice, is the subject of the credential. She has only an inexpensive, SMS-capable phone as her personal technology and depends on connected services. Alice’s identity, in this simple case, is indistinguishable from her mobile number. She is able to receive a VC from the school and present that VC to an employer.


# Survey summary

As a group who is not expert on agent creation we had to pull on the thoughts of experts in the community. We have discussed these thoughts and views with Daniel Hardman, Oliver Terbu, Manu and the secure data storage group and Orie Steel from Transmute.

Throughout the survey, we asked questions such as:
What’s the difference between a wallet and an agent?
What are your thoughts on cloud agents?
What is your thought on the simplest way of “controlling” a DID?
How do you see the relationship between an agent and storage resource?

#### What’s the difference between a wallet and an agent?
There were some confusion about how these terms are used and we want to clarify that based on our understanding of the conversations we had. See terminology

#### What are the thoughts you have on cloud agents?
This is overall an accepted term and a feasible approach to delegating some control out of a particular agent, either because that agent does not have capabilities needed to support decentralization, or one wants to abstract some aspects of its current agent. See further explanation of cloud agents in terminology.

#### How do you see the relationship between an agent and storage resource?
This is much related to the answers of wallet and agents, since some people saw the wallet as a storage resource, and others demanded a secure storage resource. We want to try to clarify what most of the community believes this relationship to be. See further explanation in terminology.

#### What is your thought on the simplest way of “controlling” a DID? 
This is a question that is a bit determined to subjectivity. Since it comes down to if the perception is from a developer or user. A user would say that the cloud agent would be the easiest. A developer would probably say that the mobile agent would be the easiest. Since you relieve much of the responsibility to the user. But in the end, control comes down to key management, which is not easy, and is not in the scope of this paper. 



# Terminology

There are a lot of terminology going around in the community, we hear over and over again that the new people find this confusing. The purpose of this section is to provide a non-opinionated glossary to help SSI community to understand the meaning of the terms that the authors intended to convey in this paper. 




#### Agent 
Is one of the terms used in SSI community with different meanings. In some cases, the term Agent and Wallet is used as the same thing, in other cases as separate concepts. In this paper, we define an agent as a software program operating on behalf of the the Identity subject with KMS capabilities in order to perform cryptographic operations , storage capabilities in order to store documents that, in case of data leak, the information disclosed could be considered a privacy breach. Finally, we consider that an agent needs some communication capabilities in order to have mutual trust interaction between Agents.

#### Storage
Storage is what (Ref to secure cloud storage paper) is working on. We want to contribute to anchoring the common understanding of what this is. We suggest that storage should be viewed as a place that Alice, as a holder, can store everything from medical records, tax document and also verifiable credentials, securely! She can control this storage through delegation or locally on her agent device.

#### Wallet
We have deliberately pulled out the term wallet of this paper, because this word is something that has created more confusion than value. Our understanding is wallet usually is used instead of a KMS, and can have an agent wrapped around itself. The term wallet has been used as simpler marketing because it is a terminology that is easy to relate too. See KMS for a more thorough explanation.

#### KMS(Key management system)
This is a familiar term in the cryptography space. Therefore we suggest using the term KMS avoiding to use less invented terminology that only makes sense inside this community. And for easier adoption of people outside of this community and the blockchain community. KMS is a wrapped terminology that can include, a secure enclave on phone, using cloud accessed HSM or local KSM on any type of device.

#### Delegation
Delegation is an important keyword. It comes from the current auth and delegation models that are out there. We should not forget this, because this is what allows us to have a pattern of agents. 

# MVP
In discussing the minimum viable protocol, we found consensus around the principles of decentralization, delegation, interoperability, and substitutability. We also found that privacy and security were hardly absolutes and have to be tuned for the realities of a particular context.

We find it useful to judge the MVP relative to two different contexts based on resource availability.

### Resource minimization context
In the introduction, we mentioned a use case where the holder was not in possession of any devices that is able to act as a suitable agent on its own. This being a SMS capable phone which does not have any storage or any possibilities for KMS. It seems difficult to enable someone with self-sovereign identity when they are only equipped with this type of device. After discussions and research, and based on our MVP diagram, we found that there had to be one type of agent that the holder could delegate to. This agent would live outside of the holder's device. The proposed agent would be a Cloud-Agent. 

In this context we see that privacy might be decreased, the security of delegation and key management has to be discussed. But this is out of scope for conveying the MVP of a resource minimization context.

We challenge the implementors to think, what is secure enough delegation, what is good enough KMS, to enable more holders of self-sovereign identity in the average scenario.

![](https://i.imgur.com/SO7BYKe.png)

### Decentralization maximization context
Data about seriously ill or politically exposed individuals is very valuable. In this context, the individuals can justify expensive technology such as smartphones and trusted execution environments that, ideally, would be completely independent and self-sovereign to each of the interacting peers. That said, the MVP must not restrict these peers from interop with services aimed at resource minimization and it must not prevent strong privacy for use-cases where that is foremost.

For security reasons, we stress the importance of delegation across all aspects of the MVP. Agents may be delegates of another agent that serves the same identity or they may be that agent of a separate entity, be it individual or institutional. Institutional agents, such as directories of personal data about many different subjects, are modeled as delegates of an agent representing an individual.

# Conclusion

![](https://i.imgur.com/83jlkQV.png)

To support the various use-cases, including interoperability and substitutability, the scope of the MVP must include agent-to-agent and agent-to-storage protocols under a delegation model. User authentication is out of scope.

The discussions spurring up after this paper, initialized by the authors and others in the community will be documented here. The authors commit to pulling forward what all the arrows and boxes basically can mean, where are protocols neded. What software do the community have running and is reusable. And what software to the community need built.
