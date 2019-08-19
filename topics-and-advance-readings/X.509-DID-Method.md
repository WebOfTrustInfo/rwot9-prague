# X.509 DID method

### Decentralising PKI starting with a X.509 DID method

By Bas Kaptijn (ICTU, https://discipl.org), Steven Gort (ICTU, https://discipl.org), Dr. Carsten Stöcker (Spherity GmbH, https://spherity.com/)

At this moment the only way for governments in the EU to issue verifiable credentials that can easily be converted into valid digitally signed documents is to sign them with a valid X.509 certificate bridging the existing federated PKI with the new SSI world. The paper about a decentralised PKI in 2015 <sup>[1](#1)</sup> discusses the flaws of this existing PKI system and proposes to decentralise it in a way the X.509 certificates get to be self issued and registered in a decentralised way on blockchain type of platforms. This paper proposes to just start this transition with an X.509 DID (sub)method that can be used by non-natural persons as issuers like governments, with their (existing) X.509 certificates to start a hybrid situation that helps shifting towards adoption of SSI.<br><br>
We propose using an X.509 DID method or X.509 DID submethod in which the DID itself contains the fingerprint of the X.509 certificate used for signing the issued verifiable credential data. This could be a new DID method, or it could be a submethod with which existing methods could optionally provide a way to use existing X.509 certificates to sign credentials.

This way, organisations like governments that have their own PKI system in place and have less privacy concerns for themselves than individual natural persons <sup>[2](#2)</sup> can use these existing systems for issuing verifiable credentials. All X.509 DID method operations are implicit and tied to such existing PKI systems (with all their flaws); it is easy to implement.

Note that a verifiable credential issued with an X.509 DID can easily be transformed into an ETSI TS 103 171 <sup>[3](#3)</sup> compliant document <sup>[4](#4)</sup> so for instance a XaDES document by adding the X.509 public keys from the one that is used for signing to the PKI root certificate. Such keys are often easily obtained afterwards or could be retrieved at time of issuing. This enables people within the EU to use a verifiable credential issued with this method to proof facts about themselves across borders within the EU and which all countries are bound to accept due to eIDAS regulation <sup>[5](#5)</sup>.

Like with existing X.509 based solutions, on itself you can not automatically resolve a fingerprint to a public key with which one can validate a signed piece of information; the public key must already exist in the local trusted key store previously installed there manually, or the validator must get or imply a reference to where to find this public key.

Such a reference is proposed to be found in a DID document (DDO) and a possibility is to use an extension block in the X.509 certificate itself as a DDO. But that would still need a way to resolve the fingerprint to where to find this DID document and which just adds a level of indirection and reintroduces the problem of how to resolve it.  Alternatively a derived DID that just includes this reference or a part thereof could be used. Though we propose not to use URLs tied to existing PKI infrastructure regarding domain names here nor centralised service endpoints. Instead it could just be left to the validator to choose some official key registry service on some platform themselves in which the validator would expect the issuer has registered their key and which they trust. Such a service might be implied more specifically from the DID (submethod) too, so then the (sub)method is the reference at the same time.

When following this line of thought there are multiple ways to define X.509 DID’s as denoted in the table below:

| did | format | how to resolve | note |
| --- | --- | --- | --- |
| 1. loosely coupled | did:x509:<fingerprint> | manually or through existing means of user’s choice | user (or the software the user trusts and uses) determines key “registry” |
| 2. tied to (sub)method | did:method:x509:<fingerprint>, did:method:submethod:x509:<fingerprint> | through ledger implied from (sub)method | (sub)method implies a certain (decentralised) key registry possibly without indirection through DDO |
| 3. referenced in dDID | did:method:identifier/x509:<fingerprint> | through service endpoint found in DDO (method specific) along with the included extension (part after “/”) | this is almost the same as (2) though more compatible with dDID’s<sup>[6](#6)</sup> |


For example: DID’s like “did:discipl:nlx:x509:<fingerprint>” could be used in which the submethod “nlx” refers to the [NLX](https://nlx.io/) platform that might refer to a specific registry of public keys issued somewhere under the Dutch root PKI certificate and these public key certificates refer to official organisation id numbers (called OIN being a subset of OID’s) of the organisations within government. The fingerprint identifies the public key with an OIN denoting the issuing entity to be found in the registry.

Note that X.509 DID’s issued by CA’s are not to be used for natural persons and you actually want to reuse them for signing VC’s quickly relating to a sufficiently large random group of different natural persons (with their own random DID’s) to help prevent linkability issues <sup>[7](#7)</sup>. Sure, against numerous SSI principles, when a certificate gets revoked this would invalidate a large group of VC’s which might have an impact on a big group of natural persons so also these verifiable credentials should have a limited lifetime to begin with and not be used as the source of “truth” of information about natural persons which limits their use cases. It can only prove that as far as a certain issuer knows, assuming only the issuer is in control of a certain private key, the given data holds.

X.509 DID’s are a good way for entities that do not represent natural persons, so-called legal persons to refer to themselves in a verifiable manner using existing systems in place. These DID’s themselves are not considered personal data in relation to the GDPR because they do not represent natural persons. This is different for DID’s of natural persons. These DID’s should probably only really temporary and kept private. In a separate future paper <sup>[8](#8)</sup> this will get elaborated upon and it is proposed to link the lifetime of DID’s to the lifetime of a need getting solved and to the context of actors that need access to it, starting in an anonymous by design way in public to a private peer to peer conversation.

X.509 DID’s can accelerate the adoption of the DID and Verifiable Credential standards and might start the transition in which the current PKI infrastructure for legal persons gets more decentralised too.

## Example use case : Waardepapieren

As an example, the Waardepapieren project in the Netherlands is aiming to use X.509 DID’s to have municipalities issue all kinds of valid proofs, not to be used for identification of a holder, in a digital way instead of issuing in print on specific watermarked paper as is done uptil now.

A minimal credential like one in the waardepapieren project <sup>[9](#9)</sup> conforming to the latest W3C v0.13 draft would be:

```
{
"@context": "https://www.w3.org/2018/credentials/v1",
“id” : "link:discipl:ephemeral:394799234772934879324...",
“type” : ["VerifiableCredential", "Uittreksel-GBA-woonplaats"],
"issuer" : "did:discipl:nlx:x509:2349837EF9032783278CD93434..."
"issuanceDate" : "2017-01-01T19:23:24Z"
"credentialSubject": {
"BSN" : "123456789"
"CityLivingIn" : "The Hague"
}
}
```

Note that the id is a so called verifiable claim link, a concept as defined in the [Discipl](https://discipl.org/home/technology/) project, that also includes the signature the issuer signed the claim with. Instead of storing such link in the id property (which is optional) the signature could be stored in a proof property. Besides links Discipl however also defines verifiable claim set exports that includes the did’s and links to possibly nested verifiable claims, which you can use as linked data and intuitively should be stored as credential subject removing the need of many other properties. All this is out of scope of this paper however and to be discussed in a separate paper already mentioned above. However, this is why currently this solution does not (yet) follow the verifiable credential standard in an exact way until now though it easily could.

<br>
<a id="1">1: https://github.com/WebOfTrustInfo/rwot1-sf/blob/master/draft-documents/Decentralized-Public-Key-Infrastructure-CURRENT.md </a>

<a id="2">2: Instead of natural persons information like public keys from legal persons, especially big non commercial organisations, are not to be seen as personal data within the GDPR: https://www.europarl.europa.eu/stoa/en/document/EPRS_STU(2019)634445</a>

<a id="3">3: https://www.etsi.org/deliver/etsi_ts/103100_103199/103171/02.01.01_60/ts_103171v020101p.pdf</a>

<a id="4">4: A verifiable credential seems really grown to be a sort of JSON Advanced Electronic Signature (JaDES) anyways.</a>

<a id="5">5: https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/eSignature+standards</a>

<a id="6">6: as for example discussed in https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/A_DID_for_everything.pdf</a>

<a id="7">7: if a DID of an issuer is made holder specific, different VC’s of the same holder could be linked across validators</a>

<a id="8">8: a future paper with the title "Rebooting Society" is currently being worked on</a>

<a id="9">9: https://github.com/discipl/waardepapieren/</a>
