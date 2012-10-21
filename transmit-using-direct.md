---
layout: default
title: Transmitting Data Using the Direct Protocol
---

# Transmitting Data Using the Direct Protocol

This functionality enables a dataholder, like an EMR, to send patient health information to a third party. Blue Button recommends that data should be transmitted using the Direct protocol. Direct is a means of sending health information securely from a dataholder to a recipient. For example, recipients can be other provider EMRs and third party applications for patients.

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

## Technical

### Authorization for Transmitting

Blue Button recommends a dataholder's system to be able to handle 2 types of transmits: (1) an authorization to send once and (2) an authorization to send when ever my patient record is updated. See Triggers section to learn more.

### Payload

- Clinical Content: Needs to be a CCDA with MU-2 sections and fields.
- Claims: 

Should be CCDA/MU-2 for health data. Should be YYY for claims data.

### Direct Protocol

Direct is not a new protocol, but rather, a specification for how existing standards can be used to securely transport health information over the internet. Direct uses SMTP, S/MIME, and X.509 certificates to achieve security, privacy, data integrity, authentication of sender and receiver, and confirmation of delivery.

The Direct Protocol is used to send health data securely from Point A to Point B.

Description of Direct Protocol

Image outlining how it works.

Technical image outlining how it works.

Certificate Exchange
Pointers to "Trusted" Whitelist.
Must be able to refer to multiple whitelists.
Must pull from whitelists at X frequency.

Certificate Discovery - Using DNS and LDAP
Link to more detailed spec.

Links to Sample Code

Links to Direct Spec

### Automation

Sending frequency. Triggers.

## Privacy & Security

Guidance - It's okay to use publically discoverd certificates to send a Direct message initiated by the consumer. This ensures everything transmitted is encrypted. 

(The certificates do not need to be exchanged.)

A patient should be able to send their files to any Direct address.

Link to Letter/Guidance from ONC/OCR.

Best Practice / Suggestion - Show a lock. Show a signature icon too.

Under HIPAA a patient may request a provider to send their information in the form of their choosing. For Blue Button, a provider should give patients a standardize a way of requesting their information.

This authorization can be one of two types: a one time send of information or a permanent authorizations of sending when things change.

the patient the option of receiving their data once or always.


Temp Area
Entire Record
Package - File List, Grandma