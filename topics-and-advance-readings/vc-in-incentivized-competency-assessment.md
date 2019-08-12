**Keywords**: competency-based assessment, self-sovereign identity, decentralized identifiers, verifiable credentials, digital certificates.

## Contributors

Stepan Gershuni, credentia.me

## Abstract

Verifiable Credential is qualification, achievement, quality, or piece of information about an entity's background. In this work we propose another possible use case of Verifiable Credentials in education space — competency-based assessment that does not rely on a centralized party. We leverage web of trust concept in order to create a network of competencies where Experts (Examiners) act as verifiers to assess user's competency on a given subject. We propose using decentralized staking and slashing mechanism similar to Augur's dispute model in order to create financial incentives for users to minimize fraud in the network. Finally, we propose a design for mechanism that produces verifiable credentials of skills and competencies which do not require centralized assessor or an institution.

## Rationale

With the advancement of the internet and open platforms (YouTube, Wikipedia, online libraries) billions of people are getting access to free or almost free educational content. As this trend continues, more and more people around the world will be able to acquire same level of education as students from top universities. The problem however is that they don't have any way to demonstrate those qualifications unless they are able to enroll and pay for the degree, test or certification.

Current model of educational credentials issuing is not ideal due to the fact that it only captures the fact of completion of some formal educational program but actual competencies and skills. On the other hand, employers are more interested in applied skills rather than abstract learning history no matter if it was an official degree, online course or self-education.

## Decentralized Issuance of Verifiable Credentials

We propose building a decentralized protocol called Credentia that involves at least 3 of the user groups described below. Credentials are issued by the network and only Credential subject posses keys to prove ownership.

Parties included in our proposed network are:

1. Student — person
2. Expert — person
3. Verifiable Credential Issuer — open sourced software of the Network
4. Verifiable Credential Verifier — employer, institution or any organization that requires Student to prove certain competency
5. Watcher — any user of the Network who is not Student or Expert

## Assessment Process

Assessment is done in purely online fashion that gurantees scalability of the system. This reflects inherent permissionless nature of the protocol.

Credentia network and user-faced applications built on top of it provide a variety of assessment methods which can be used by Experts with no charge. Typical competency assessment process starts with an Expert or group of Experts creating a verification process in Credentia Test Constructor software. While creating the test they are able to utilize and order test items which may consist of one or many different types. Those types include but not limited to:

- Multiple Choice Question
- Open Question
- Upload a File
- Code
- Screencast
- Interview
- Group Work
- Chat

Once assessment test is created Students are able to take it. Results are saved on IPFS node and are accessible publicly. Experts have permission to rate test results. Once threshold of ratings is reached, credential is issued with *pass* or *not pass* properties.

## Data Model

In order to preserve properties of decentralization and self-sovereign identity all data in anonymized and public:

- Anonymity property ensures no user identifying information can be leaked without explicit permission for user.
- Publicity property ensures track record of any interaction between Student and Expert on the platform, thus gives a proof of competency verification process.

In addition to standard VC claim:

    {
      "@context": [
        "https://www.w3.org/2018/credentials/v1",
        "https://example.org/examples/v1"
      ],
      "id": "http://example.edu/credentials/3732",
      "type": ["VerifiableCredential", "CompetencyCredential"],
      "issuer": "https://example.edu/issuers/14",
      "issuanceDate": "2010-01-01T19:23:24Z",
      "credentialSubject": {
        "id": "did:example:ebfeb1f712ebc6f1c276e12ec21",
        "competency": {
          "type": "MarketingCompetency",
          "name": "Mobile App Analytics",
    			"competencyLevel": "3",
        }
      },
      "proof": { ... }
    }

We then add customized *evidence* property, which has examiner's information such as link to examiner profile, their DID and signature. 

      "evidence": [{
        "id": "https://example.edu/evidence/f2aeec97-fc0d-42bf-8ca7-0548192d4231",
        "type": ["ExpertVerification"],
        "examiner": [{
    				"examinerName": "https://credentia.me/experts/14",
    				"id": "did:example:fac4...ab",
    				"proofValue": "DgYdY...SVfRrs1D"
    		}],
        "verificationData": "https://credentia.me/exams/f2aeec97-fc0d-42bf-8ca7-0548192d4231",
        "verificationDate": "2010-01-01T19:23:24Z",
        "verificationResult": "passed"
      },{
    		"id": "https://example.edu/evidence/f2aeec97-fc0d-42bf-8ca7-0548192d4444",
        "type": ["ExpertVerification"],
        "examiner": [{
    				"examinerName": "https://credentia.me/experts/14",
    				"id": "did:example:fac4...ab",
    				"proofValue": "DgYdY...SVfRrs1D"
    		}],
        "verificationData": "https://credentia.me/exams/f2aeec97-fc0d-42bf-8ca7-0548192d4444",
        "verificationDate": "2010-01-01T19:33:24Z",
        "verificationResult": "passed"
      }],

## Threat Model

The model described above is subject to several possible attacks that can undermine the value produced by the network:

1. Verifiers are not diligent enough in their work
2. Collusion between Verifier and Student
3. Watchers not being active in the network

In order to mitigate these threats we propose creating an incentive-based mechanism that will minimize risk of fraud and ensure trust maximization.

## Mechanism Design for Fraud Minimization

The goal is to construct an incentive-compatible mechanism where truthful and honest behavior is a dominant strategy for all relevant parties (Student, Expert, Watcher). To achieve this we utilize Dispute Rounds mechanism initially developed by Augur [[https://www.augur.net/whitepaper.pdf](https://www.augur.net/whitepaper.pdf)].

We propose using staking and slashing strategy in order to guarantee financial incentives for correct reporting for all parties involved. We require Experts to submit a stake before attempting to rank existing Students. After the fact of successful exam stake will be frozen for 7 days. At this time any other user (Watcher) is able to review examination materials and process and start dispute round if they find any signs of fraud. Starting dispute round will require Watcher to submit double of the Expert stake.

Dispute ROI for the winning party is always 40% and 10% is always burned in order to prevent dispute exploitation. This way any user has positive expected ROI for truthful reporting and financial incentives are in place in order to prevent collusion or corruption.

If the dispute is passed, Credentia network will issue Verifiable Credential with *type* of ***Dispute Credential***.

## Web of Trust for Competencies and Next Steps

Model described in this paper still relies on centralized model of competencies and rubrics. Ideal network should also feature some sort of DAO-based instruments for community to come up with relevant and up-to-date map of skills and rubrics describing grading criteria and defining different levels for each competency.
