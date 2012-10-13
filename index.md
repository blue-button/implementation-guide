---
layout: default
title: Blue Button Implementation Guide
---

# Section Title

Using Skeleton for Responsive Layout

- **A Responsive Grid Down To Mobile:** Elegant scaling from a browser to tablets to mobile.
- **Fast to Start:** It's a tool for rapid development with best practices
- **Style Agnostic:** It provides the most basic, beautiful styles, but is meant to be overwritten.

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