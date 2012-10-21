---
layout: default
title: Blue Button Implementation Guide
---

# Content Format for Health Records

Two sentences setting that describes the type of health record. Explain what a CCD is.

## Workflow

Refer to Download, Transmit Using Direct, and Receive Using Direct.

## Technical
For Blue Button, the recommended standard for representing the patient health record is the HL7 Consolidated Clinical Document Architecure also known as the Consolidated CDA.

The Consolidated CDA is a XML-based standard that specifies the encoding, structure, and semantics of a clinical document.

### Sections and Fields
Blue Button builds on the requirements from Meaningful Use Stage 2. When ever a patient helath record is generated, it should have the following fields, if they exist in the dataholders system:

<table>
	<tr>
		<th rowspan="1">Encounter Information</th>
		<td>Care Team Members</td>
	</tr>
	<tr>
		<th rowspan="6">Patient Information</th>
		<td>Date of Birth</td>
		<td>Ethnicity</td>
		<td>Patient Name</td>
		<td>Preferred Language</td>
		<td>Race</td>
		<td>Sex</td>
	</tr>
</table>

Consolidated CDA - Meaningful Use 2 Template

Discuss Stylesheet to make it human readable.

List the sections in MU 2 Template

Link to Companion Guide to Consolidated CDA.

Link to samples of MU 2 files.

## Privacy & Security

Section not needed.

## FAQ

1. What is the difference between a CCD/C32 and CCD/CCDA?

2. If I am outputting a CCD/C32, is that sufficient?
