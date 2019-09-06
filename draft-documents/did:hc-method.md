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
   <td>Marcus Sabadello<br/>
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



## CRUD Operation Definitions
The crud operation for the did:holo
Why do we let people create did's via your public gateway

### Read (Resolve / Verify a DID)
This will read the status of the did.
1. make a api call to the [DeepKey DNA](https://github.com/Holo-Host/DeepKey) with zome as `dpki` and function`key_status`
2. if `return = Live`:
    - Return the DID Doc with an `authorization` field.
`"authentication": "sec:authenticationMethod",`
3. else if `return = Updated` 
    - Return the DID Doc with an `revoke` field.
`"revoked": {"@id": "sec:revoked", "@type": "xsd:dateTime"}`
4. else if `return = Deleated` 
    - Return the DID Doc with an `expired` field.
`"expires": {"@id": "sec:expiration", "@type": "xsd:dateTime"}`
5. else if `return = Err`(Not Found) 
    - Return 404 Error.

### Create (Register)
> **Not Supported**

Holochain is a lightweight, peer-to-peer framework. If you need to create, up in order for keys to properly validated We can create a new DNA that provides the keys, but at the moment we would not be providing a create options.
instead to create a key would require you to run a holochain source chain.



### Update
> **Not Supported**

### Delete (Revoke)
> **Not Supported**

## Security Considerations
ToDo...

## Privacy Considerations
ToDo...

## Performance Considerations
ToDo...

## References
1. [DID Spec](https://w3c-ccg.github.io/did-spec/)
2. [did:erc725 method](https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/topics-and-advance-readings/DID-Method-erc725.md)
