+++
date = '2025-05-29T20:23:58+05:30'
draft = false
title = '[OWASP] Broken Object Level Authorization'
series = 'OWASP API Security'
featured_image = "/images/bola/featured.jpeg"
tags = ['OWASP']
+++

{{< series title="OWASP API Security Top 10" series="OWASP API Security" >}}


## 1. Introduction
In the present world, Application Programming Interface (API) stands out to be one of the most critical aspects. APIs are responsible for our daily activities like checking weather on our smart phone, buying a product from an E-commerce store or accessing our data on cloud storage and many more. However such technology also comes with its own risks. One of which is Broken object level authorization(BOLA).

This vulnerability is recognized as Top security threat in [OWASP API Security Top 10](https://owasp.org/API-Security/editions/2023/en/0x11-t10/) , which has ability to compromise many systems if ignored. In this blog let us see how it works and how it can be mitigated


### 1-1. Authentication VS Authorization
<img src="/images/bola/2.jpeg" alt="example" width="600">

Before moving to actual workings of BOLA, let's first point out a common misconception. Many people think Authentication is same as Authorization, but in reality both cover different concepts.

Authorization maybe defined as "the process of verifying that a requested action or service is approved for a specific entity" [(NIST)](https://csrc.nist.gov/glossary/term/authorization). Where as Authentication is a process of verifying an entity's identity. A user who is authenticated (perhaps by username and password) is not often authorized to access every resource and perform every action possible on the system. For example, a web app will contain both normal users and admins. Usually the actions performed by admins are not privileged to normal users even though they are authenticated, and also authentication is not always required to access data, like unauthenticated users can have access to public data, a login page, or a whole web page

## 2. BOLA Workings
<img src="/images/bola/1.png" alt="example" width="600">

BOLA is a specific type of [insecure direct object reference (IDOR)](https://pengw0in.github.io/lohithsrikar/) , occurs when an API fails to check whether a user is authorized  to access specific object like : JSON file, image file, a document or a resource, based on identifiers like `user_id`, `account_id`, sequential integers, UUIDs, or generic strings.

> *Just because a user is authenticated doesn't mean that the user authorized to access any object.*

This vulnerability allows attackers to simply send API requests by altering object identifiers and gain access to sensitive data

### 2-1 Attack Scenarios
- Consider a University website which uses an API developed by university itself, which provides information about current students in that university. By inspecting browser requests , an attacker can identify a API end point like `example_uni/Photo_id/rollno` which returns student Photo based on identifier `rollno`. If attacker gains access to roll numbers of students, with a simple script, the attacker can access to photos of thousands of students.

- An automobile manufacturer has enabled remote control of its vehicles via a mobile API for communication with the driver's mobile phone. The API enables the driver to remotely start and stop the engine and lock and unlock the doors. As part of this flow, the user sends the Vehicle Identification Number (VIN) to the API. The API fails to validate that the VIN represents a vehicle that belongs to the logged in user, which leads to a BOLA vulnerability. An attacker can access vehicles that don't belong to him [source](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/#:~:text=An%20automobile%20manufacturer,belong%20to%20him.).


## 3. Real-World BOLA Breaches
- **Uber(2016):** In October 2016, Uber experienced a data security incident that resulted in breach of information related to riders and driver accounts [source](https://help.uber.com/en/riders/article/information-about-2016-data-security-incident?nodeId=12c1e9d1-4042-4231-a3ec-3605779b8815).
- **Facebook (2018):** A BOLA flaw allowed attackers to exploit access tokens, leading to the unauthorized access of millions of user accoun [source](https://www.theguardian.com/news/2018/mar/17/cambridge-analytica-facebook-influence-us-election).
- **Parler (2021):** Researchers exploited BOLA vulnerabilities to download unprotected media files by incrementing object IDs, bypassing access controls without authentication [source](https://www.wired.com/story/parler-hack-data-public-posts-images-video/).

These cases highlight how simple oversights in authorization mechanisms can lead to massive data breaches.

## 4.  How to prevent
- Implement a proper authorization mechanism that relies on the user policies and hierarchy.
- Use the authorization mechanism to check if the logged-in user has access to perform the requested action on the record in every function that uses an input from the client to access a record in the database.
- Prefer the use of random and unpredictable values as GUIDs for records' IDs.
- Write tests to evaluate the vulnerability of the authorization mechanism. Do not deploy changes that make the tests fail.

## 5. References 
- [API1:2023 Broken Object Level Authorization](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/)
- [Medium Post by Babu Tripathy](https://medium.com/@bubu.tripathy/broken-object-level-authorization-bola-the-silent-threat-in-api-security-2fe5f57b21b2)
- [Blog by Dr. Katie Paxton-Fear](https://www.traceable.ai/owasp-api/broken-object-level-authorization)

---
*Last edit: 30-05-2025*