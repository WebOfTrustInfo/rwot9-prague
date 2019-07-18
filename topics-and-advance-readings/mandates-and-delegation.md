#  Mandates and Delegation

Author: Rieks Joosten (rieks.joosten@tno.nl)

'Mandates' and 'Delegation' are important topics that need to be adequately addressed in any interoperable SSI infrastructure that supports the electronic exchange of verified (personal) data, using e.g. Verifiable Credentials (VCs). Before we can do this, we need a good understanding of what these terms actually mean, and more importantly perhaps: what they are to be used for in the context of an SSI infrastructure.

This paper aims

* to inventory uses of (use-cases for) the terms 'mandate' and 'delegation' (including any authoritative references), and from that 
* to derive a conceptual, generic (mental) model for discussing mandates and delegation, which can be used to
* to be used in standardization efforts directed at embedding mandates in VCs.

## An Inventory Inspired By Dutch Law

This section describes some of the inspiration I got from looking at Dutch law that sees upon mandates and delegation. I'm sure other countries have similar laws that differ at various points, best practices, etc., all of which we can use to derive a conceptual, generic (mental) model for discussing mandates and delegation. The final paper should collate these different sources. 

Within the Dutch government, the terms 'delegation' and 'mandate' are very well defined. The definitions and their effects can be found in the 'General Administrative Law Act' (this is the Google translation of the real source, which is [Algemene Wet Bestuursrecht](https://wetten.overheid.nl/BWBR0005537) (Awb)).

The basis for mandates is given by the statements: "*Mandate means: the authority to take decisions in the name of an administrative body*", and "*A decision taken by the mandated within the limits of his authority counts as a decision of the mandator*", where 'mandator' is governmental body that some law has assigned the right or obligation to take decisions of some kind, and 'mandated' is the natural or legal person (NLPerson) that the mandator has granted permission, or has ordered, to take these decisions on its behalf. 

Similarly, the basis for delegation is given by: "*Delegation is understood to mean: the transfer by a governmental body of its power to take decisions to another person who exercises this responsibility under his own responsibility*" The law does not specify terminology, that would be analogous to 'mandator' and 'mandated'.

Note that the meaning of these definitions is limited to the scope of applicability of the law that specifies them. Outside that scope we may have, and indeed we would need, different definitions. For example, we do not want to restrict 'mandate' to decision making: we want to enable mandating of any other activity as well. Similarly, we want to extend the meaning of 'delegation' to include others than just management bodies, and other activities than decision making.

In discussions to pin down the terminology and semantics for mandates and delegation, we may find further inspiration in other articles of this law. Here are just a few:

* One article says: "*A decision taken by the mandated within the limits of his authority counts as a decision of the mandator*". This is nice within the scope of Dutch law, but how do we operationalize this 'in the wild'? 
* Another article has: "*A mandate can either be of a general nature or concern a specific case*". Do we want technological support for such kinds of statements? 
* Yet another one states: "*If the mandated does not work under the responsibility of the mandator, the mandate requires the consent of the mandated and, where appropriate, the person under whose responsibility he works*". How (if at all) would that translate into the more generic situations supported by SSI?
* Several articles impose all sorts of different restrictions, regarding e.g. the kinds of decisions that can be mandated, approvals needed for issuing mandates, the NLPersons that can(not) be mandated, etc. Observing that these restrictions are highly domain-specific, we might want to ponder on what we would need in an SSI infrastructure to support domain-specific mandate constraints. 

On the Internet, we can find many documents of governmental bodies named 'Mandate Register' or something similar. These documents contain tables, where each row specifies a kind of decision that the applicable governmental body has a right to, or is obliged to make, to body that is mandated to take such decisions in its place, whether or not the mandated body is permitted to mandate a third body to make these decisions, and some miscellaneous guidance, which may contain restrictions that apply to the mandate, or ways in which the mandate must be executed. 

It seems that 'delegation' looks a lot like mandating. The differences seem to be:

- the body to which a decision is delegated is fully responsible (whereas with mandates, the mandator remains responsible)
- the body that delegates a decision can only give policy rules with regard to the exercise of delegated authority, i.e. it cannot specify precise procedures and demand that they must be followed. 

