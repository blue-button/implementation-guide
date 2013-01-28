---
layout: default
title: Enabling the Download of Health Data
---

# Enabling the Download of Health Data

This section describes how a consumer can ***download*** a copy of their record from a portal.

![Download](images/download.png)

## Workflow

As part of the View, Download, and Transmit requirements in Meaningful Use Stage 2, a patient must be able to download a copy of their health record. A high-level flow of this is:

1. A patient (or their authorized representative) logs into the Patient Portal using previously-validated credentials
2. Within the portal experience, there is access to functionality that allows them to download a copy of their health record
3. The download happens over a secure connection such as HTTPS

The workflow in this section is meant to be illustrative, not prescriptive.


## Content

The patient needs to be able to download a package that is human-readable and machine-readable.

### Required for MU 2
The required content for ***download*** will be the [***Clinical Summary***](healthrecords.html), which is the entire patient's health history. The content format shall use the [Consolidated CDA w. Meaningful Use Stage 2 Sections and Fields](healthrecords.html) and have a MIME type of application/xml.

If the data holder has not yet implemented Meaningful Use  Stage 2 certified electronic health record technology (CEHRT), they may alternatively use the data elements and format required by Meaningful Use Stage 1 for a Continuity of Care Document / C32.

To ensure human-readability, make sure the patient can download a stylesheet along with the Consolidated CDA. The file type is application/xslt.

### Human-Readable Options
There are other human-readable options such as PDF or TXT. It will be up to electronic health record companies to decide how they can make this data more accessible for patients.