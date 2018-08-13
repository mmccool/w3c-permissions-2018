# w3c-permissions-2018
Position paper for [2018 W3C Permissions and User Consent Workshop](https://www.w3.org/Privacy/permissions-ws-2018/cfp.html).
* Deadline is August 17

## Ideas
* Using FOI to identify categories of information that can be shared
* Combine with discretionary access control
* Use WoT as an example of "[consent as access control](0806-kajiwara-original-plans.txt)" concept

----

# User Consent as Access Control

This is an idea where we describe user consent information in machine-readable standardized format and use them to restrict/filter sensitive information before letting the services use these information. With a standardized description for user consent, app developers can develop privacy-aware applications by being able to parse these documents and filter their data accordingly.

## From a Web of Things perspective: describing data sharing capabilities with Field of Interest

Using the Web of Things standards, we can describe what information a device can send using the Thing Description. In addition to this, we can group multiple devices based on what they do using Field of Interest information. With these information, the user can figure out what kind of information a device or a group of devices are sending, then decide on what information can leave the device and be shared with others.

The standardized user consent data can be used to restrict information from leaving the network by filter them out at the gateway, or to tell the device explicitly not to send certain information out of the device.

## Standards of access control / policy description

There are (at least) two relevant standards in the access control domain:

* [XACML](http://xml.coverpages.org/xacml.html)
    * Describes policies in XML format, enables fine-grained attribute-based access control. 
    * Widely used, and many implementations are present, including open-source ones.
    * Drawbacks: they are too heavy-weighted and also based on Mandatory Access Control, where the administrator defines top-down rules for which resources can be accessed by whom.
* Next Generation Access Control(NGAC)
    * https://www.sbir.gov/sbirsearch/detail/1229007
    * https://www.nist.gov/publications/exploring-next-generation-access-control-methodologies
    * https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-178.pdf
    * Uses a dependency graph based model to describe which user or a class of users can access an object or a class of objects.
    * Supports Discretionary Access Control (user defines who can access their objects) efficiently compared to XACML.
    * Not many implementations are present, and lacks a standardized format for describing policies.

From my understanding, there is no standardized/widely-used JSON-based format that describes access control policies and support efficient discretionary access control. There are many services that have discretionary access control and perform well, so I think this combination is not impossible to achieve.
