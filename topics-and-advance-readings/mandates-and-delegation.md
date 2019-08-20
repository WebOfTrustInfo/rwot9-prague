# Mandates and Delegation

Author: Rieks Joosten (rieks.joosten@tno.nl)

'Mandates' and 'Delegation' (and as an extension thereof perhaps also Guardianship) are important topics that need to be adequately addressed in any interoperable SSI infrastructure that supports the electronic exchange of verified (personal) data, using e.g. Verifiable Credentials (VCs). Before we can do this, we need a good understanding of **what these terms actually mean**, and more importantly perhaps: **what they are to be used for** in the context of an SSI infrastructure.

This paper aims

* to roughly explore how the terms 'mandate' and 'delegation' are being used  
* to derive a (conceptual, generic) mental model for discussing mandates and delegation, 
* to make this model useful e.g. for prototype implementations (with which to validate the model), and  standardization efforts that specify (best practices for) how to use mandates in VCs.

## Exploration

This chapter explores how the terms 'mandate' and 'delegation' are being used in a number of arbitrarily chosen contexts.  [***To be complemented by similar explorations from other countries***].

### The Dutch General Administrative Law Act

Within the Dutch government, the terms 'delegation' and 'mandate' are very well defined. Their definitions and effects can be found in the 'General Administrative Law Act' (this is the Google translation of the real source, which is [Algemene Wet Bestuursrecht](https://wetten.overheid.nl/BWBR0005537) (Awb)).

The basis for mandates is given by the statements: "*Mandate means: the authority to take decisions in the name of an administrative body*", and "*A decision taken by the mandatee within the limits of his authority counts as a decision of the mandator*", where 'mandator' is governmental body that some law has assigned the right or obligation to take decisions of some kind, and 'mandatee' is the natural or legal person (NLPerson) that the mandator has granted permission, or has ordered, to take these decisions on its behalf. 

Similarly, the basis for delegation is given by: "*Delegation is understood to mean: the transfer by a governmental body of its power to take decisions to another person who exercises this responsibility under his own responsibility*" The law does not specify terminology for the governmental body that transfers its power,  nor for the person that would subsequently exercise this responsibility. However, it does say that the body that delegates a decision can only give policy rules with regard to the exercise of delegated authority, i.e. it cannot specify precise procedures and demand that they must be followed. 

The scope of applicability of these terms is limited to that of the law that specifies them. Outside that scope we may have, and indeed we would need, different definitions. For example, we do not want to restrict 'mandate' to decision making: we want to enable mandating of any other activity as well. Similarly, we want to extend the meaning of 'delegation' to include others than just management bodies, and other activities than decision making.

In discussions to pin down the terminology and semantics for mandates and delegation, we may find further inspiration in other articles of this law. Here are just a few:

* One article says: "*A decision taken by the mandatee within the limits of his authority counts as a decision of the mandator*". This is nice within the scope of Dutch law, but how do we operationalize this 'in the wild'? 
* Another article has: "*A mandate can either be of a general nature or concern a specific case*". Do we want technological support for such kinds of statements? 
* Yet another one states: "*If the mandatee does not work under the responsibility of the mandator, the mandate requires the consent of the mandatee and, where appropriate, the person under whose responsibility he works*". How (if at all) would that translate into the more generic situations supported by SSI?
* Several articles impose all sorts of different restrictions, regarding e.g. the kinds of decisions that can be mandated, approvals needed for issuing mandates, the NLPersons that can(not) be mandated, etc. Observing that these restrictions are highly domain-specific, we might want to ponder on what we would need in an SSI infrastructure to support domain-specific mandate constraints. 

### Mandate Registers Of Dutch Governmental Bodies

On the Internet, we can find many documents of governmental bodies named 'Mandate Register' or something similar. These documents usually contain specifications of mandates, i.e. texts structures in the form of 'articles' that one may find in laws, and/or rows in 'mandate tables' that do not tell us who can do what, but rather give rules from which 'who can do what' can be inferred. Each specification usually specifies:

* an **identifier** (number, text) so as to be able to refer to the mandate specification;
* **one or more (kinds of) activities** (most often: (kinds of) decisions), the right or obligation to execute of which is being transferred by the mandate. This text may specify the actually activities and/or refer to such specifications, e.g. some (articles from a) law, (parts of) a policy, etc.
* the **mandator** (somtimes also called 'mandans') in terms of a governmental body, one or more functions (i.e. specific roles for civil servants, e.g. 'Mayor',  'Municipal Council', 'Recovery Officer', 'Finance Department'); 
* the **mandatee** (sometimes also called 'mandate holder' or 'mandataris') om terms of a governmental body, one or more functions (i.e. specific roles for civil servants, e.g. 'Mayor',  'Municipal Council', 'Recovery Officer', 'Finance Department'). Some mandate registers note that 'incidental mandates'  exist (i.e. mandates assigned for specific one or more (kinds of) activities to specific individuals), but are not administrated in the register.
* whether **submandating** is allowed, i.e. whether or not the mandatee can create a mandate for the same (kinds of) activities to other mandatees that itself, and 
* **other notes**, which may be
  * further instructions (e.g. procedures to be followed), 
  * limitations (criteria that state when the mandate can(not) be used, e.g. limiting it to some maximum amount of money that can be spent),
  * guidance (best practices), 
  * references to texts containing any of the aforementioned,, e.g. from legislation, policy or protocols

### Deriving Requirements From The Purposes That Mandates Serve
There are very many different ways in which mandates can be created, used, updated, disputed end deleted/revoked. We cannot list them all, not even in the limited scope of e.g. Dutch law.

However, one might say that mandates only matter in the following cases:

1. after an actor (a person or computer) has received a request to execute some activity, he must decide whether or not to service or deny that request. A clear, unambiguous mandate that allows the actor to infer whether or not (a) the requester is eligible to make such a request, and/or (b) the actor itself is eligible to service that request, will help it to decide this.
2. when someone needs to face consequences as a result of an action having been executed (i.e. this someone is responsible, for that execution). A clear, unambiguous mandate from which it can be inferred who is responsible for that action, will help to solve any disputes regarding who is responsible (and make that someone face the consequences).
3. ... [***more, anyone?***]

#### Ad 1.: Judging A Request For Executing an Action

ad 1.: People that find themselves in a situation like this will have informal ways of dealing with this situation, or formal ways (e.g. in regulated contexts). Formal ways usually means: legal ways, and that's a cesspit: there are many laws, by-laws, policies etc. that may all apply to a single mandate. In fact, we can find various discussions for specific cases on the Internet that all refer to different laws and regulations as they attempt to construct arguments for deciding whether or not a mandate (judicially) exists, and if so, whether or not it is valid.
One reason  for this is that real Mandates rarely seem to exist (e.g. in terms of a document that provides all clarity that we need). Rather, Mandate Registers exist that collect the activities and related laws, policies etc - sometimes even specifying more rules themselves - from which Mandates need to be inferred. This means that to decide about the existence and validity of a Mandate, arguments for deciding this are required, and there's the problem: such arguments may be disputable.

Computers that find themselves in a situation like this, however, cannot resort to informal ways for dealing with this. Also, they cannot deal with situations where the existence and validity of a Mandate needs to be inferred from laws, business policies such as mandate registers, etc. Computers require that:

* it is easy to digitally determine whether or not a mandate exists, and if so: obtain it. Much of what in the physical world is called a mandate, doesn't cut it.
* it is easy to digitally determine whether or not an obtained mandate is valid. Basically, this means that it should be attested to by the mandator, and in certain cases also by a third party that is trusted by the verifier.

#### Ad 2.: Determining The Responsibility For An Executed Action

After an action has been executed, it may need to be established who is responsible. Court cases basically establish the following facts:

1. Determine whether or not there is a mandate relationship, i.e. whether there is/are (a) mandate(s) where the actor that executed the action is a mandatee, and the party that is being held responsible is a mandator. 
2. Determine whether or not the mandate covers the executed action. This means that the action should be one as described, and the mandatee has executed it within the limits of the criteria for doing so, has followed the guidance, etc.
3. Determine whether or not the mandate is judicially valid. This means that the mandate is in accordance with applicable law, which may e.g. specify whether or not the mandator was allowed to issue such mandates (some laws may require that the mandator explicitly decides that the mandate exists, and must register this decision),  whether or not it may have been issued to that mandatee, etc.

These determinations are to be made by 'the business', i.e. people (that usually do so on behalf of the organization they work for). They are not made by computers. 

Computers, however, do need 

* access to the results of such determinations so as to digitally determine whether or not a mandate is valid and applicable to their decision whether or not to service some request (re Ad 1 above);
* to accumulate (digital) artefacts by which it can later be proved which mandate was used to service requests, which (together with other proofs, such as who the requestor was) can be used to identify the mandatee and establish that the action was executed in compliance with the constraints set by the mandate.

### What Do We Need To Create And Use Mandates?

* creation of mandate specifications
* derivation (creation/revocation) of actual mandates from mandate specifications
* creation/revocation of specific/incidental mandates

## Ideas

I (currently) suggest that a Mandate be specified to have the following attributes (and multiplicities):

* **`mandator`** [1..1]: the (single) Party (i.e. NLPerson or Organization) that has issued the mandate.
* **`actSpec`** [1..n]: the specification of the  (kinds of) action(s) for which the Mandate has been issued. A Mandate can be issued for multiple ActSpecs.
* **`mandatee`** [1..1]: the Party  that the `mandator` has ordered, or given the authority, to execute one or more actions according to the `actSpec` of the Mandate, on behalf of the `mandator` (i.e. an action that `mandatee` executes according to the `actSpec`s will count as if the `mandator` had executed it).
* **`mandateIsDelegation`** [0..1]: property of the Mandate, stating that the `actSpec`s are delegated rather than mandated, meaning that `mandatee` has been assigned the responsibility for the execution of any `actSpec`.
* **`submandatable`** [0..1]: property of the Mandate, stating that `mandator` has permitted its `mandatee` to create mandates for the collection of `actSpec`s of the Mandate, and  whose `mandatee`s are third Parties. The `mandator` remains responsible for the action that are executed by such third Parties for as long as they are within the`actSpec` specifications.
* **`warrant`** [0..n]: reference to an authoritative text (e.g. a law, a policy, or a submandatable mandate)  that justifies the existence of the mandate.
* **`startDateTime`** [1..1]: point in time at which the Mandate becomes valid.
* **`endDateTime`** [0..1]: point in time after which the Mandate is no longer valid.

I also suggest to specify Action(s) to have the following attributes:

* **`reference`** [1..n]: a bit string (text, DID, ...) that can be used to uniquely identify an `actSpec`;
* **`author`** [0..1]: the Party that controls (maintains, can update) attributes in the `actSpec`;
* **`specification`** [1..1]: text that specifies one or more specific actions and/or one or more specific kinds of actions;
* **`condition`** [0..n]: condition that a Party that executes an action must satisfy in order to be compliant with this `actSpec`;
* **`direction`** [0..n]: text that provides direction to a Party as it (wants to) execute(s) an action that is compliant with this `actSpec`;
* **`note`** [0..n]: other texts that are considered to have some relevance;
* **`IsSpecializationOf`** [0..n]: `actSpec`s whose every `condition`, `direction` and `note` is (also) applicable to this `actSpec`, unless it is inconsistent with the set of `condition`s, `direction`s and `note`s of this `actSpec`.

### Does Guardianship Link With Mandates (and if so: how)?

From the information I have (mostly rooted in legal stuff), it seems that Guardianship is in order when someone is incapable of taking sufficient care for him/herself. Examples include small children, and people with certain mental and/or physical disabilities. Under such conditions, a judge may be asked to install guardianship, which, if awarded, results in a set of obligations and the appointment of a natural person or a legal person (called the 'guardian') that will be held accountable for their realization. 

Administrative law as I have seen it is pretty much does the same thing: it states obligations and appoints governmental bodies that are accountable for their realization. Then, these bodies have mandate registers that provide the criteria to determine which individuals may (not), should (not), or must (not) do things related to these obligations. 

[***Further discussions/thoughts needed***]
