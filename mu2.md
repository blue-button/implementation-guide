---
layout: default
title: Achieving MU 2 VDT Requirement with Blue Button
---

# V/D/T and Blue Button+

As a dataholder, by implementing Blue Button+, you will be meeting the requirements of View, Download, and Transmit (V/D/T) in Meaningful Use Stage 2.

Blue Button+ gives specific guidance to dataholders in meeting the V/D/T requirements. In doing so, it describes a few minor clarifications and additions to V/D/T that ensures patients can transmit their records to third party applications of their choice.


<table>
	<tr>
		<th class="table-column">Requirements</th>
		<th class="table-column">Specified in MU 2 VDT</th>
		<th class="table-column">Specified for Blue Button+</th>
	</tr>
	<tr>
		<th>Structure</th>
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
	<tr>
		<th>Certificate Discovery</th>
		<td>Via DNS or LDAP</td>
		<td>Via DNS or LDAP</td>
	</tr>
	<tr class="odd">
		<th>Transmit Context</th>
		<td>-</td>
		<td>In message body and optional Request.txt</td>
	</tr>	
	<tr>
		<th>Download</th>
		<td>Yes</td>
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

