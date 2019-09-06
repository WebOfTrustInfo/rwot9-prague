# did:snail: A DID Method for the Real World

By Amy Guy &lt;amy@rhiaro.co.uk&gt;, Yancy Ribbens, & Dmitri Zagidulin

This submission is a snapshot of a new DID Method under development. Links to the ongoing work:

* [DID Snail Method Specification](https://rhiaro.github.io/didm-snail)
* [DID Snail Method issues](https://github.com/rhiaro/didm-snail/issues/)
* [DID Snail Method implementation reports](https://rhiaro.github.io/didm-snail/implementations/)

## Disclaimer

This DID Method specification started out as satire, but it occurred to us that exercises in mapping DID related concepts to offline or non-technical scenarios might actually be a useful educational tool.

But it's a bit silly so please only invest time in reading this if you're particularly interested in finding metaphors or analogies to help people outside the space understand DIDs and related technologies, or if you really need a break from the more serious stuff.

## Introduction

Current work on DID Method specifications depends on technical solutions, much of which involves things we don't understand and can't be bothered to learn. We believe DID Methods should be inclusive, as well as resistant to the inevitable impending robot apocalypse. The SnailMail DID Method presents an alternative, for those who find communicating with old fashioned postal systems to be just fine, as well as those who just enjoy the pleasure of letter-writing.


## SnailMail Identifiers

The namestring that shall identify this DID method is: `snail`.

A DID that uses this method MUST begin with the following prefix: `did:snail`. Per the DID specification, this string MUST be in lowercase. The remainder of the DID, after the prefix, is a globally unique identifier based on an IRL address.

### Prerequisites

This DID method assumes you already have a place to live. If you don't, please consult wikipedia or legal counsel regarding your local regulations about purchasing, renting or squatting land and buildings and get somewhere to live before proceeding.

### Generating the identifier

The `snail` identifier portion is generated from your IRL address. To generate, perform the following steps:

1.  Write down the details of where you live, starting from the most general to the most specific. You SHOULD also include any country- or region-specific codes, such as postal or zip codes. The last line SHOULD be your name.
2.  Replace spaces with the `+` character.
3.  Replace line breaks with a `_` character.
4.  Append this string to `did:snail:`.

Globally unique IRL addresses are not case-sensitive, and capitalization MAY be used to help with readability.

For example, if you are the Queen of England you would use:

```
did:snail:Planet+Earth_Europe_United+Kingdom_SW1A1AA_London_Spur+Road_Buckingham+Palace_HM+The+Queen
```

To serialize a `snail` identifier into an IRL address, essentially perform the generation steps in reverse:

1.  Take the portion of the DID after `did:snail:`.
2.  Break it up into lines by replacing the `_` characters with line breaks.
3.  Replace all `+` characters with spaces.
4.  Reverse the order of the lines.

> **Note:** A quick check to see if your identifier is correctly formed is to write the serialized form on an envelope, and attach an appropriately priced stamp. You MAY put something in the envelope, but that is not necessary. Put the envelope in a postbox, and wait several days. If the envelope eventually returns to you, your globally unique IRL address is correct. If the envelope does not return, your address was malformed, or the post office lost the letter. Try again just in case.

> **Issue: Centralization of mail delivery services** Relies on a centralized mail delivery system like a national post office. Consider alternatives like passing the letter between people who know each other until it arrives at its intended destination?

> **Issue: Valid duplicate DIDs?** What if two people with the same name live at the same address?

## Operations

### Create

Once you have generated a SnailMail DID from your address, you also need a DID Document. Take your favourite kind of paper - it can be anything, blank, lined, squared, coloured, recycled, thick or thin. It is RECOMMENDED to use A4 size paper. The paper MAY be US Letter size, but really what kind of proportions is that? The paper SHOULD not be larger than A2 because this is hard to cram into sensibly sized envelopes.

Write out your DID Document according to the data model in the [[DID-SPEC]]. Include properties from the [[DID-SPEC]], and any other metadata you deem suitable. You MAY type it out and print it onto your paper, you MAY hand write it in pen or pencil or crayon, you MAY use finger painting or cut out and glue small pieces of paper. Express yourself however you like. You SHOULD NOT use glitter or food.

> **Issue: Interpretive dance** Can DID Documents be expressed in interpretive dance? Probably not because this can't be sent through the postal service. Maybe make a new DID Method for this?

You SHOULD store your DID Document somewhere, but where is out of scope. It could be in a safe, framed on the wall, in a filing cabinet, or amongst a stack of other stuff on your desk.

### Read

To resolve a `snail` DID, carry out the following steps:

1.  Serialize the DID into the IRL address format, according to the algorithm above.
2.  Write the serialized DID on an envelope.
3.  Purchase a stamp; what kind of stamp depends on the IRL region you are and the IRL region of the DID. Affix the stamp to the top right hand corner of the envelope.
4.  Write the following on a slip of paper: "Please send me your DID Document."
    *   You MAY write the message in any natural language. If you know the native language of the DID Subject, you SHOULD use that language.
    *   You MAY repeat the message using multiple natural languages.
    *   You MAY include pleasant greetings or thanks or otherwise express appreciation at the end of the message.
    *   You MUST NOT write anything mean.
5.  The paper MUST be signed. This can be with your signature, an analogue one, with a pen. You MAY alternatively or additionally fold the paper and use a wax seal.
6.  Take a second envelope. On it, write your own SnailMail DID, serialized into IRL address format according to the algorithm above. If you are able to obtain an appropriate stamp for the return envelope, you SHOULD do so and attach the stamp to the return envelope. This may not be possible due to the geographical region(s) involved however.
7.  Place the signed paper, and the stamped addressed envelope, into the first envelope, and seal.
8.  Post the envelope according to your local mail delivery service.
9.  Wait. Check your own post box every day. Look out for the stamped addressed envelope you sent out.
10.  Eventually you will receive a response from the DID Subject. The response MAY be:
    *   A photocopy of the DID Document you requested.
    *   A handwritten copy of the DID Document you requested.
    *   A polite note explaining why you're not authorized to read the DID Document you requested.
    *   A rude note explaining why you're not authorized to read the DID Document you requested.
11.  Verify the response by checking the analogue signature or seal. Does it look legit? Probably fine.

The DID Subject also has a part to play in the resolution process. Upon receipt of a polite note requesting a copy of your DID Document:

1.  You MUST verify the request has been signed. Does it look legit? Probably fine.
2.  If the request came from someone you trust to send a copy of your DID Document to, or you just don't care:
    1.  Make a copy of your DID Document. You MAY do this any way you like; write it out in crayon, photocopy it, take a polaroid, whatever is convenient. You SHOULD NOT use etch-a-sketch as the quality may degrade if it is shaken in transit.
    2.  You MUST sign the copy of your DID Document (with a pen or a wax seal). You MUST include the date the copy was made, in ISO 8601 format. You MAY include any additional metadata, polite notes or in-jokes along with the DID Document.
3.  If you don't want to send of a copy of the DID Document for whatever reason:
    1.  Write note explaining why. You MAY include HTTP status codes or memes as appropriate.
    2.  You MUST sign the note, and include an ISO 8601 date of when you wrote the note.
4.  Take the return addressed envelope that was included as part of the request, and place the copy of your DID Document or rejection note as appropriate inside.
5.  If the envelope was not stamped by the sender, affix an appropriate stamp according to the geographical region(s) involved.
6.  Post the envelope according to your local mail delivery service.

### Update

If you wish to update your DID Document, just update it. Maybe you move house, and want to add a `forwardingAddress` property so people know your new DID. You can scribble out the parts you want to change, write it out again with changes and destroy the original, or use tippex or masking tape or any other kind of erasing technology.

If someone else tries to update your DID Document, you MAY help them, or tell them no, depending on whether you like their ideas or not.

You MUST include the updated date in ISO 8601 format, and initial or do a really small signature, beside the updates.

### Deactivate

You may wish to deactive your DID if you abandon society to live in the woods, are the victim of structural inequality which renders you homeless, or shuffle off this mortal coil. To do so:

1.  Take your paper DID Document in two hands. You MAY involve teeth, furniture, or hands of a trusted friend.
2.  Tear the DID Document into tiny pieces.
3.  You MAY additionally set the pieces on fire or scatter them to the winds.

> **Issue: Paper shredders?** Consider option to use a paper shredder for deactivation. Is using something powered by electricity unsustainable? Is a paper shredder with a hand crank okay?

## Authentication

Authentication is performed through analogue signatures. Sign your DID Document so people know it is from you. Sign your requests for DID Documents too. Sign everything. Signatures are good enough for the US banking system, they're good enough for SnailMail DIDs.

## Authorization

You are the physical holder of your DID Document, so you get to decide who is authorized to update or deactivate it. Just decide. It's up to you.

## Privacy Considerations

When you try to read a DID Document, you reveal your own DID in the process (in order to get the DID Document posted back to you). If this is a problem, consider creating a new SnailMail DID using a fake name, a PO Box, or your friend's address.

## Security Considerations

You should employ appropriate security (like lock your doors) in order to prevent your DID Document from being stolen or modified or damaged by attackers. If malicious parties also live in your house, you should take steps to prevent them from accessing it, like putting it on a high shelf or obfuscate it in a folder labelled 'taxes'.

A SnailMail DID includes personally identifiable information (your real world address). This means people can find out where you live just from your DID. This DID Method is not for you if you're worried about creeps showing up at your house. Mitigation mechanisms include building walls, moats, employing private security, or only leaving your house in disguise or through secret tunnels.

> **Issue: MITM Attacks** Is there a risk of the post being intercepted? Why do people send money and valuable goods through the post if this is a serious concern?