---
layout: default
title: Achieving MU 2 VDT Requirement with Blue Button
published: true
---

# V/D/T and Blue Button+

As a dataholder, by implementing Blue Button+ Direct, you will be meeting the requirements of View, Download, and Transmit (V/D/T) in Meaningful Use Stage 2.

Blue Button+ Direct specifications ask data holders to meet V/D/T requirements, and offers guidance for a few minor clarifications and additions to V/D/T that ensure patients can easily transmit their records to third party applications of their choice.

###Patient engagement.

	(1) View, download, and transmit to 3rd party. (i) EHR technology must provide patients (and their authorized representatives) with an online means to view, download, and transmit to a 3rd party the data specified below. Access to these capabilities must be through a secure channel that ensures all content is encrypted and integrity-protected in accordance with the standard for encryption and hashing algorithms specified at §170.210(f).

(A) View. 

	Electronically view in accordance with the standard adopted at §170.204(a), at a minimum, the following data:

	(1) The Common MU Data Set (which should be in their English (i.e., non-coded) representation if they associate with a vocabulary/code set).

	(2) Ambulatory setting only. Provider's name and office contact information.

	(3) Inpatient setting only. Admission and discharge dates and locations; discharge instructions; and reason(s) for hospitalization.

(B) Download. 

	(1) Electronically download an ambulatory summary or inpatient summary (as applicable to the EHR technology setting for which certification is requested) in human readable format or formatted according to the standard adopted at §170.205(a)(3) that includes, at a minimum, the following data (which, for the human readable version, should be in their English representation if they associate with a vocabulary/code set):(i) Ambulatory setting only. All of the data specified in paragraph (e)(1)(i)(A)(1) and (2) of this section.(ii) Inpatient setting only. All of the data specified in paragraphs (e)(1)(i)(A)(1) and (3) of this section.
	
    (2) Inpatient setting only. Electronically download transition of care/referral summaries that were created as a result of a transition of care (pursuant to the capability expressed in the certification criterion adopted at paragraph (b)(2) of this section).
    
(C) Transmit to third party. 

	(1) Electronically transmit the ambulatory summary or inpatient summary (as applicable to the EHR technology setting for which certification is requested) created in paragraph (e)(1)(i)(B)(1) of this section in accordance with the standard specified in §170.202(a).
    
	(2) Inpatient setting only. Electronically transmit transition of care/referral summaries (as a result of a transition of care/referral) selected by the patient (or their authorized representative) in accordance with the standard specified in §170.202(a).

Learn more about Meaningful Use at <a href="http://www.healthit.gov/policy-researchers-implementers/meaningful-use-stage-2" target="_blank">HealthIT.gov</a>. And view the final ONC rule <a href="http://www.gpo.gov/fdsys/pkg/FR-2012-09-04/pdf/2012-20982.pdf" target="_blank">here</a>.

<table>
	<tr>
		<th class="table-column">Requirements</th>
		<th class="table-column">Specified in MU 2 VDT</th>
		<th class="table-column">Specified for Blue Button+</th>
	</tr>
	<tr>
		<th>Content</th>
		<td><a href="healthrecords.html">Consolidated CDA</a></td>
		<td><a href="healthrecords.html">Consolidated CDA</a></td>
	</tr>
	<tr class="odd">
		<th>Section &amp; Fields</th>
		<td><a href="healthrecords.html">Sections and fields described in MU 2</a></td>
		<td><a href="healthrecords.html">Sections and fields described in MU 2</a></td>
	</tr>
	<tr>
		<th>Transmit</th>
		<td><a href="transmit-using-direct.html">Direct Protocol (SMIME/SMTP)</a></td>
		<td><a href="transmit-using-direct.html">Direct Protocol (SMIME/SMTP)</a></td>
	</tr>
	<tr class="odd">
		<th>Trust Anchors</th>
		<td>Manual Anchor Exchange</td>
		<td><a href="https://secure.bluebuttontrust.org" target="_blank">Blue Button Trust Bundle</a></td>
	</tr>
	<tr class="odd">
		<th>Certificate Discovery</th>
		<td>Via DNS or LDAP</td>
		<td>Via DNS or LDAP</td>
	</tr>
	<tr>
		<th>Transmit Context</th>
		<td>-</td>
		<td>In message body and optional Request.txt</td>
	</tr>	
    <tr class="odd">
		<th>View</th>
		<td><a href="http://www.gpo.gov/fdsys/pkg/FR-2012-09-04/pdf/2012-20982.pdf#page=128" target="_blank">Yes</a></td>
		<td>Yes</td>
	</tr>
	<tr>
		<th>Download</th>
		<td><a href="http://www.gpo.gov/fdsys/pkg/FR-2012-09-04/pdf/2012-20982.pdf#page=128" target="_blank">Yes</a></td>
		<td>Yes</td>
	</tr>
	<tr class="odd">
		<th>Transmit: Send Once</th>
		<td>Yes</td>
		<td>Yes</td>
	</tr>
	<tr>
		<th>Transmit: Send on Change</th>
		<td>-</td>
		<td><a href="transmit-using-direct.html#triggers">Automation &amp; Triggers</a></td>
	</tr>
</table>

## Key Differences

### Trust Anchors: Blue Button Trust Bundle

Manually installing anchors is not a scalable way to ensure scalable exchange using Direct. The Blue Button+ community has assembled a collection of anchors of third party applications and services. This anchor bundle is at [http://secure.bluebuttontrust.org](http://secure.bluebuttontrust.org).

Members of the Blue Button+ community have updated the [.NET](http://wiki.directproject.org/CSharp+Reference+Implementation) and [Java](http://wiki.directproject.org/Java+Reference+Implementation) reference implementations of Direct to include automated bundle retrieval functionality.

So if you are using one of the Direct reference implementations, retrieving the Blue Button Trust Bundle is as simple as updating a configuration file.

Learn more in the <a href="transmit-using-direct.html#bundle">Transmit</a> section.

### Transmit Context: Message Body & Request.txt

This is a simple addition to the message body to distinguish the type of transfer that is happening. The message indicates that it is a patient mediated transfer.

There is also an optional Request.txt that can be attached.

Learn more in the <a href="transmit-using-direct.html#context">Transmit</a> section.

### Transmit: Send on Change (Automation)

Blue Button+ aims to encourage a health ecosystem of patient-centric applications. In order to do that, data needs to easily get from providers to third party applications. That is achieved using Direct.

Automation is a key component because it enables data to flow to applications seamlessly. A patient can initiate a transmit and request it to be resent whenever data is changed.

Learn more about <a href="transmit-using-direct.html#triggers">Automations and Triggers</a>.