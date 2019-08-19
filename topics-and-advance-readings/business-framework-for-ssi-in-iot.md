# A Business Framework for SSI in IoT

Authors: Michael Shea (The Dingle Group) & Michael Corning (Secours)

## Abstract

The IDC recently forecasted that by 2025 there will be 41 Billion connected IoT devices generating more that 79 Zettabytes of data. For all these glorious forecasts, it should be a little troubling that in 2019, there is still a consensus of opinion that the Internet of Things ecosystem continues to have significant challenges around the realms of security, data access, and control.  Conversely, within the SSI community there is a sense that SSI provides the 'silver bullet' to solve these challenges.  

What is not so clear is how.  This is not a technical problem (though there are challenges in this realm), but a business problem; in the hard reality of tight margins and production costs, it is unclear how to build a financial model that demonstrates the financial returns necessary to justify the investment and additional operating costs of adding SSI into new or existing product lines.  This paper attempts to map out a typical IoT system, identify potential SSI deployment points and develop a framework of questions that once answered will provide the information necessary to develop the business case to support the necessary investment.

## The Approach

1. Outlining current top security concerns within the IoT sector
2. Create a reference IoT system
3. Identify questions to be answered
4. Reframe reference IoT system in the context of SSI, identify SSI touch/integration points, identify area of potential cost increases/decreases, identify whether each cost is an attractor or detractor to the overall appeal of the system.
5. Summary


## Current Concerns

Even with IoT exploding across all sectors of society it is surprising that the number of large and significant security gaps continue to persist.  The following list of security concerns was created in late 2017, but unfortunately this list is still very much relevant today.

1. Secure constrained devices
2. Authorize and authenticate devices
3. Manage device updates
4. Secure communication
5. Ensure data privacy and integrity
6. Secure web, mobile, and cloud applications
7. Ensure high availability
8. Detect vulnerabilities and incidents
9. Manage vulnerabilities
10. Predict and preempt security issues

< Additional definition information on security challenges in source: https://developer.ibm.com/articles/iot-top-10-iot-security-challenges/ (viewed August 16, 2019) >

As part of this effort, the concerns that can be addressed by SSI will be identified.


## Reference System

<a href="./media/business-ssi-iot-1.png"><img src="./media/business-ssi-iot-1.png" width="800" style="margin:20px"></a>

### System Components
* SSA - Smart Smoke Alarm, this device has additional capabilities to generate alerts to external services.
* Sentinel - a small tracking device that is GPS and Bluetooth enabled.
* Bridge - an interface device for the Sentinel’s that is connected to an external hosting service.
* Wireless Router - Access point for the household to ISP

###

### User Story

John has a mother with dementia. He buys a Smart Smoke Alarm for $30 (dumb alarms cost $25, the $5 sentinel cost accrues to XYO). Both the alarm and the sentinel use the same battery, so there will be a periodic cost to replace the batteries, but they don’t have to replace two of them). John has equipped mother’s home with internet connectivity. The SSA uses WIFI to connect to the XYO Bridge John set up and placed next to the WIFI router.  All this cost John $200. WIFI connects the sentinel in the SSA to the XYO Bridge, and the XYO Bridge has registered to the XYO network to collect data from the SSA and from Mother’s sentinel.

So far, no SSI necessary.

People come and go in the home and interact with the SSA. John bought an XYO sentinel for $8 to put in mother’s purse. This sentinel in her purse will interact with the SSA and bounded-witness data from the interaction between her sentinel and the SSA are stored in the XYO ledger without cost. This data has no reference to John or mother; only to the location of the sentinel. If somebody knows the digital identity of mother’s sentinel, they can pay for a query the XYO ledger for her location. Not good.

For the moment, XYO is acting like a guardian, so if John grants a guardianship credential to mother’s sentinel…,
 
John is a Secours member, and this comes with a dementia monitoring member benefit. This benefit is like a webhook on the XYO ledger, so when the purse leaves the range of the SSA, John gets notified and pays a $5 fee for each query. After a month, John has paid for too many false positives, so he further restricts the notification threshold. [This calibration could be implemented in the guardianship credential]
 
All these devices have firmware. Today, firmware updates have minimal access controls. Vendors can push updates without the owner knowing.  This means that each of these devices has some level of user based authentication and access controls.


## Framework Questions

The below systems model below represents the attractors and detractors of opportunity regarding security and adoption of IoT.

... image goes here ...

* Map out the following system processes : 
    * 1. data flow - how does data move within/around the system?
    * 2. money flow - how are costs of the system currently dealt with, and how does revenue flow back to the vendor?
    * 3. physical flow - good or services flow through the system? 
* Map out value chain; flow of goods and services and return flow of money.
* For each IoT system where are the big commercial costs?  
* How is device identity managed?
* How does the system work with a vendor issued ID?
* How does system change when there is no vendor issued ID for the system components?
* How does the system change when the ID is self issued?
* How does the system change when there is no central ID provider?
* Who is the device controller?  
* Is the device controller also the data subject?  
* Is the data produced by the device about a human data subject?
* How are device updates managed?  Can the device be updated over the air?  Are device updates the responsibility of the user? 
* Who does the device communication with?  Other devices? Device controller? Device user?
* If usage or data consumption can be identified can the device (asset) be shared?
* By adding identity (owner, controller, user) does this change the levels of services that can be offered? 

## Reframed Reference System

To be added

## Summary

To be added
