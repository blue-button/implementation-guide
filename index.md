---
layout: default
title: Blue Button Implementation Guide
---

# Getting Started with Blue Button

Mauris vel justo et neque tincidunt fermentum volutpat eget odio. Sed ornare scelerisque neque, nec venenatis nisl pulvinar non.

- **Great Idea 1:** Proin ac cursus urna. Quisque ut aliquet ipsum. 
- **Great Idea 2:** Etiam fringilla ante eget arcu faucibus et euismod lacus hendrerit.
- **Great Idea 3:** Nulla cursus, mi sit amet placerat facilisis.

## Level Two Header

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

Example of Code:

{% highlight json %}
{
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
{% endhighlight %}  

More Code:

{% highlight json %}
{
	"patient": {    
	    "demographics": {
	        "firstName": "David",
	        "middleName": null,
	        "lastName": "Yun",
	        "age": 38,
	        "gender": "Male",
	        "bloodType": "AB",
	        "organDonor": "Yes"
	    },
	    "address": {
	        "street": "123 Anywhere Road",
	        "city": "San Francisco",
	        "state": "CA",
	        "country": "United States",
	        "zipCode": 94103
	    }
    }
}
{% endhighlight %}