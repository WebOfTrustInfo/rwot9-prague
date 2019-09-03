# did:hc method

## Author

<table style="text-align: center; border-width: 0;">
  <tr>
   <td>Joel Ulahanna
   </td>
   <td>Kim<br/>
   </td>
   <td>Marcus<br/>
   </td>
  </tr>
</table>


## Abstract 
We will be specing and prototyping a `DID` method for holochain.


## DID Method Name

The name-string that shall identify this DID method is: `hc`.

A DID that uses this method **MUST** begin with the following prefix: `did:hc`.

## Method Specific Identifier
    hc-did = "did:hc:" hc-specific-idstring
    hc-specific-idstring = [ hc-network  ":" ] hc-address
    hc-network  = "mainnet" / "testnet"
    hc-address  = (Hex-encoded smart contract address)
### Example

Example `hc` DIDs:

 - `did:hc:Qe2B37C890824242Cb9B0FE5614fA2221B79901E`
 - `did:hc:mainnet:Qe2B37C890824242Cb9B0FE5614fA2221B79901E`
 - `did:hc:testnet:Qe2B37C890824242Cb9B0FE5614fA2221B79901E`

## DID Document

### Example

	{
		"@context": "https://w3id.org/did/v1",
		"id": "did:hc:mainnet:Qe2B37C890824242Cb9B0FE5614fA2221B79901E",
		"publicKey": [{
			"id": "did:hc:mainnet:Qe2B37C890824242Cb9B0FE5614fA2221B79901E#key-1",
			"type": "HCSigningKey",
			"publicKeyHex": "HcSciNw8EPFNprfjnvpoZ97hTYZPb97zdkjqiTmb8epjozf5iC8XoQmxnvdrfea"
		}, {
			"id": "did:hc:mainnet:Qe2B37C890824242Cb9B0FE5614fA2221B79901E#key-2",
			"type": "HCEnctyptionKey",
			"publicKeyHex": "HcSCIiHwBMkj54n6kmrQsnNtETucepmvyRcgefKJ6Re4ewe5KOncyQ8wkuyazrz"
		}],
		"authentication": {
			"type": "Secp256k1SignatureAuthentication2018",
			"publicKey": "did:hc:mainnet:Qe2B37C890824242Cb9B0FE5614fA2221B79901E#key-2"
		},
		"service": []
	}

## CRUD Operation Definitions
The crud operation for the did:h
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
