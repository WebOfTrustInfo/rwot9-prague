
Authors

Chris Howe, Bryan Bishop, Mark Friedenbach, Christopher Allen, Yancy Ribbens, Hank Chu, ChiaWei Tan, Laurence Chen

# Abstract

Social key recovery allows users to collaborate with each other to securely recover their secrets instead of using centralized account reset procedures. Shamir secret sharing is an increasingly popular implementation for social key recovery, where a secret can be split into a number of shares with various threshold requirements or in the future any arbitrary monotone boolean function.

SatoshiLabs' SLIP 39 is one proposed implementation of Shamir secret sharing with mnemonics. SLIP 39 is Simple Shamir Secret Sharing plus a two-level fixed threshold group, and a mnemonic text encoding scheme, and an encryption scheme as well.

We are uncomfortable with some of the decisions in SLIP 39 and uncomfortable with the fact that they are all bound together tightly. In light of this, we are writing a Bitcoin Improvement Proposal that is loosely inspired by SLIP 39. In this BIP, the proposal includes a binary format, additional metadata (such as birthdate), allows for the greater flexibility of thresholds, and one of the goals is to make the design so that it is possible to independently audit the independent parts of the proposal, making the proposal more modular. It will also be compatible with future upgrades like verifiable secret sharing and MuSig.

We are looking forward to championing this proposal in the community, collecting feedback, and driving the improvement proposal process. We also propose to make an implementation as required by the BIP process.
