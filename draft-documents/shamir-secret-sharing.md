# Shamir secret sharing BIP

<http://diyhpl.us/wiki/transcripts/rebooting-web-of-trust/2019-prague/shamir-secret-sharing/>

## Authors

Chris Howe, Bryan Bishop, Mark Friedenbach, Christopher Allen, Yancy Ribbens, Hank Chu, ChiaWei Tan, Laurence Chen

## Abstract

Social key recovery allows users to collaborate with each other to securely recover their secrets instead of using centralized account reset procedures. Shamir secret sharing is an increasingly popular implementation of social key recovery, where a secret can be split into a number of shares with various threshold requirements or in the future any arbitrary monotone boolean function.

SatoshiLabs' SLIP 39 is one proposed implementation of Shamir secret sharing with mnemonics. SLIP 39 is Simple Shamir Secret Sharing plus a two-level fixed threshold group, and a mnemonic text encoding scheme, and an encryption scheme as well.

We are uncomfortable with some of the decisions in SLIP 39 and uncomfortable with the fact that they are all bound together tightly. In light of this, we are writing a Bitcoin Improvement Proposal that is loosely inspired by SLIP 39. In this BIP, the proposal includes a binary format, additional metadata (such as birthdate), allows for the greater flexibility of thresholds, optional pre-defined pre-parameterized threshold requirement templates, and one of the goals is to make the design so that it is possible to independently audit the independent parts of the proposal, making the proposal more modular. It will also be compatible with future upgrades like verifiable secret sharing and MuSig.

We are looking forward to championing this proposal in the community, collecting feedback, and driving the improvement proposal process. We also propose to make an implementation as required by the BIP process.

## Term glossary

Shard dealer: An individual that has a secret that is sharded using this secret sharing scheme. The user makes a number of shards that are dealt out to different users to turn each user into a shard custodian.

Deck: A collection of shards that together can be combined (in at least one way) to reconstruct the original secret.

Script policy: A script that specifies a policy for how the deck's secret (seed entropy) can be reconstructed from some combination of shards.

Quorum: Any set shards sufficient to meet the script policy for reconstruction.

Shard: A member of a deck, with both unencrypted visible information (including a shard value) and encrypted hidden information. The encrypted hidden information is encrypted by the original secret, and the dealer distributes the encrypted hidden information to each user. You want to know the unencrypted metadata, the identifier information, then there's private data which is encrypted with the key which gets derived from the secret. Then there's the y value, and then a checksum over all of this.

Shard unencrypted metadata (public metadata): Data associated with a shard that describes the shard and the deck among other things. This includes birthdate, identifier information, and so on.

Shard value: The mathematical or cryptographic value that can be used in the secret sharing scheme to reconstruct the original secret. This is the y value.

Private data (encrypted) (encrypted blob or deck blob): Encrypted data transferred with each shard. The decryption key can be computed by recombining all the shards.

Shard custodian: A user that holds a number of shards, possibly from multiple different decks.

Shard pool: A shard custodian can use software that implements a shard pool that contains their collection of shards they are responsible for. The shard pool allows for querying over the set of shards to find particular shards to respond to a request.

Seed entropy: Used to create the derived secret.

Derived secret: The derived secret is used to decrypt the identical private data associated with each shard.


