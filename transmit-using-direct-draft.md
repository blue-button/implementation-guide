---
layout: default
title: Transmitting Data Using the Direct Protocol
---

# Transmitting Data Using the Direct Protocol

This section describes the use of the [Direct Project](http://directproject.org) specification to transmit health data securely from a ***data holder*** to a ***third party***.

![Transmit Diagram](images/transmit.png)

Examples of data holder systems include: provider's EHR, health insurance claims database, or pharmacy dispensing system. Examples of third parties include: personal health records, mobile applications, or web services.

## 1. Technical

### A. Authentication
A patient's identity must be validated before a transmission of his/her data can occur. In the case of a patient portal, a patient or their authorized representative is authenticated by logging in using previously-validated credentials. In the case of a live interaction with the patient or their authorized representative, the provider is responsible for "in-person" identity validation.

These requirements are the same identity assurance and authentication requirements sufficient for access to the View and Download portions of View, Download, and Transmit in Meaningful Use Stage 2. 

### B. Handling a Patient's Request for Transmit

A patient's request for sharing their data will include:

1. Authorization for transmit
2. Frequency preferences
3. Destination Direct address(es) 

A system must be able to receive these 3 pieces of information from a patient before transmitting their information. These pieces of information may be received via a patient portal or via a provider interface. The patient must also have the ability to revoke a transmit request.

#### 1. Authorization 
Patient access to his or her own health information is a right under the HIPAA Privacy Rule. However, the provider may reasonably wish to ensure that the patient understands and accepts the resulting action and risks inherent in transmit.

The system should display consent messaging, including all necessary legal language, to the patient or to the provider on the patient's behalf. The user should be able to accept or reject the language. For auditing purposes, that response should be recorded.


#### 2. Frequency Preferences

A system must allow the user to set and change at least two options for transmit frequency:

1. Send a single one-time push of health information to the supplied Direct address(es)
2. Continually push health information to the supplied Direct address(es) when the patient record is updated (See [Triggers](#triggers))

Other frequencies are permitted and can be provided by the implementer.

#### 3. Direct Addresses

A system must be able to accept one or more Direct Addresses. A Direct address may look like ellen.ross@somephr.org or jack.smith@direct.someapp.com. 

- For field validation, a Direct address follows the form of an email address.
- For certificate validation, all legitimate addresses will have corresponding public certificates discoverable via DNS or LDAP. (See [Certificate Discovery](https://docs.google.com/document/d/1igDpIizm7CTfV-fUw_1EnrCUGIljFEgLPRHpgK5iaec/edit))

### C. Revoking Transmit Request

Patients may not revoke authorization retrospectively, but must be able to revoke authorization prospectively. There must be a mechanism in the provider interface and patient portal to enable the user to terminate all future transmissions.

### D. Transmitting Using the Direct Protocol

The [Direct Protocol](http://wiki.directproject.org/Documentation+Library) is a specification for how existing standards can be used to securely transport health information over the internet. Direct uses SMTP, S/MIME, and X.509 certificates to achieve security, privacy, data integrity, authentication of sender and receiver, and confirmation of delivery.

As a dataholder, you will need to send patient health information from your system to a Direct address. In order to do that, your system needs to be able to send that payload through a Security/Trust Agent (STA). A STA uses SMTP and S/MIME to ensure messages and their payload are delivered securely. A STA can be a component internal to your system, or hosted externally. 

When an STA is hosted externally, it is usually by a Health Information Services Provider (HISP). 

For Blue Button, a STA must be able to:
- ***Send***: A message and its payload must be sent via SMTP
- ***Encrypt***: Messages will be encrypted using S/MIME
- ***Use Encryption Certificates***: A STA must [discover certificates via DNS or LDAP](https://docs.google.com/document/d/1igDpIizm7CTfV-fUw_1EnrCUGIljFEgLPRHpgK5iaec/edit) to encrypt messages
- ***Validate Certificates***: Certificates must be valid [Direct Address or Organizationally Bound Certificates](http://wiki.directproject.org/Applicability%2BStatement%2Bfor%2BSecure%2BHealth%2BTransport%2BWorking%2BVersion%23x4.0%20Trust%20Verification-4.1%20Verification%20of%20Certificate-Entity%20Binding)
- ***Trust Anchor Bundle***: A STA should automatically retrieve the latest Blue Button trust bundle
- ***Sign Messages w. EV Certificate***: Outbound message should also be signed by an Extended Validation (EV) certificate
- ***Handle Errors***: Provide [error codes/responses](http://wiki.directproject.org/file/view/Implementation+Guide+for+Delivery+Notification+in+Direct+2012060601.pdf/343915016/Implementation%20Guide%20for%20Delivery%20Notification%20in%20Direct%202012060601.pdf) to the data holder's system

Your system will communicate the payload and destination Direct address to a STA/HISP. It will most likely be via REST or SOAP, but this can differ from system to system.

See [Direct Protocol Documentation](http://wiki.directproject.org/Documentation+Library), [.NET Reference Implementation](http://wiki.directproject.org/CSharp+Reference+Implementation), and [Java Reference Implementation](http://wiki.directproject.org/Java+Reference+Implementation).

#### Retrieving Blue Button Trust Bundle
Your STA/HISP will need a set of trust anchors in order to transmit Direct messages. This bundle includes the trust anchors from third party applications in the Blue Button ecosystem. The certificate bundle can be retrieved from:


{% highlight text %}
https://secure.bluebuttontrust.org
{% endhighlight %}

The bundle format is ***PKCS7*** which has a ***.p7b*** extension. The bundle should be retrieved and loaded into the STA/HISP daily.

#### Signing with a Certificate
Your STA/HISP will need to sign messages before they are transmitted. Messages can be signed by multiple certificates. A set of trust communities like [Direct Trust](http://directtrust.org) will establish their trust bundles and you will be able to sign messages with those certificates. If you are not participating in one of those communities, then one of the signing certificates must be an extended validation (EV) certificate from a reputable vendor.

Between Jan - June 2013, if you are just performing trials and demonstrations, you have the option of submitting your anchor to the ***Providers-Test*** [Blue Button Trust Bundle](https://secure.bluebuttontrust.org/).

#### Detailed Flow Diagram
The following diagram depicts a successful transmission. See it [full-size](files/patient-transmit.pdf).

![Direct Transmit Flow Diagram](images/direct-transmit.png)


### E. Automation and Triggers {#triggers}

When the patient has requested "ongoing" sharing of information, the data holder's system will have to use internal triggers that will cause new information to be sent. How this is done will differ from system to system, but we suggest the following as a starting point:

***Clinical Systems***:
- Discharge or transition to a new care setting (Acute/ER/Inpatient)
- End of encounter (Ambulatory)
- Any time significant new information is received (e.g., new image or lab report)

***Payer Systems***:
- New adjudicated claims data is available
- New explanation of benefits is available

Other triggers are permitted and encouraged. It is up to the implementer. Systems that are unable to implement triggers should investigate transmitting records at predetermined time intervals.

### F. Payload

When a transmission occurs, the following should be part of the payload as a multi-part MIME:
1. Clinical Summary
2. Additional Documents
3. Transmit Context
4. Request.txt

#### 1. Clinical Summary
The primary content of the transmission will be the [***Clinical Summary***](healthrecords.html), which is the entire patient's health history.

The content format shall use the [Consolidated CDA w. Meaningful Use Stage 2 Sections and Fields](healthrecords.html) and have a MIME type of application/xml. If the data holder has not yet adopted MU Stage 2, they may alternatively use the data elements and format required by MU Stage 1 for a Continuity of Care Document / C32.

#### 2. Additional Documents
Depending on the trigger or type of encounter, it may also be appropriate to include one of the following:
- ***Transition of Care / Referral Summary***
- ***Ambulatory Summary***
- ***Inpatient Summary***

The payload may include other documents as well.

#### 3. Transmit Context
The message body should also include attribution that this transmission was on behalf of the patient in text/plain or text/html:

{% highlight text %}
This message was sent by [Data Holder Name] at the request of [Patient Name].
{% endhighlight %}

An example of what that body text would look like:

{% highlight text %}
This message was sent by Ashby Medical Center at the request of Ellen Ross.
{% endhighlight %}

#### 4. Request.txt
In addition to the friendly message in the body, you should include a ***request.txt***. This is a simple way, much like [robots.txt](http://www.robotstxt.org/robotstxt.html) works to provide some semi-structured context to machines.

{% highlight text %}
Destination: [Direct Address]
Patient: [Patient Name]
Data-holder: [Data Holder Name]
Recurring: [Yes / No]
{% endhighlight %}

An example of what a request.txt would look like:

{% highlight text %}
Destination: ellen.ross@somephr.org
Patient: Ellen Ross
Data-holder: Ashby Medical Center
Recurring: Yes
{% endhighlight %}

### G. Workflow

Storyboards have been drafted to match the key user flows described above: (1) within the patient portal and (2) within the provider's EHR interface.

![Patient Portal](images/transmit-workflow-1.jpg)

![Patient Portal - Revoke](images/transmit-workflow-2.jpg)

![Provider Interface](images/transmit-workflow-3.jpg)

![Provider Interface - Revoke](images/transmit-workflow-4.jpg)