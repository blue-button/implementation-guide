---
layout: default
title: Blue Button Implementation Guide
---

# Content Format for Health Records

An electronic health record keeps a digital record of all clinical information. With the amount of variability in Health IT systems, it is important to have a consistent set of health information for each patient. Meaningful Use specifies the fields and content structure of clinical data that patients need to keep about themselves, as they move between provider settings.


## Technical
For Blue Button, the recommended standard for representing the patient health record is the HL7 Consolidated Clinical Document Architecture also known as the Consolidated CDA.

The Consolidated CDA is a XML-based standard that specifies the encoding, structure, and semantics of a clinical document.

There are a wide-range of templates that can be represented in the Consolidated CDA standard. For Blue Button we are outlining a subset set of sections and fields that should be used.

### Sections and Fields
Blue Button adopts the requirements for sections and fields from Meaningful Use Stage 2. When ever a patient health record is generated, it should have the following fields, if they exist in the dataholders system:

<table>
	<tr>
		<th class="table-column">Category</th>
		<th class="table-column">Data Elements</th>
	</tr>
	<tr>
		<th rowspan="1">Encounter Information</th>
		<td>Care Team Members</td>
	</tr>
	<tr class="odd">
		<th rowspan="6">Patient Information</th>
		<td>Date of Birth</td>
	</tr>
	<tr class="odd">
		<td>Ethnicity</td>
	</tr>
	<tr class="odd">
		<td>Patient Name</td>
	</tr>
	<tr class="odd">
		<td>Preferred Language</td>
	</tr>
	<tr class="odd">
		<td>Race</td>
	</tr>
	<tr class="odd">
		<td>Sex</td>
	</tr>
	<tr>
		<th rowspan="1">Care Planning</th>
		<td>Care plan field(s), including goals and instructions</td>
	</tr>
	<tr class="odd">
		<th rowspan="1">Conditions or Concerns</th>
		<td>Problems</td>
	</tr>
	<tr>
		<th rowspan="2">Medications and Immunizations</th>
		<td>Medication Allergies</td>
	</tr>
	<tr>
		<td>Medications</td>
	</tr>
	<tr class="odd">
		<th rowspan="4">Observations and Results</th>
		<td>Laboratory Tests</td>
	</tr>
	<tr class="odd">
		<td>Laboratory Values(s)/Results(s)</td>
	</tr>
	<tr class="odd">
		<td>Smoking Status</td>
	</tr>
	<tr class="odd">
		<td>Vital signs (height, weight, BP, BMI)</td>
	</tr>
	<tr>
		<th rowspan="1">Procedures</th>
		<td>Procedures</td>
	</tr>
	<tr class="odd">
		<th rowspan="5">Encounter Information</th>
		<td>Admission and Discharge Dates</td>
	</tr>
	<tr class="odd">
		<td>Admission and Discharge Location</td>
	</tr>
	<tr class="odd">
		<td>Date of Visit</td>
	</tr>
	<tr class="odd">
		<td>Provider Name and Office Contact Information</td>
	</tr>	
	<tr class="odd">
		<td>Visit Location</td>
	</tr>	
	<tr>
		<th rowspan="7">Care Planning</th>
		<td>Clinical Instructions</td>
	</tr>
	<tr>
		<td>Diagnostic Test(s) Pending</td>
	</tr>
	<tr>
		<td>Discharge Instructions</td>
	</tr>
	<tr>
		<td>Future Scheduled Appointments</td>
	</tr>	
	<tr>
		<td>Future Scheduled Test(s)</td>
	</tr>
	<tr>
		<td>Recommended Patient Decision Aids</td>
	</tr>	
	<tr>
		<td>Referrals to Other Providers</td>
	</tr>	
	<tr class="odd">
		<th rowspan="4">Conditions or Concerns</th>
		<td>Encounter Diagnoses</td>
	</tr>
	<tr class="odd">
		<td>Reason for Hospitalization</td>
	</tr>
	<tr class="odd">
		<td>Reason for Referral</td>
	</tr>
	<tr class="odd">
		<td>Reason for Visit</td>
	</tr>
	<tr>
		<th rowspan="2">Medications and Immunizations</th>
		<td>Immunizations</td>
	</tr>
	<tr>
		<td>Medications Administered during the Visit</td>
	</tr>
	<tr class="odd">
		<th rowspan="2">Observations and Results</th>
		<td>Cognitive Status</td>
	</tr>
	<tr class="odd">
		<td>Functional Status</td>
	</tr>
</table>

Link to [Companion Guide to Consolidated CDA](http://wiki.siframework.org/Companion+Guide+to+Consolidated+CDA+for+MU2).

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
