# BTCR Continued

Authors: Francesco Micheli, Kim Hamilton Duffy, Anthony Ronning

# Overview
We'll continue to interate on the BTCR specification, libraries, and mobile tools

We will continue making progress on the issues identified from the [last BTCR Hackathon](https://weboftrustinfo.github.io/btcr-hackathon-2019/final_report.html) and iterate on BTCR Android support. The latter is outlined below. 

## BTCR DID Support on Android

**Abstract**

The aim is to create a Java library to do BTCR DID Resolution using the btcrservice written in Go to generate a DID Document from a BTCR DID.

The library can be used to integrate a BTCR DID Resolver inside a Bitcoin wallet for Android.



1. Resolve an existing BTCR DID
    1. Purpose: Given btcr did generate a DDO
    2. Use txref resolver: [https://github.com/WebOfTrustInfo/txref-conversion-java](https://github.com/WebOfTrustInfo/txref-conversion-java)
    3. Fetch the transaction using [https://github.com/kulpreet/btcr-service](https://github.com/kulpreet/btcr-service)
        1. No auth required
        2. Probably need txref resolver
    4. Follow UTXO from c??
        3. If unspent you can generate a minimal DDO - Goal: Display this in your app
        4. If spent, follow tip and then if unrevoked (i.e. unspent) then generate a DDO
    5. Notes:
        5. [https://github.com/w3c-ccg/did-hackathon-2018/blob/master/BTCR-DID-Tests.md](https://github.com/w3c-ccg/did-hackathon-2018/blob/master/BTCR-DID-Tests.md)
        6. [https://weboftrustinfo.github.io/btcr-tx-playground.github.io/](https://weboftrustinfo.github.io/btcr-tx-playground.github.io/)
        7. [https://github.com/WebOfTrustInfo/btcr-did-tools-js](https://github.com/WebOfTrustInfo/btcr-did-tools-js) 
2. Create a new BTCR DID
    6. Import key or have an existing key in your wallet
    7. Spend a UTXO
        8. Minimal DID: Which is the simple case we used in BTCR resolution as well
        9. With details: simply a URL in op_return
3. Generate Verifiable Credential/Claim
    8. Once you have your bitcoin private key

<!-- Docs to Markdown version 1.0β17 -->
