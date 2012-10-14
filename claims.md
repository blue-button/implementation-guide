---
layout: default
title: Content Format for Medical Claims
---

# Content Format for Medical Claims

Two sentences on claims data. Claims standard to be specified.

## Workflow

Refer to Download, Transmit Using Direct, and Transmit Using Email.

## Technical 

What are the requirements for medical claims?
How do we describe the format?

Example:

{% highlight json %}
{
   "patient":{
      "name":"Ellen Lu",
      "patientIdentifier":"W1234123456"
   },
   "insurance":{
      "name":"Name of Insurance",
      "payerID":123456,
      "payerIDType":"National Payer ID",
      "policyName":"Name of Policy",
      "policyInformation":123456,
      "memberID":"W1234123456",
      "memberName":"Name of Plan Member",
      "planName":"Name of Plan"
   },
   "claims":[
      {
         "claim":"0210336239290",
         "type":"PartB",
         "provider":{
            "name":"Inova Health Services",
            "providerID":123456789,
            "providerIDType":"National Provider ID"
         },
         "date":{
            "lowValue":20101102,
            "highValue":20101102
         },
         "charges":{
            "priceBilled":1022.50,
            "negotiatedPrice":782.33,
            "insurancePaid":625.86,
            "patientResponsibility":156.47
         },
         "service":{
            "name":"Name of Service Provided",
            "codeSystemName":"CPT",
            "codeSystem":"2.16.840.1.113883.6.96",
            "code":28521
         },
         "diagnosis":[
            {
               "name":"Name of Condition",
               "codeSystemName":"CPT",
               "codeSystem":"2.16.840.1.113883.6.96",
               "code":28521
            },
            {
               "name":"Name of Condition",
               "codeSystemName":"CPT",
               "codeSystem":"2.16.840.1.113883.6.96",
               "code":5854
            }
         ]
      }
   ]
}
{% endhighlight %}

## Security & Privacy

Section not needed.