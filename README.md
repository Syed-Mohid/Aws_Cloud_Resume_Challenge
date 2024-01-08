
# Cloud Resume Challenge Powered by AWS

The Cloud Resume Challenge is a hands-on project designed to help you bridge the gap from cloud certification to cloud job. It incorporates many of the skills that real cloud and DevOps engineers use in their daily work. 

It allows Certified Profesionals to showcase their learnings and demonstrate the knowledge they have gained through certification.

Here is my attempt at the Cloud Resume Challenge and a breif discription of a small problem I faced and how i solved it .


## Architecture

![Architecture Diagram]()![Architecture Diagram](/website/assets/images/Arch.png)

## Certification

A certification for the Cloud resume challenge is the first step on it. This orients the developer to AWS services that can facilitate them in their Cloud Journey and help them complete the Challenge. Here is my Certification below

[AWS Certified Cloud Practioner]( https://www.credly.com/badges/ca536060-8c52-46ac-903a-26baa9fa8f08/public_url )


## Front-End Dev & Static Website 

The Resume is written in HTML and has been styled by utiling CSS. After the website is designed it is stored in an S3 Bucket and can be viewed as an Amazon S3 Static Website.

## HTTPS & DNS

The S3 Website URL should utilize HTTPS for security. Cloudfront is utilized to help with this. Route 53 is utilize to register a domain name for the website and Cloudfront distribution is used to point the website to the custom DNS domain name.
## JavaScript and Database

JS is utilized to include a vistor count that displays total number of people that have accesed the website.The visitor counter will need to retrieve and update its count in a database somewhere. Amazon’s DynamoDB is utilized for this.
## API , Python and IaC

An API that accepts requests from your web app and communicates with the database is utilized. In this case the Access to this API is generated through AWS lambda and Functional URL where every function has a URL to call it. 

Python is utilized to set up the lambda function. AWS SAM is utilized to deploy the lambda function using the AWS SAM CLI. This is called “infrastructure as code” or IaC.
## CI/CD

By utilizing github Actions CI/CD is setup such that when the code or changes are pushed to the repository they immediately update the contents of the S3 Bucket ( front end ) or the python code ( back end ) that includes the SAM applications.


## Problem Faced

The challenge was overall very informative and there are tons of guides to follow them and do it in your desired way. An Issue I faced was with Cloudfront.

Cloudfront is designed in such a way that cloudfront Caches your objects. CloudFront caching, allows more objects to be served from CloudFront edge locations, which are closer to your users. This helps Content reach your users quicker and without any delay.

A Cloudfront is a CDN which stands for Content delivery network and it is used in netflix to have users quick access to movies and tvshows.

In my case my website would be cached at said edge locations and would update after almost over a day. I would make a particular change and not be able to see it immediately since it had been cached at an edge location close to me. 

Therefore in order to see changes immedidately I utlized the cloudfronts ability to invalidate certain objects. That means that Cloudfront will omit these objects and not have them cached at the edge location. Utilizing this concept i was able to Update my Cloudfront almost immediately after comitting to my repo and pushing the contents on to my S3 Bucket.
