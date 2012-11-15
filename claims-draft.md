---
layout: default
title: Content Format for Medical Claims
---

# Content Format for Medical Claims

There is a workgroup actively working on describing how medical claims data should be structured.

If this is an area that is relevant to you or your company, participate in the ABBI [Workgroup for Payer Content](http://wiki.siframework.org/ABBI+Payers+Workgroup).

## Draft of Claims Format

It includes both Part B and Part D.

{% highlight json %}
{
   "patient":{
      "name":"Ellen Lu",
      "patient_identifier":"W1234123456"
   },
   "insurance":{
      "name":"Name of Insurance",
      "payer_id":123456,
      "payer_id_type":"National Payer ID",
      "policy_name":"Name of Policy",
      "policy_information":123456,
      "member_id":"W1234123456",
      "member_name":"Name of Plan Member",
      "plan_name":"Name of Plan"
   },
   "claims":[
      {
         "claim":"0210336239290",
         "type":"Part B",
         "provider":{
            "name":"Inova Health Services",
            "provider_id":123456789,
            "provider_id_type":"National Provider ID",
            "provider_billing_address":"601 OFFICE CENTER DRIVE FORT WASHINGTON, PA 19034"
         },
         "date":{
            "start_date":20101102,
            "end_date":20101102
         },
         "charges":{
            "price_billed":1022.50,
            "negotiated_price":782.33,
            "insurance_paid":625.86,
            "patient_responsibility":156.47
         },
         "service":{
            "name":"Name of Service Provided",
            "code_system_name":"CPT",
            "code_system":"2.16.840.1.113883.6.96",
            "code":28521
         },
         "diagnoses":[
            {
               "name":"Name of Condition",
               "code_system_name":"CPT",
               "code_system":"2.16.840.1.113883.6.96",
               "code":28521
            },
            {
               "name":"Name of Condition",
               "code_system_name":"CPT",
               "code_system":"2.16.840.1.113883.6.96",
               "code":5854
            }
         ],
         "lines":[
            {
               "start_date":20101102,
               "end_date":20101102,
               "procedure_code":"A0428",
               "procedure_description":"Description of Procedure",
               "modifiers":[
                  {
                     "description":"Additional details"
                  }
               ],
               "quantity":1,
               "price_billed":275.00,
               "negotiated_price":208.99,
               "patient_responsibility":66.01,
               "place_of_service_code":41,
               "place_of_service:":"Ambulance - Land",
               "type_of_service_code":9,
               "type_of_service":"Other Medical Services",
               "rendering_provider_number":"Q335520003",
               "rendering_provider_npi":1023062544
            },
            {
               "start_date":20101102,
               "end_date":20101102,
               "procedure_code":"A0428",
               "procedure_description":"Description of Procedure",
               "modifiers":[
                  {
                     "description":"Additional details"
                  }
               ],
               "quantity":1,
               "price_billed":275.00,
               "negotiated_price":208.99,
               "patient_responsibility":66.01,
               "place_of_service_code":41,
               "place_of_service:":"Ambulance - Land",
               "type_of_service_code":9,
               "type_of_service":"Other Medical Services",
               "rendering_provider_number":"Q335520003",
               "rendering_provider_npi":1023062544
            },
            {
               "start_date":20101102,
               "end_date":20101102,
               "procedure_code":"A0425",
               "procedure_description":"Description of Procedure",
               "modifiers":[
                  {
                     "description":"Additional details"
                  }
               ],
               "quantity":44,
               "price_billed":472.50,
               "negotiated_price":364.35,
               "patient_responsibility":108.15,
               "place_of_service_code":41,
               "place_of_service:":"Ambulance - Land",
               "type_of_service_code":9,
               "type_of_service":"Other Medical Services",
               "rendering_provider_number":"Q335520003",
               "rendering_provider_npi":1023062544
            }
         ]
      },
      {
         "claim":"000000123456",
         "type":"Part D",
         "pharmacy":{
            "name":"Costco Pharmacy",
            "provider_id":1234567891,
            "provider_id_type":"National Provider ID",
            "provider_billing_address":"601 FIRST STREET, FORT WASHINGTON, PA 19034"
         },
         "date":20071002,
         "drug":{
            "name":"OXISTAT",
            "code_system_name":"RxNorm",
            "code":"00462035860",
            "fill_number":0,
            "days_supply":30
         },
         "prescriber":{
            "identifier":1111111111,
            "name":"Harvey, A. McGehee"
         }
      }
   ]
}
{% endhighlight %}