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
We will be specing and prototyping a `DID` method for holochain.


## DID Method Name

The name-string that shall identify this DID method is: `holo`.

A DID that uses this method **MUST** begin with the following prefix: `did:holo`.

## Method Specific Identifier
    holo-did = "did:holo:" holo-specific-idstring
    holo-specific-idstring = [ holo-network  ":" ] holo-address
    holo-network  = "mainnet" / "testnet"
    holo-address  = (Hex-encoded smart contract address)
### Example

Example `holo` DIDs:

 - `did:holo:b2B37C890824242Cb9B0FE5614fA2221B79901E`
 - `did:holo:mainnet:b2B37C890824242Cb9B0FE5614fA2221B79901E`
 - `did:holo:testnet:b2B37C890824242Cb9B0FE5614fA2221B79901E`

## DID Document

### Example

	{
		"@context": ["https://w3id.org/did/v1", "https://holochain.org/did/v1"],
		"id": "did:holo:mainnet:b2B37C890824242Cb9B0FE5614fA2221B79901E",
		"authentication": {
			"id": "did:holo:mainnet:b2B37C890824242Cb9B0FE5614fA2221B79901E#key-1",
			"type": "Ed25519SignatureAuthentication2018",
			"publicKeyMultibase": "zHcSciNw8EPFNprfjnvpoZ97hTYZPb97zdkjqiTmb8epjozf5iC8XoQmxnvdrfea"
                },
		// in base DID spec (eventually, maybe)
		"keyAgreement": {...}, // for doing Encryption key agreement (generating key agreement key)
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
The crud operation for the did:holo Method
### Create (Register)
instance_id: dpki_happ
Zome: dpki
Function: create_agent_key

### Read (Resolve)
instance_id: dpki_happ
Zome: dpki
Function: key_status

### Update
instance_id: dpki_happ
Zome: dpki
Function: update_key

### Delete (Revoke) 
instance_id: dpki_happ
Zome: dpki
Function: delete_key

## Security Considerations
ToDo...

## Privacy Considerations
ToDo...

## Performance Considerations
ToDo...
