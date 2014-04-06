---
layout: default
title: Interim Recommendations For Payer / Health Plan Content
---

# Interim Recommendations For Payer / Health Plan Content

Blue Button files from health plans are typically derived from administrative claims databases, as well as self-entered data from online Personal Health Records. Files made available to patients via Blue Button+ should be:

1.	Human-readable, and
2.	Formatted in a way that is "machine readable" for downstream (e.g. 3rd-party) applications.

The Blue Button+ file should include, as possible, interoperable data fields and elements as covered below in [Blue Button+ recommended data fields and elements](#fields). The base set of data fields and elements included should be as consistent as possible with the data represented in the [MyMedicare.gov Blue Button file](http://www.cms.gov/Research-Statistics-Data-and-Systems/Files-for-Order/NonIdentifiableDataFiles/BlueButtonInitiative.html). Additional fields were also recommended by the group and detailed below. These include fields to describe the patient, payer coverage, provider(s), and codified claims history (including medication where possible).
Several options for formatting are currently possible. Each option is described below in "Blue Button+ format options,” with the potential strengths and limitations of each choice described.

## Blue Button+ Recommended Data Fields and Elements {#fields}

This section describes the recommended data fields and elements to represent in Blue Button files.

Blue Button files from non-EMR sources typically come from administrative claims data, as well as potentially self-entered data on Personal Health Records. To the extent that data holders already have useful and meaningful health data for consumers' Blue Button files, including from administrative claims data, the following data fields and elements are recommended for inclusion.

***Payer & Coverage Information***
1.	Payer name
2.	Payer ID type (e.g. CMS National Plan ID)
3.	Payer ID code
4.	Plan ID
5.	Payer web site
6.	Eligibility period start date
7.	Eligibility period end date (if applicable)
8.	Plan Type (e.g. Medical, Pharmacy, etc.)
9.	Primary Insurance vs. Secondary

***Patient Information***
1.	Patient Name (Last, First)
2.	Patient Identifier (e.g. Member ID#)

***Provider Information*** (note: may be provided on a claims-level basis)
1.	Provider ID code (e.g. NPI)
2.	Provider Name (Last & First name or organization)
3.	Provider web site

***Claims-Level Detail***
1.	Claim-level Detail
2.	Claims ID number
3.	Date of Service
4.	"Procedure" Code Type (e.g. CPT, HCPCS, NDC Rx code, ICD-9 CM procedure)
5.	"Procedure" Code(s)
6.	"Procedure" Description(s)
7.	Diagnosis Codes (e.g. ICD-9, ICD-10)
8.	Diagnosis Description(s)

***Health Financial Amounts***
1.	Provider Charged Amount ("Amount charged")
2.	Allowed/Negotiated Amount ("Insurance approved")
3.	Paid-to-Provider Amount ("Provider paid")
4.	Patient Responsibility ("You may be billed")
5.	Deductible Amount
6.	Coinsurance Amount
7.	Copay Amount
8.	Coordination-of-Benefits (COB) Amount
9.	Adjustments
10.	Explanatory Codes

***Other Health Data Elements found in non-EMR data sources***
1.	Laboratory result data (e.g. LOINC-coded results)
2.	Wellness & Care Management Program Alerts & Invitations
3.	Security & Authentication Hashes

Further detail on data fields and elements for Blue Button+ is available on [http://wiki.siframework.org/ABBI+Payor+Content+Interim+Guidance](http://wiki.siframework.org/ABBI+Payor+Content+Interim+Guidance).

## Blue Button+ Format Options:

This section describes the recommended format options for Blue Button files. Note: multiple options can be offered simultaneously.

1. ***ASCII Plain Text Format:*** the Blue Button file should ideally start with representing data fields currently shown in the [MyMedicare.gov Blue Button file](http://www.cms.gov/Research-Statistics-Data-and-Systems/Files-for-Order/NonIdentifiableDataFiles/BlueButtonInitiative.html). The actual visual layout may differ, however, and plans are encouraged to provide public sample files and details of data fields supported if alternate structures are provided, for developer and trading partner use. Special note: the My HealtheVet Blue Button file from the Department of Veterans Affairs presents clinical data in another format. It was originally derived from clinical data rather than payer-based data, does not contain codified data, and is therefore not recommended for interoperability purposes (but rather human-readability, basic Blue Button "non-plus" purposes).

2. ***CDA-formatted XML:*** for plans seeking to give consumers a file that can interoperate with clinical systems, Consolidated CDA (C-CDA) XML files should be offered, ideally in a Continuity of Care Document template (CCD). At present there is no formal HL7 implementation guide; however, several interim options and mappings are presented below, along with sample disclaimer text for consumers to understand the limitations of claims data relative to point-of-care clinical data. C-CDA files should be validated against NIST tools as well as semantic validators (e.g. [C-CDA Scorecard](http://ccda-scorecard.smartplatforms.org/).

3. ***"Lightweight" XML or JSON and HL7 Fast Healthcare Interoperability Resources (FHIR):*** for plans seeking interoperability with mobile applications and RESTful APIs, FHIR-style XML and/or JSON documents may be offered. The FHIR specification, and its patient, coverage, provider, and claims resources offer a promising way to approach this. This is a standard currently under development and not due to emerge until 2013-2014, because of the limitations of CDA in representing personal health financial data, it provides a method to express Explanation of Benefit (EOB) type of data in a structured and open fashion. (See also a simplified XML and JSON representation, below.)

No currently-existing standard is ideal for all of the available data, nor all the use cases, particularly to represent personal health financial data (EOB content). A new standard common format is most likely needed in order for payers to represent EOB-like data for consumer applications (as opposed to payer-provider transactions). Future implementation guidance should be updated with a (EOB-like) claims-derived consumer data standard as soon as possible.

Blue Button+ Simplified XML and JSON: As a starting point for future standards-development processes, or for organizations who wish to innovate ahead of the standards development process, an example open Blue Button+ simplified XML and JSON representation of MyMedicare.gov data elements is provided for reference and potential interim application. For example, organizations seeking to develop mobile application ecosystems may wish to consider this format. [See sample XML representation](https://github.com/blue-button/claims/blob/master/claims.xml). [See sample JSON representation](https://github.com/blue-button/claims/blob/master/claims.json).

Additional proprietary or closed data exchange formats and platforms also exist for health plan data interoperability with consumer-facing applications, including consumer health financial data, but are not detailed here. These were explored and discussed by the sub-workgroup, and include Microsoft Healthvault, Dossia, and Intuit/Optum Open Medical Exchange Platform.

Further detail on formats for Blue Button+ is available on [http://wiki.siframework.org/ABBI+Payor+Content+Interim+Guidance](http://wiki.siframework.org/ABBI+Payor+Content+Interim+Guidance).


## Security Considerations:

HL7 CDA security issues have come to light in certain implementations.  Maliciously-crafted documents can lead to vulnerabilities and exploits in the HTML portions of the CDA document, particularly if using the C-CDA display using HL7 style sheets.  See important post from Dr. Joshua Mandel from Harvard for more detail:
[http://smartplatforms.org/2014/04/security-vulnerabilities-in-ccda-display/](http://smartplatforms.org/2014/04/security-vulnerabilities-in-ccda-display/)

also Graham Grieve has helped summarize these issues:
1. Unsanitized nonXMLBody/text/reference/@value can execute JavaScript
2. Unsanitized table/@onmouseover can execute JavaScript
3. Unsanitized observationMedia/value/reference/@value can leak state via HTTP Referer headers

HL7 FHIR, I would suggest, may be less vulnerable to these types of attacks.  This standard not only has the feature set described in the Interim Guidance, but also several important protective features, namely that FHIR already includes native HTML, and active content is not allowed.  Other information, including Graham Grieve's post on white-listing external references and imaging, are detailed here:

[http://www.healthintersections.com.au/?p=2000](http://www.healthintersections.com.au/?p=2000)

