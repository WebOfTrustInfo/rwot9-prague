# Publicly verifiable split-key schemes for hybrid secret sharing and multi-sig authorization

## by Mark Friedenbach, Christopher Allen

Social key recovery schemes allow users to specify groups of individuals that
acting together possess the ability to recover the root secret of the user.  The
most popular social key recovery schemes, such as Shamir Secret Sharing, combine
shares to reconstruct the original secret on a single machine, where it can then
be used for signing authorization or other purposes.

Multi-signature schemes, such as [MuSig over Schnorr][1], allow groups of
individuals acting together to create signatures for a combined private key that
is never materialized as part of the signing process.  Threshold multi-signature
schemes extend this core capability to create k-of-n signing thresholds for some
set of key holders[2].

There is a deep connection between social key recovery and threshold
multi-signature schemes, as the same mathematics underly both:

* A social key recovery scheme starts with a single secret and splits it into N
  shares.  A multi-signature scheme starts with N independent public keys and
  combines them into a single public key representing the entire set of signers.

* In secret sharing private keys (shares) are combined to (re-)construct the
  master secret, which can then be used to sign or decrypt messages.  In
  multi-signature schemes a similar recombination is performed homomorphically
  over signatures values in order to interactively construct a signature of the
  combined key without placing the master secret at risk.

In both instances we use the same equations, what differs is whether you start
with a master key and derive shares in a dealer mode, or whether you start with
independent keys and (homomorphically) combine to discover the master (public)
key.

In principle this commonality allows for the specification of a protocols that
combine both approaches, allowing users to choose whether to initialize by
splitting a secret or multi-party compute, or to recover the master secret or
create signatures without revealing shares.  However such hybrid applications
only become possible when the threshold secret sharing is done over the same
group as the elliptic curve used in the signature scheme, and requires the
shared secret to be the actual master secret, not message data or an ephemeral
encryption key as is often done in traditional Shamir secret sharing.

Performing threshold secret sharing of an asymmetric secret over the same group
as the signature scheme has one further advantage: the scheme is (publicly)
verifiable secret sharing, or VSS.  A VSS permits arbitrary third parties that
did not partake in the secret split to nevertheless verify that the distributed
shares are sufficient to reconstruct the secret or generate a signature.  This
use case is of particular interest as a self-sovereign alternative in situations
where key escrow has been traditionally required by regulators: a public auditor
could ensure that sufficient shares to reconstruct a secret have been dutifully
backed up, e.g. by encrypting them to a set of functionaries for that purpose.

This paper intends to explore how practical, near-term publicly verifiable
split-key schemes differ from the presently deployed traditional Shamir secret
sharing, and what those differences imply for application protocols.  We also
intend to show how existing Shamir secret sharing schemes can be modified to
permit future upgrades to publicly verifiable, hybrid VSS schemes, and what
implications that has for exposed interfaces.

## References

[1]: "MuSig: A New Multisignature Standard."  Andrew Poelstra, Blockstream
     Research.
     <https://blockstream.com/2019/02/18/en-musig-a-new-multisignature-standard/>

[2]: "Implementing Compact Threshold MuSig Signatures."  Andrew Poelstra, SF
     Bitcoin Devs.  <https://www.youtube.com/watch?v=j9Wvz7zI_Ac>