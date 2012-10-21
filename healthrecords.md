---
layout: default
title: Blue Button Implementation Guide
---

# Content Format for Health Records

An electronic health record keeps a digital record of all clinical information. With the amount of variability in Health IT systems, it is important to have a consistent set of health information for each patient. Meaningful Use specifies the fields and content structure of clinical data that patients need to keep about themselves, as they move between provider settings.


## Technical
For Blue Button, the recommended standard for representing the patient health record is the HL7 Consolidated Clinical Document Architecure also known as the Consolidated CDA.

The Consolidated CDA is a XML-based standard that specifies the encoding, structure, and semantics of a clinical document.

There are a wide-range of templates that can be represented in the Consolidated CDA standard. For Blue Button we are outlining a subset set of sections and fields that should be used.

### Sections and Fields
Blue Button adopts the requirements for sections and fields from Meaningful Use Stage 2. When ever a patient health record is generated, it should have the following fields, if they exist in the dataholders system:

<table>
	<tr>
		<th rowspan="1">Encounter Information</th>
		<td>Care Team Members</td>
	</tr>
	<tr>
		<th rowspan="6">Patient Information</th>
		<td>Date of Birth</td>
	</tr>
	<tr>
		<td>Ethnicity</td>
	</tr>
	<tr>
		<td>Patient Name</td>
	</tr>
	<tr>
		<td>Preferred Language</td>
	</tr>
	<tr>
		<td>Race</td>
	</tr>
	<tr>
		<td>Sex</td>
	</tr>
</table>

Link to Companion Guide to Consolidated CDA.

### Human Readable Stylesheet
If a patient or other person is the main consumer of the health record, it should include a stylesheet. 

To make the CCDA XML human readable, an XSLT stylesheet should be included. This will allow a person to easily view their information on a computer or print it.

### Sample Health Records
Link to samples of MU 2 files.

### Sample Stylesheets
Link to sample stylesheet


## Commonly Asked Questions

1. What is the difference between a CCD/C32 and CCD/CCDA?

2. If I am outputting a CCD/C32, is that sufficient?
