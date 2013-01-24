---
layout: default
title: Content Format for Medical Claims
---

# Content Format for Medical Claims

There is a workgroup actively working on describing how medical claims data should be structured.

If this is an area that is relevant to you or your company, participate in the ABBI [Workgroup for Payer Content](http://wiki.siframework.org/ABBI+Payers+Workgroup).

## 1. Sections
Text describing where these sections come from. Medicare data. X12 data.

<table>
   <tr>
      <th class="table-column">Section</th>
      <th class="table-column">Description</th>
      <th class="table-column">Quick Link</th>
   </tr>
   <tr>
      <th>Payer &amp; Coverage Information</th>
      <td>...</td>
      <td><a href="#header">Jump to Section</a></td>
   </tr>
   <tr class="odd">
      <th>Patient Information</th>
      <td>...</td>
      <td><a href="#allergies">Jump to Section</a></td>
   </tr>
   <tr>
      <th>Provider Information</th>
      <td>...</td>
      <td><a href="#encouters">Jump to Section</a></td>
   </tr>
   <tr class="odd">
      <th>Claims Details</th>
      <td>...</td>
      <td><a href="#encouters">Jump to Section</a></td>
   </tr>
</table>

## 2. Breakdown of XML

### Payer & Coverage Information

<table>
   <tr>
      <th class="table-column">Field</th>
      <th class="table-column">Description</th>
      <th class="table-column">Example</th>
   </tr>
   <tr>
      <th>Payer name</th>
      <td>...</td>
      <td>Medicare</td>
   </tr>
   <tr>
      <th>Payer ID type</th>
      <td>...</td>
      <td>...</td>
   </tr>
   <tr>
      <th>Payer ID code</th>
      <td>...</td>
      <td>...</td>
   </tr>
   <tr>
      <th>Plan ID</th>
      <td>...</td>
      <td>...</td>
   </tr>
   <tr>
      <th>Payer website</th>
      <td>...</td>
      <td>...</td>
   </tr>
   <tr>
      <th>Eligibility period start date</th>
      <td>...</td>
      <td>...</td>
   </tr>
   <tr>
      <th>Eligibility period end date</th>
      <td>...</td>
      <td>...</td>
   </tr>
   <tr>
      <th>Plan Type</th>
      <td>...</td>
      <td>...</td>
   </tr>
   <tr>
      <th>Primary Insurance vs. Secondary</th>
      <td>...</td>
      <td>...</td>
   </tr>
</table>

The follow is the XML representation:

{% highlight xml %}
   <payer>
      <name>Name of Insurance</name>
      <payer_id>123456</payer_id>
      <payer_id_type>National Payer ID</payer_id_type>
      <plan_name>Name of Policy</plan_name>
      <plan_id>123456</plan_id>
      <member_id>W1234123456</member_id>
      <member_name>Name of Plan Member</member_name>
      <url>http://yourinsurer.org</url>
   </payer>
{% endhighlight %}

### Patient Information

<table>
   <tr>
      <th class="table-column">Field</th>
      <th class="table-column">Description</th>
      <th class="table-column">Example</th>
   </tr>
   <tr>
      <th>Patient Name</th>
      <td>...</td>
      <td>Ellen Harrision Lu</td>
   </tr>
   <tr>
      <th>Patient Identifier</th>
      <td>...</td>
      <td>Member ID</td>
   </tr>
</table>

The follow is the XML representation:

{% highlight xml %}
   <patient>
      <name>Ellen Harrison Lu</name>
      <patient_identifier></patient_identifier>
   </patient>
{% endhighlight %}


<!--
{% highlight xml %}
<?xml version="1.0" encoding="UTF-8" ?>
<blue_button_claims>

   <claims>
      <claim>0210336239290</claim>
      <type>Part B</type>
      <provider>
         <name>Inova Health Services</name>
         <provider_id>123456789</provider_id>
         <provider_id_type>National Provider ID</provider_id_type>
         <provider_billing_address>601 OFFICE CENTER DRIVE FORT WASHINGTON, PA 19034</provider_billing_address>
      </provider>
      <date>
         <start_date>20101102</start_date>
         <end_date>20101102</end_date>
      </date>
      <charges>
         <price_billed>1022.5</price_billed>
         <negotiated_price>782.33</negotiated_price>
         <insurance_paid>625.86</insurance_paid>
         <patient_responsibility>156.47</patient_responsibility>
      </charges>
      <service>
         <name>Name of Service Provided</name>
         <code_system_name>CPT</code_system_name>
         <code_system>2.16.840.1.113883.6.96</code_system>
         <code>28521</code>
      </service>
      <diagnoses>
         <name>Name of Condition</name>
         <code_system_name>CPT</code_system_name>
         <code_system>2.16.840.1.113883.6.96</code_system>
         <code>28521</code>
      </diagnoses>
      <diagnoses>
         <name>Name of Condition</name>
         <code_system_name>CPT</code_system_name>
         <code_system>2.16.840.1.113883.6.96</code_system>
         <code>5854</code>
      </diagnoses>
      <details>
         <start_date>20101102</start_date>
         <end_date>20101102</end_date>
         <procedure_code>A0428</procedure_code>
         <procedure_description>Description of Procedure</procedure_description>
         <modifiers>
            <description>Additional details</description>
         </modifiers>
         <quantity>1</quantity>
         <price_billed>275</price_billed>
         <negotiated_price>208.99</negotiated_price>
         <patient_responsibility>66.01</patient_responsibility>
         <place_of_service_code>41</place_of_service_code>
         <place_of_service>Ambulance - Land</place_of_service>
         <type_of_service_code>9</type_of_service_code>
         <type_of_service>Other Medical Services</type_of_service>
         <rendering_provider_number>Q335520003</rendering_provider_number>
         <rendering_provider_npi>1023062544</rendering_provider_npi>
      </details>
      <details>
         <start_date>20101102</start_date>
         <end_date>20101102</end_date>
         <procedure_code>A0428</procedure_code>
         <procedure_description>Description of Procedure</procedure_description>
         <modifiers>
            <description>Additional details</description>
         </modifiers>
         <quantity>1</quantity>
         <price_billed>275</price_billed>
         <negotiated_price>208.99</negotiated_price>
         <patient_responsibility>66.01</patient_responsibility>
         <place_of_service_code>41</place_of_service_code>
         <place_of_service>Ambulance - Land</place_of_service>
         <type_of_service_code>9</type_of_service_code>
         <type_of_service>Other Medical Services</type_of_service>
         <rendering_provider_number>Q335520003</rendering_provider_number>
         <rendering_provider_npi>1023062544</rendering_provider_npi>
      </details>
      <details>
         <start_date>20101102</start_date>
         <end_date>20101102</end_date>
         <procedure_code>A0425</procedure_code>
         <procedure_description>Description of Procedure</procedure_description>
         <modifiers>
            <description>Additional details</description>
         </modifiers>
         <quantity>44</quantity>
         <price_billed>472.5</price_billed>
         <negotiated_price>364.35</negotiated_price>
         <patient_responsibility>108.15</patient_responsibility>
         <place_of_service_code>41</place_of_service_code>
         <place_of_service>Ambulance - Land</place_of_service>
         <type_of_service_code>9</type_of_service_code>
         <type_of_service>Other Medical Services</type_of_service>
         <rendering_provider_number>Q335520003</rendering_provider_number>
         <rendering_provider_npi>1023062544</rendering_provider_npi>
      </details>
   </claims>
   <claims>
      <claim>000000123456</claim>
      <type>Part D</type>
      <pharmacy>
         <name>Costco Pharmacy</name>
         <provider_id>1234567891</provider_id>
         <provider_id_type>National Provider ID</provider_id_type>
         <provider_billing_address>601 FIRST STREET, FORT WASHINGTON, PA 19034</provider_billing_address>
      </pharmacy>
      <date>20071002</date>
      <drug>
         <name>OXISTAT</name>
         <code_system_name>RxNorm</code_system_name>
         <code>00462035860</code>
         <fill_number>0</fill_number>
         <days_supply>30</days_supply>
      </drug>
      <prescriber>
         <identifier>1111111111</identifier>
         <name>Harvey, A. McGehee</name>
      </prescriber>
   </claims>
</blue_button_claims>
 {% endhighlight %}

-->