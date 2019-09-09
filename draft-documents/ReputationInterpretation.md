Abstract
This paper explores how to take a “reputation” trust graph, with multiple characteristics and create actionable output. 
We are looking to categorize the types of reputation people might have into general buckets, such as:

* Knowledge
* Emotional Intelligence 
* Generalized Skills
* Reviews from others
The output that we would produce is specific to each type of community or decision. 
For example:
* Yes/no 
* Graph or diagram 
* Report
* Derivative reputation assessment. For example, in moving from one sport to another, some skills might be transferrable and some not. 
* Complex adjustment to the terms of engagement. For example, if you are offering a job to someone, the output might be a change in their job description. 

There are many different ways that people are collecting data and different parameters about people. We need a reputation table of some metrics. The question is what do you once you have it? We want to divide the different categories of reputation that people might have, like knowledge or skills in a particular domain, emotional intelligence, and generalized skills. What kind of outputs would you have? This is actionable output like a yes/no output or it might be something a little more like a recommendation or a report about something. It might also be an interpretation of that person's reputation in your new system or new community. How do we take a reputation that this matrix that comes from many different sources, and what does the actionable output look like?


## **Reputation Interpretation**

Authors: Arthur Brock, Kaliya Hamlin, Grace (Rebecca) Rachmany, Eric Welton

## **Abstract**

This paper explores how to take a “reputation” trust graph, with multiple characteristics and create actionable output. The paper is not focused on the automation of the process. It can be applied by human processing of information or through a programmed software implementations. It may also apply to business entities and organizations, not just persons.

We are looking to categorize the types of reputation people might have into general buckets, such as:

1. Knowledge
1. Emotional Intelligence
1. Generalized Skills
1. Reviews from others

The output that we would produce is specific to each type of community or decision.

For example:

1. Yes/no
1. Graph or diagram
1. Report
1. Derivative reputation assessment. For example, in moving from one sport to another, some skills might be transferrable and some not.
1. Complex adjustment to the terms of engagement. For example, if you are offering a job to someone, the output might be a change in their job description. 

## **Overview**

The fundamental assumption of this paper is that data collection is not the problem in creating a “reputation” for individuals, entities or groups but that the issue comes when interpreting the data. Reputation inputs are constantly collected and understood differently in different contexts. We do not address the question of “what is reputation?” nor do we address “how to create interoperable reputation standards”. Instead, the focus is on how to interpret reputation data. 

In the above (placeholder) diagram, we visualize the process we discuss in this paper. Reputation Interpretation, the box in the center, is the focus of this paper. While this paper touches on Inputs and Outputs from the interpretation process, the focus of the paper is on the process an organization would undertake to Interpret the data in a way that makes sense to that organization. In that sense, the context is decisive.

Following is the process the authors identified as the Reputation Interpretation Process. The following description also serves as a mini-glossary to the terminology used in this document. Some of the terminology may be a placeholder as these concepts have not been well-defined previous to the paper. Once running, we imagine the process itself happening in the following chronological sequence. 

**Illustration case: Throughout this discussion, we will use the case of interpreting data for mental health professionals, such as therapists or psychologists.** 

1. **Input qualification:** The Reputation Interpretation system (Bob) will have defined the input desired for the specific context and output, and sends a request to Alice for the information required. The data may come in different formats, discussed briefly below. For example, someone might ask a mental health professional for educational certifications, Myers-Briggs or other personality trait results, testimonials from clients, peer assessments, test results, etc.
1. **Margin of Error:**Alice approves a certain subset of the information Bob requested. Bob has defined a “margin of error” based on less than 100% of the data. The Margin of Error represents how close to accurate the end result is. For example, if the health professional didn’t send any testimonials, they may simply not have them or they may be hiding them, so the score needs to take this into account.
1. **Normalization** of Data Elements: Data, even data of similar types (such as ratings or reviews) comes in different formats, so some form of normalization processing needs to be performed to put the data in a format that is understandable and processable by the system. Each piece of data might inform a different element of the output. For example, if the output is a recommendation of the types of patients Alice would serve the best, specific words identified in the reviews and assessments would correspond to the section describing Alice’s specialty, for example, teenagers or recovering drug addicts.
1. **Concerns**: Once the data is normalized, the specific concerns are applied to the data. The judgements are individual for each community or system. For example, Bob may think study of Jungian psychology is an advantage or a disadvantage for the health clinic.  
1.1. **Weights** signify The importance of each element of data is (for example, peer reviews are 30% of Alice’s score).
1.1. **Credence** refers to how reliable the data is. For example, on a Myers-Brigg test result, Bob would consider the credence of the issuer and whether the test might have been gameable .
1.1. **Towards, Away and Dealbreakers.** When considering the concerns, there are things that have positive (Towards) value, such as Bob wants people with proven experience. Other characteristics are negative (Away) values, such as Bob might think that if Alice has a certification as a Reiki healer, mental health patients in his facility might think it’s less reliable. Dealbreakers are dealbreakers, for example, if Alice’s drug tests show she is a heroin addict, Bob would not allow her to treat any patients.
1. **Processing the data:** Once the data is normalized, and the concerns are accounted for, the data can be processed to provide the final output.
1. **Output:** The output of the Reputation Interpretation process is contextual and actionable. Output could be a number or yes/no answer, but in many systems it might be more complex. For example, Bob might offer Alice a job contract with customized terms of engagement, depending on the assessment of the data. 

Designing the system would be in the following order (as is the paper):

1. Define the output
1. Identify the inputs
1. Define normalization of the data
1. Define the concerns
1. Map the associations and calculations of the elements to produce the output

The remainder of the paper goes into more detail on each one of these steps.

## **Diagram of the process**

(diagram with explanations of the process with that cute matrix thing)

## **Define the Output**

Many discussions of reputation focus on numerical measures of reputation. Generally speaking, in the digital world, reputation is expressed as a kind of number, such as 5-star ratings, reputation points, credit rating, rankings, or accumulated reputation in the form of tokens. Within the digital identity community, another common form of reputation is in the form of credentials or claims. Alice may make a claim that she worked for a particular employer or holds a degree, and a yes/no verification of that claim by the institution in question indicates it is valid.

While these numbers and certificates are a convenient and accepted measures, and there has been a bias to think of reputation in these terms, numbers aren’t necessarily actionable. When Bob chooses a therapist (for himself or his clinic), just knowing that Alice has 5 star ratings isn’t enough. Perhaps Bob would want to read the experiences of other patients in long form as well, or perhaps Bob values professional peer opinions.

Likewise, there’s been a bias towards thinking of “actionable” as taking a binary decision. For example, Bob may be making a simple choice: purchase this service. However, Bob may be facing a complex choice, such as the terms of employment to offer Alice at his clinic, the workload and types of patients to assign to Alice, etc.

Following is a list of the types of outcomes discussed in the group. It is a starting list for the purposes of this paper and to allow Bobs to consider varying types of outcomes. More suggestions to this list are welcome.

Types of actionable outcomes:

1. Binary decisions (hire/no hire)
1. Categorization (placing Alice in a category, such as a professional specialty)
1. Matching recommendations (providing patients with a list of recommended therapists based on their needs)
1. Terms of engagement or update to terms of engagement (Alice attended professional training and received a number of assessments, and it is time to review and Bob would like to update her work conditions)
1. Choose from options (scheduled an interview or session, purchase a subscription, buy a book or online course Alice has published)
1. Filter (provide a list of the top candidates for a job offer)
1. Assessment (report or other long-form assessment, such as in a personality test)
1. Context-appropriate reputation (translate someone’s ranking or reputation points in one context to another context)
1. Utilization for machine learning (assessing effectiveness of different therapeutic methods on different profiles of patients)
1. Ranking
1. Disqualification 

The different types of output are appropriate for different contexts and intent. In defining the output, other areas to consider are:

1. **Intent:** What is done with the output, how long it is retained, whether this is a one-time decision or part of a larger decision.
1. **Relevant actions:** The actions that will be taken based on the output.
1. **Decision criteria:** The important factors for making decisions. This varies on the context and judgment of the community or individual making a decision. For example, Bob may consider professional assessment as extremely important.
1. **Output requirements:** The format in which the output will be presented. For example, Bob may get one report for his decision-making regarding the terms of engagement for Alice’s work contract. A patient at Bob’s clinic may receive a different presentation of the output. Some of the information about Alice may never be exposed to Bob. For example, Alice’s gender, age and race would not be exposed, although that information is in the system, in order to avoid biases.
1. **Individualization of outputs:** In some contexts, Bob may want to provide individualization of outputs. For example, IQ tests are biased towards certain racial and educational backgrounds. Bob may want to create individualized reports taking into account such biases, or individualized reports based on different educational backgrounds. For someone with a strong academic background, ongoing certifications might be less important than someone who didn’t do as much initial study.  

**Illustration case: Bob’s output will be a contract for employing Alice, as well as matching recommended clients, and a short overview that is shown on the clinic’s website and that patients review to help them choose their practitioner.** 

## **Identify Inputs**

Once the output is well-defined, it is possible to determine the inputs that can be used to reach that output. Starting with the end in mind immediately simplifies the seemingly impossible tasks of wading through the tremendous amount of information available.

This paper makes no attempt to define or categorize the types of inputs available, nor does it make any suggestions about how that input should be provided.

Following are the considerations for Bob when identifying and determining inputs.

1. **Ideal:** The ideal outcome would be perfect in every way. Bob would have all of Alice’s academic record, information on every outcome for every patient Alice had ever served, peer reviews of her work, patient reviews, etc. All of that “perfect” information would be 100% reliable and not gameable.
1. **Available:** In the real world, not all information is available. For example, Bob ideally would like to know the symptoms or complaints of each client who went to Alice, how long they were treated for, and what the outcome was. For example, Alice might have taken 3 hours to eliminate someone’s phobia, or they might have gone for 3 years and still have symptoms. While ideally, Bob would have access to this information about every patient Alice saw, in fact, none of it is generally available. Even in a future world where the patient could release that (anonymized data), some of Alice’s clients would release the information and some would not, so it would be incomplete.
1. **Cost:** Some data costs money, whether in terms of the actual purchase of the data, or in the form of difficulty of processing that data.

Following these considerations, Bob would end up with a list of the data and data sources that Bob will request from Alice. 

## **Margin of Error**

Bob now makes a request from Alice for the data, and Alice provides all or a subset of the data. Looking at the subset of data, Bob may assess the “Margin of Error”. Bob may or may not know whether Alice simply doesn’t have that data (for example, she never had a Myers-Brigg assessment performed), or whether she intentionally withheld data (for example, omitting an employer from her resume or LinkedIn profile). Based on the completeness or incompleteness of the data, Bob determines the “reliability” or “margin of error” for the final score. 

Some data may be more critical than others in determining “margin of error.” For example, if Alice is missing test results from academic institutions, Bob might consider that a minor factor for margin of error, but if she is missing actual certification from the institution, that might be a major omission that Bob considers giving a high “margin of error” because her claim to have graduated now seems dubious, putting into doubt all the rest of her self-attestations.

The authors of the paper were divided as to whether the Margin of Error would be calculated as an “overall” score on the report, or whether it would be applied individually to each item of data. The sequence of the calculation is an implementation issue. This paper points out the issue of completeness of data as one to take into consideration, and it is up to the Bobs of the world to determine where they want to implement it. 

## **Normalization**

Once data is collected, the data needs to be normalized in ways that it is understandable and can be processed. Following are considerations for normalization of data.

1. **Data may be provided in difficult-to-understand or variable formats.** For example, ratings might use a numerical 1-5 scale or a 1-10 scale (odd scales have a middle option and even scales do not), a thumbsup-thumbsdown rating, or a multifaceted rating (professionalism, effectiveness, friendliness, good-for-families, etc.) A system collecting professional assessments or reviews may need to normalize the data so it’s provided on a similar scale.
1. **Data may be gameable**. The system itself may have vulnerabilities, people may be able to put in false reviews, hack the system, be biased for certain behaviors, etc.
1. **User control:** Some institutions will provide uncensored data. For example a university transcript includes all grades for all courses, and Alice cannot edit out anything. In LinkedIn, when someone provides a recommendation, Alice can approve or decline, or request a change to the review. This is not “gaming” the system, just the fact that each system offers different levels of control by the user.
1. **Trustworthiness** (reputation in the non-formal sense of the word) of the issuer: A grade from a trade school may be worth more or less to Bob based on the institution’s reputation, how much Bob values applied learning versus academic learning, etc.
1. **Biases on the type of data:** For example, review systems tend to be biased towards excellent and horrible reviews, because of human bias. If people have an okay or neutral response, they tend not to provide any review. By definition, human reviews tend towards the extreme.

The above are top-level concerns for unpacking the data. Furthermore, data may be multidimensional. For example, records from Alice’s graduate studies might include grades, peer reviews, student reviews, number of publications, letters of recommendation, awards, etc.

Part of the normalization process is attributing the different characteristics to the appropriate part of the outcome. For example, if Alice worked for a particularly prestigious institution that would affect the salary offered and that institution’s name would be mentioned in the website blurb.

(Diagram of puzzle pieces)_

## **Concerns**

 Once data from different sources has been normalized, presumably what Bob now has is some format that allows similar types of data to be processed together in groups. For example, peer reviews would be normalized as positive, neutral, or negative. Text that will be scanned for keywords indicating specialties will be normalized into categories separating client reviews from peer reviews from employer recommendations.

Two types of concerns were identified:

1. **Importance:** Bob will use weighting mechanisms to determine the importance of the elements in determining output. For example, patient reviews may be an important part of what potential clients see, taking up 50% of that report, but in providing the contract of employment, Bob may give them no weight, and just have a threshold, for example, hire Alice if she has more than 80% positive reviews.
1. **Credence:** Each data source (or aggregated data element) has a level of credence for that particular value. The credence is an assessment of how likely it is that the data is believable. The believability of the data can be influenced by anything from the issuer through the hackability of the connection when the data was provided. Each element can be weighted according to its credence.

## **Processing**

Bob’s on his own here. Maybe he’ll attend RWoT10 and add this part.

## **Conclusions** 
