## Zion Key Management SDK Sets and SLIP-39 for Social Key Recovery

Authors: Hank Chiu, Hankuan Yu, David Chen, Jon Tsai

### Introduction

The goal of HTC EXODUS devices is to provide users to own their private keys on blockchain. And to maximize the capability of that, we believe open to the community is important. Therefore, we create the SDK sets for Zion Key Management APIs to help developers to use and to explore more real use cases of using user's own keys. Below briefs how each SDK works:

- ZKMA/ZKMS
  - For apps that need standalone wallet feature, e.g., Opera, BCH wallet.
  - Support major coins, e.g., BTC, ETH, LTC, XLM...etc., and more coins on the plan, e.g., BCH, BNB.
  - Support collectibles, e.g., Cryptokitties, Ethermon, Decentraland...etc.
- Zion Vault SDK
  - For exchange purpose apps, e.g., Simplex, Nodle.
  - More exchanges on the plan, e.g., HashPower.
- Zion SKR SDK
  - For social key recovery feature
  - V1.0 (Jul. 2019)  
    3rd party apps can backup or restore seeds using HTC UI and UX.
  - V1.2 (Sep. 2019)  
    3rd-party apps can fully customize UI and flow on their own.

![SDK](media/skr_sdk.png "SDK")


### ZKMA/ZKMS

ZKMA (Zion Key Management API) is a service which provides a way for developers to manage seed security built into HTC EXODUS devices, which integrates Zion protection. All secure operations (input pin, display seed, sign transaction…) will be performed by the trusted OS and no secure data exposed to the rest of Android.
<p align="center"><img src="https://raw.githubusercontent.com/wiki/htczion/ZKMA/image/1.png" align="middle" width="700"></p>
    
<p align="center"> <b>Figure 1. ZKMA API call flow</b></p>
  
ZKMA APIs can be called directly or bound as ZKMS of HTC Zion Vault. For performance, our suggestion is you can call ZKMA by ZKMA.aar. Another way which is ZKMS can be used for reducing your APK size. 

|   | ZKMA  | ZKMS  |
|:-:|:-:|:-:|
Library name|  ZKMA.aar |  ZKMS.aar |   |
File Size| 7 MB~  | 20 KB~  |   |
Architecture| Direct call API via ZKMA library  | Call API via ZKMS service  |   |
HTC Zion Vault App| Unnecessary  |  Mandatory |   |

<b>Table 1. A comparison between ZKMA and ZKMS libraries</b>


### ZionVaultSDK

This SDK provides two major functions：

1. Get crypto currency account address from Zion Vault.
2. Request Zion Vault to sign a transaction.

Zion SDK offers two approaches to integrate Zion Vault with the transaction service provided by cryptocurrency exchange services providers：  

1. Web base integration：Zion Vault loads a mobile web page that provided by exchange service provider.
2. Application base integration：Exchange service provider implements an Android application to work with Zion Vault.

<p align="center"><img src="https://github.com/htczion/ZionVaultSDK/wiki/media/28d4ce4b1cf38cfb03eafcbe6d79a94f.png" align="middle" width="700"></p>


### SKR Architecture

The below architecture diagram describes the components involved when we implement the Social Key Recovery.

![Architecture](media/skr_architecture.png "Architecture")


### SLIP-39 in SKR 2.0

SLIP-39 describes a standard and interoperable implementation of Shamir's secret sharing (SSS). SSS splits a secret into unique parts which can be distributed among participants, and requires a specified minimum number of parts to be supplied in order to reconstruct the original secret. Knowledge of fewer than the required number of parts does not leak information about the secret. In order to support the SLIP-39 and make the apps that use Zion-SKR-SDK can also recover the seed on different apps, we have implemented a C library for SLIP-39 
[https://github.com/Seclabs-htc/slip39](https://github.com/Seclabs-htc/slip39).
