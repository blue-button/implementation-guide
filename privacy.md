---
layout: default
title: Best Practices for Transmitting Data
---

# Privacy and Security

These are Blue Button privacy and security related questions that came from the ABBI workgroup.

## Background
We are working on a new implementation guide for the Blue Button, which will encourage dataholders (health care providers and health plans) to provide patients (“individuals”) an electronic copy of their health data in a machine-readable format in accordance with privacy and security best practices.  

Blue Button functionality provides data that is formatted in a consolidated continuity of care document (consolidated CCD).  A consolidated CCD contains a subset of protected health information (PHI) maintained in an individual’s medical records and therefore is a subset of a designated record set. Accordingly, under the HIPAA Privacy Rule, the individual who is the subject of the PHI has a right of access to the PHI in the consolidated CCD. (We recognize that individuals continue to have the right to request and receive all their PHI in the medical records outside of the consolidated CCD or Blue Button function.)  For ease of reference, we will call the PHI in a consolidated CCD “Blue Button health information” in our Use Cases and Questions and Answers  below.

DIRECT is a set of technical specifications that allow providers and individuals to securely transmit PHI electronically. It is similar to e-mail, in that providers and patients each have “DIRECT addresses” that allow them to communicate with each other, but is more secure than regular e-mail.  For example, a John Q. Public could have a Direct address (JohnQPublic@direct.healthvault.com). Meaningful Use Stage 2 requires every certified Electronic Health Record system to be able to send messages to DIRECT addresses.

## Use cases
1. While interacting in person with his HIPAA-covered health care provider’s office the individual gives the provider either the individual’s e-mail address or a Direct address and requests the provider to electronically transmit the individual’s Blue Button health information to this e-mail or Direct address.
2. The individual has established an account with the portal of his HIPAA-covered health care provider and through that portal requests that the individual’s Blue Button health information be transmitted to the individual’s e-mail or Direct address.

## Preliminary Questions and Answers

***1. What are HIPAA’s general requirements for verifying the individual’s identity when the individual requests that the health care provider furnish an electronic copy of the individual’s Blue Button health information?***

The Privacy Rule requires covered entities (including health care providers) to verify the identity and authority of a person requesting protected health information (PHI), if the identity or authority of the person is not already known to the provider.  See 45 C.F.R. 164.514(h)(1).  These verification requirements apply to individuals who request access to their PHI that is maintained in a designated record set, including PHI maintained by or for a covered entity that is available through the Blue Button function (Blue Button health information).  The Privacy Rule does not include specific or technical verification requirements, largely allowing a covered entity’s professional judgment and industry standards to determine what is reasonable and appropriate under the circumstances. 
In addition to the Privacy Rule’s verification requirements, where electronic access is being provided by or on behalf of a covered entity, the HIPAA Security Rule requires administrative safeguards be in place to authorize only appropriate persons to have access to the electronic protected health information (e-PHI) and technical safeguards be implemented to verify that a person seeking access to e-PHI is the one claimed. See 45 C.F.R. §§ 164.308(a)(4)(i) (information access management standard) and 164.312(d)) (person or entity authentication standard).

***a.	What if the individual makes his or her request in person to have the health care provider electronically transmit the individual’s Blue Button health information to an e-mail or Direct address?***

If the individual is not known to the covered entity, the covered entity (including a health care provider) is required to verify the identity of the individual requesting access before authorizing the access.  Verification may be obtained either orally, or in writing.  If the covered entity already knows the identity of the individual, it is not required to take additional steps to verify the individual’s identity.  
	  
***b.	What if the individual’s identity was previously verified for purposes of establishing a web portal account with the health care provider and the individual requests their Blue Button health information from the provider through that portal?***

Once the individual’s identity has been verified and the individual authorized to obtain electronic access to PHI through the web portal, the Security Rule also requires that a covered entity (including a health care provider) implement technical safeguards for verifying that when the individual seeks access through the portal, he or she is the one claimed (45 CFR 164.312(d)(1)).  For example, a web portal could require the individual to enter a user name and password to access the individual’s health information.  
 
***2.	May a health care provider require individuals to submit in writing their requests that their Blue Button health information be transmitted to them?***

Yes. The Privacy Rule allows covered entities (including health care providers) to require individuals to make requests for access in writing, provided that they inform the individual of such a requirement.  See 45 C.F.R. § 164.524(b)(1).  In addition, electronic documents qualify as written documents under the Privacy Rule.  Thus, the Privacy Rule equally supports covered entities’ providing individuals with a means to request access to their Blue Button health information in paper (e.g., a note or a form) or through electronic means (e.g., e-mail, web portal). 

As a practical matter, requiring that such requests be in writing may reduce errors and may serve as the covered entity’s record of the e-mail or Direct address to which the individual requested their information be sent.

***3.	If an individual requests a machine-readable consolidated CCD and the health care provider is able to readily furnish a copy in that format, must the provider furnish the copy of the CCD in this requested format?***

Yes. The Privacy Rule requires covered entities (including health care providers) to provide access to the PHI in the form or format requested by the individual if it is readily producible in such form or format. See 45 C.F.R. § 164.524(c)(2).

***4.	What are the implications for breach notification if a health care provider transmits Blue Button health information to an individual in accordance with the Direct exchange specifications, which require encrypting with at least one algorithm endorsed by FIPS 140-2?***

PHI in transit that has been rendered unusable, unreadable or indecipherable in compliance with encryption processes that are Federal Information Processing Standards (FIPS) 140-2 validated meets the safe harbor provision of the Breach Notification Rule so long as the confidential process or key that might enable decryption has not been breached. See Federal Register, volume 74, page 42742 (August 24, 2009).  This means that information that is transmitted in accordance with the Direct exchange specifications (where the decryption key or process has not been breached) would be considered to meet the safe harbor provision of the Breach Notification Rule.

***5.	If an individual requests that a provider transmit their Blue Button health information via unencrypted e-mail, may the provider do so?***

In e-mailing PHI to individuals, covered entities (including health care providers) are required to comply with the HIPAA Security Rule, which, among other requirements, requires implementation of technical security measures to guard against unauthorized access to e-PHI  that is being transmitted over an electronic communications network.  See  45 CFR 164.312(e).   The Security Rule requires encryption when transmitting e- PHI where it is reasonable and appropriate to encrypt the information, and in general, encryption is a reasonable and appropriate measure to safeguard the e-PHI in e-mail transmissions.  However, there may be instances where an individual may not want to receive his or her e-PHI  encrypted.  In these cases, covered entities are permitted to send e-PHI to individuals through unencrypted e-mails if they have advised the individual of the risk, and after doing so, the individual still requests that his or her e-PHI be sent through unencrypted e-mail.  


***a.	May a provider require written documentation that an individual has requested his or her Blue Button health information be sent via unencrypted e-mail, despite being advised of the risks of sending sensitive information through an unsecured transmission?  For example, may a provider require an individual to sign a written request for access that includes provisions that 1) specify that the individual has requested to receive PHI via unencrypted e-mail versus in a more secure manner, 2) set out the potential security risks of sending unencrypted e-mail, and 3) state that the individual understands the risks and still wishes to receive PHI via unencrypted e-mail?***

Yes.  Covered entities (including health care providers) are permitted to require that individuals make access requests in writing, which may include documentation of an individual’s wish to receive his or her e-PHI via unencrypted e-mail even though the individual has been advised of the risks.  

***6.	Is a provider responsible for the security of Blue Button health information under the HIPAA Rules once it has been received by the individual?***

A covered entity is not responsible for safeguarding e-PHI once it has been delivered to the destination designated by the individual. 


***Not in use case, but requested.***

***Does an individual have a right of access to claims and other payment information about the individual maintained by a health plan?***

An individual’s right of access  applies to the PHI that is maintained in a covered entity’s designated record set(s).  With respect to health plans, a designated record set includes the health plan’s enrollment, payment, claims adjudication, and case or medical management record systems, as well as any records used in whole or in part by or for the health plan to make decisions about the individual.  A record is any item, collection, or grouping of information that includes PHI that is maintained, collected, used or disseminated by or for the covered entity.  See 45 C.F.R. 164.501 (definition of “designated record set”).
