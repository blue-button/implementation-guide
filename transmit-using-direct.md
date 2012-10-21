---
layout: default
title: Transmitting Data Using the Direct Protocol
---

# Transmitting Data Using the Direct Protocol

This functionality enables a dataholder, like an EMR, to send patient health information to a third party. Blue Button recommends that data should be transmitted using the Direct protocol. Direct is a means of sending health information securely from a dataholder to a recipient. For example, recipients can be other provider EMRs and third party applications for patients.

<!---
## Workflow

It is important to enable a patient to transmit their health information from the patient portal and from the provider setting.

### Patient Portal

Storyboard describing flow.

Patient Logs In. Patient clicks Share w. Direct. Patient enters Direct address. Check if always want to send. Patient clicks Share.

Ability to login and revoke access.

Handling error cases: bad address

### Provider Setting (EMR)

Storyboard describing flow.

Way 1, in-person.
Way 2, clipboard consent.

Patient provides consent to Provider. Provider uses EMR. Goes to Patient Record. Clicks add Direct Address. Enters a Direct Address. Check if always want to send. Clicks "Add & Send".

Ability to stop sending.

Handling error cases: bad address
-->

## Technical

### Handling a Patient's Request for Transmit

A patient's request for sharing their data will include authorization for transmit and the destination Direct address(es).

#### Authorization

An authorization is a patient giving a provider or patient portal permission and instructions to send them their health information via Direct. Blue Button requires systems to enable 2 types of authorizations:

1. A one-time share of health information to a Direct address
2. A continual share of health information to a Direct address when my patient record is updated

For additional guidance on "updating" see Triggers section.

#### Direct Addresses

A Direct address looks like name@direct.something.com. For field validation, it follows the form of an email address.

### Direct Protocol

Direct is a specification for how existing standards can be used to securely transport health information over the internet. Direct uses SMTP, S/MIME, and X.509 certificates to achieve security, privacy, data integrity, authentication of sender and receiver, and confirmation of delivery.

As a dataholder, you will need to send patient health information from your system to a Direct address. In order to do that, your system needs to be able to send that payload via SMTP and SMIME through a Health Information Service Provider (HISP). The functionality of a HISP can be internal to your system or hosted externally.

A HISP is a component that handles Direct message delivery and receipt. For Blue Button, a HISP must be able to:
- Send messages via SMTP
- Discover certificates via LDAP and DNS
- Encrypt using S/MIME
- Error Cases

Your system can communicate the payload and destination Direct address to a HISP via SOAP or REST.

Link to Direct Spec - IE how to build a HISP
Link to Sample Code - Head start in Java, .NET, etc...

#### Certificate Exchange
Pulls from a "trusted" White list. Must be able to pull from multiple whitelists. Must pull from whitelists at X frequency.

#### Certificate Discovery
More details on DNS and LDAP. The ability to send to any address that is given to you.

### Automation

Sending frequency. Triggers.

### Payload

- Clinical Content: Needs to be a CCDA with MU-2 sections and fields.
- Claims: 

Should be CCDA/MU-2 for health data. Should be YYY for claims data. Packaging.

## Privacy & Security

Guidance - It's okay to use publically discoverd certificates to send a Direct message initiated by the consumer. This ensures everything transmitted is encrypted. 

(The certificates do not need to be exchanged.)

A patient should be able to send their files to any Direct address.

Link to Letter/Guidance from ONC/OCR.

Best Practice / Suggestion - Show a lock. Show a signature icon too.

Under HIPAA a patient may request a provider to send their information in the form of their choosing. For Blue Button, a provider should give patients a standardize a way of requesting their information.

<!---

Temp Area
Entire Record
Package - File List, Grandma

-->