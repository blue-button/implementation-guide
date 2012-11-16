---
layout: default
title: Receiving Health Data Using the Direct Protocol
---

# Receiving Health Data Using the Direct Protocol

This section describes the use of the [Direct Project](http://directproject.org) specification to receive health data securely from a ***data holder***. The ability to receive health data securely enables an ecosystem to be built on patient health data.

## 1. Using the Direct Protocol to Receive Data
The Direct Protocol is a specification for how existing standards can be used to securely transport health information over the Internet. Direct uses SMTP, S/MIME, and X.509 certificates to achieve security, privacy, data integrity, authentication of sender and receiver, and confirmation of delivery.

Your application will need to communicate with a Health Information Service Provider (HISP) to accept Direct messages and their payload. A HISP is a component that handles message delivery and receipt via SMTP and S/MIME. The functionality of a HISP can be internal to your system or hosted externally.

For Blue Button, your HISP must be able to:
- ***Receive***: A message and its payload must be accepted via SMTP.
- ***Publish Encryption Certificates***: Your certificates must be discoverable via LDAP and DNS.
- ***Generate Direct Addresses***: You should provide Direct addresses for your use cases.
- ***Handle Errors***: Provide [error codes/responses](http://wiki.directproject.org/file/view/Implementation+Guide+for+Delivery+Notification+in+Direct+2012060601.pdf/343915016/Implementation%20Guide%20for%20Delivery%20Notification%20in%20Direct%202012060601.pdf) to the receiver's system

Your application will receive the payload from the HISP. It will most likely be via REST or SOAP, but this can differ from system to system.

See [Direct Protocol Documentation](http://wiki.directproject.org/Documentation+Library), [.NET Reference Implementation](http://wiki.directproject.org/CSharp+Reference+Implementation), and [Java Reference Implementation](http://wiki.directproject.org/Java+Reference+Implementation).


## 2. Receiving Data

Once your application has received the message and payload, it needs to process it. It needs to understand what files have been included. It also needs to handle cases where it receives multiple updates from the same user, over a period of time.

### A. Content and Payload

If it is a Blue Button transmission, the following should be part of the payload as a multi-part MIME:
1. Clinical Summary
2. Additional Documents
3. Request.txt

#### 1. Clinical Summary
The primary content of the transmission will be the ***Clinical Summary***, which is the entire patient's health history.

The content format should be using the [Consolidated CDA w. Meaningful Use Stage 2 Sections and Fields](healthrecords.html)

#### 2. Additional Documents
Depending on the data holder and type of encounter, you may also be receiving one of the following:
- ***Transition of Care / Referral Summary***
- ***Ambulatory Summary***
- ***Inpatient Summary***

#### 3. Request.txt
The payload should also include a ***request.txt*** file that attributes this transmission was on behalf of the patient:

{% highlight text %}
These records were sent by the provider on behalf of [Patient Name].
{% endhighlight %}

### B. Frequency
For a given address, there is the likelihood that your application will receive multiple documents over a period of time. This will be especially so, if the consumer sets up an "automated" transmission when ever their health data changes. 

This is beneficial for your application, because it will be getting an up-to-date stream of data. However, your application will need to handle the merging of these transmissions.

### C. Ensuring Validity
To ensure you are receiving from semi-trusted parties, you should verify that the message has been signed by a level 1 or better certificate. You may not want to trust self-signed certificates.

You should also consider rejecting messages to addresses not in your system.

<!--

You need to setup a HISP.
You need to make your certificate publicly accessible.
You need to register with a "whitelist" provider.
You need to then give addresses to your users.
Now when you receive messages to those addresses, you do something special with it on-behalf of your user.
Your system will know what type of file it is by doing ZZZ.

If the consumer has setup "automation", expect to receive messages continually. Your system needs to handle this case.

If you receive a message that is directed to an unknown address, reject it.

## Privacy & Security

What privacy and security guidance do we need to provide?

## FAQ

1. How do I get a certificate for my application?
2. How do I get listed in the trusted whitelist?

-->