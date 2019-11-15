# did:holo method

## Author

<table style="text-align: center; border-width: 0;">
  <tr>
   <td>Joel Ulahanna
   </td>
   <td>Arthur Brock<br/>
   </td>
   <td>Manu Sporny<br/>
   </td>	  
   <td>Kim Hamilton Duffy<br/>
   </td>
   <td>Markus Sabadello<br/>
   </td>
   <td>Dmitri Zagidulin<br/>
   </td>
   <td>Dan Burnett<br/>
   </td>	  
</tr>
</table>


## Abstract 
Decentralized Identifiers (DIDs, see [1]) are designed to be compatible with any distributed ledger or network (called the target system). We will be specing and prototyping a `DID` method for holochain.


## DID Method Name

The name-string that shall identify this DID method is: `holo`.

A DID that uses this method **MUST** begin with the following prefix: `did:holo`.

## Method Specific Identifier

The method specific identifier is composed of an optional Holochain network identifier with a : separator, followed by a Hex.

    holo-did = "did:holo:" holo-specific-idstring
    holo-specific-idstring = [ holo-network  ":" ] holo-address
    holo-network  = "mainnet" / "testnet"
    holo-address  = (Hex-encoded smart contract address)

### Example

`holo` DIDs:

 - `did:holo:b2B37C890824242Cb9B0FE5614fA2221B79901E`
 - `did:holo:mainnet:b2B37C890824242Cb9B0FE5614fA2221B79901E`
 - `did:holo:testnet:b2B37C890824242Cb9B0FE5614fA2221B79901E`

## DID Document

### Simple Example
    {
        "@context": "https://w3id.org/did/v1",
        "id": "did:holo:mainnet:b2B37C890824242Cb9B0FE5614fA2221B79901E",
        "authentication": {...},
        "revoked": {...},
        "expires": {...},
        "service": [...]
    }


### Alternate Example:
	{
		"@context": ["https://w3id.org/did/v1", "https://holochain.org/did/v1"],
		"id": "did:holo:mainnet:b2B37C890824242Cb9B0FE5614fA2221B79901E",
		"authentication": {
			"id": "did:holo:mainnet:b2B37C890824242Cb9B0FE5614fA2221B79901E#key-1",
			"type": "Ed25519SignatureAuthentication2018",
			"publicKeyMultibase": "zHcSciNw8EPFNprfjnvpoZ97hTYZPb97zdkjqiTmb8epjozf5iC8XoQmxnvdrfea"
                },
		// in base DID spec (eventually, maybe)
		"keyAgreement": {...}, // for doing key agreement (generating key agreement key)
		"assertionMethod": {...}, // for signing verifiable credentials
		"capabilityInvocation": {...}, // for invoking authorization capabilities
		"capabilityDelegation": {...}, // for delegating authorization capabilities

                // holochain specific (might not make sense)
		"appStateChange": {...},
		"keyManagementAuthorization": {...},
		"keyManagementRevocation": {...},
		// do not sweat services, they are still being worked out, you don't need them yet
		"service": [...]
	}

## Set up your local instance of DeepKey

Please refer [this link](https://hackmd.io/xp5h1bkLRy-oef45tiJ1yw) to set up your local DeepKey instance 

## CRUD Operation Definitions
The crud operation for the did:holo
To run the crud operation you have to set up your local DeepKey instance, and make API calls as defined bellow.
To understand how to make API calls to a holochain conductor please refer to the [Holochain Developer Docs](https://developer.holochain.org/guide/latest/conductor_json_rpc_api.html)

### Read (Resolve / Verify a DID)
**DNA:** DeepKey
**Zome Name:** dpki
**Function Name:** key_status
**params:** `{key:""}`

```=curl
curl -X POST -H "Content-Type: application/json" -d '{"id": "0", "jsonrpc": "2.0", "method": "call", "params": {"instance_id": "dpki_happ", "zome": "dpki", "function": "key_status", "args": {key:""} }}' http://127.0.0.1:8800
```

### Create (Register)

Holochain is a lightweight, peer-to-peer framework. If you need to create, up in order for keys to properly validated We can create a new DNA that provides the keys, but at the moment we would not be providing a create options.
instead to create a key would require you to run a holochain source chain.

**DNA:** DeepKey
**Zome Name:** dpki
**Function Name:** create_agent_key
**params:** `{agent_name:""}`

```=curl
curl -X POST -H "Content-Type: application/json" -d '{"id": "0", "jsonrpc": "2.0", "method": "call", "params": {"instance_id": "dpki_happ", "zome": "dpki", "function": "create_agent_key", "args": {agent_name:""} }}' http://127.0.0.1:8800
```



### Update

**DNA:** DeepKey
**Zome Name:** dpki
**Function Name:** update_key
**params:** `{old_key:"", signed_old_key:"", context:""}`

```=curl
curl -X POST -H "Content-Type: application/json" -d '{"id": "0", "jsonrpc": "2.0", "method": "call", "params": {"instance_id": "dpki_happ", "zome": "dpki", "function": "update_key", "args": {old_key:"", signed_old_key:"", context:""} }}' http://127.0.0.1:8800
```

### Delete (Revoke)

**DNA:** DeepKey
**Zome Name:** dpki
**Function Name:** delete_key
**params:** `{old_key:"", signed_old_key:""}`

```=curl
curl -X POST -H "Content-Type: application/json" -d '{"id": "0", "jsonrpc": "2.0", "method": "call", "params": {"instance_id": "dpki_happ", "zome": "dpki", "function": "delete_key", "args": {old_key:"", signed_old_key:""} }}' http://127.0.0.1:8800
```
## Security Considerations
Security of `holo` DIDs inherits security properties of Holochain itself. Holochain does not have global state or a classic "consensus algorithm". Instead it relies on distributed validation rules which define data integrity. It is a much simpler problem to achieve data integrity if there is no requirement to have a globally shared state or an absolute order of events. Data is replicated among a configurable number of nodes in Holochain's DHT. Theoretically, a piece of data can be compromised if an attacker can gain control of a sufficient number of DHT nodes. An attacker however is not able to predict or influence which nodes in the DHT store a copy of the data, since those nodes are chosen randomly based on the content itself.

## Privacy Considerations
All transactions on Holochain are signed by a user's key. Therefore, by learning a `holo` DID, an observer/attacker is able to link the user's Holochain activities with potential DID-based applications such as DID Auth or Verifiable Credentials. Users should be aware that he/she can publish their own data associated with their public key on a specific Holochain network.

## Performance Considerations
Since Holochain is based on a DHT as well as local data storage, it has much better performance characteristics than a "traditional" blockchain such as Bitcoin or Ethereum. A write operation to Holochain's DHT takes less than 2 seconds to be accepted. Key generation takes about 15 seconds.

## References
1. [DID Spec](https://w3c-ccg.github.io/did-spec/)
2. [did:erc725 method](https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/topics-and-advance-readings/DID-Method-erc725.md)
