# IDOR
How to mitigate IDOR  
# What is IDORS ?
**IDOR** stands for **"Insecure Direct Object Reference"**. It is a type of security vulnerability that occurs in web applications when an attacker can access or manipulate objects or resources directly, bypassing the application's authorization and authentication mechanisms. In other words, an attacker can access data or perform actions they are not supposed to by manipulating input parameters, such as URLs, form fields, or cookies, to reference internal objects or resources.
# Proof of Concept 


# 
Article from Hackerone <a href="https://www.hackerone.com/company-news/rise-idor"> IDOR </a>

# What are the implications of an IDOR vulnerability? 

Perhaps the most infamous IDOR vulnerability as of late is that found in alt-tech social media platform Parler. The company ordered their posts by number in the URL, a telltale sign of IDOR. If you add a sequential digit to a Parler post URL, you could access the next post on the platform indefinitely. Without authentication or access limits, an attacker could easily build a program to download every post, photo, video, and data from the entire site. While this was just public posts (not necessarily IDs used to verify accounts), geolocation data from posts was also downloaded, which could reveal GPS coordinates of users' homes.  

# How can you prevent IDORs from cropping up?

“Avoiding IDOR is only possible by building a robust access control mechanism, choosing the best fit methodology for your scenario, log all access and if possible do an audit with a post authorization check,” said HackerOne hacker Manoel Abreu Netto, better known online as @manoelt. “However, if you want to reduce the impact of an IDOR, avoid using a simple pattern to reference objects in the backend, thus not using a sequential integer value but something like uuid or even a MAC (hashed ID) with a salt per user session. This does not eliminate the IDOR, but reduces the overall impact and the ability to enumerate objects.”

# To remediate IDOR vulnerabilities, below are a few best practices. 

* Developers should avoid displaying private object references such as keys or file names.
* Validation of parameters should be properly implemented.
* Verification of all the referenced objects should be checked.
* Tokens should be generated in such a way that it can only be mapped to the user and is not public.
* Ensure that queries are scoped to the owner of the resource. 
* Avoid things like using UUIDs (Universally unique identifier) over Sequential IDs as UUIDs often let IDOR vulnerabilities go undetected.
