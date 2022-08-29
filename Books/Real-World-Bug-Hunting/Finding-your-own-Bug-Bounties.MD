# Finding your own Bug Bounties

<aside>
💡 This chapter guides you through a basic approach to begin hacking any application. It’s based on my experience interviewing successful hackers, reading blogs, watching videos, and actually hacking.
If you focus on learning a new skill, recognizing patterns, and testing new technologies, you can stay positive about your hacking during dry spells.
`Peter Yaworski`

</aside>

# RECONNAISSANCE

- What’s the **scope** of the program? Is it *.<example>.com or just www.<example>.com?
- How many **subdomains** does the company have?
- How many **IP addresses** does the company own?
- What type of site is it? **Software** as a **service**? **Open source**?
- Collaborative? Paid or free?
- Which **technologies** does it use? Which **programming** **language** is it coded in? Which **database** does it use? Which **frameworks** is it using?

First let’s consider you are testing for Open-scoop application like `*.example.com`

Start with the tools you can run in the background so you can do other recon while you’re waiting for the tools’ results.

# Subdomain Enumeration

<aside>
💡 The more subdomains you find, the more **attack surface** you’ll have.

</aside>

- **Tools**
    - Subfinder
    - Sublist3r
    - Amass
- **Websites**
    
    [crt.sh](http://crt.sh) Searching for Registered Certificates
    
    [censys.io](http://censys.io) Searching for Certificates Hashes
    

# Port Scanning

<aside>
💡 After you’ve enumerated subdomains, you can start port scanning to identify more **attack surfaces**, including **running services**.

</aside>

- **Tools**
    - NMAP
    - MASSCAN

Some details to note when port scanning from a list of subdomains are the IP addresses those domains are resolved to. If all but one subdomain resolves to a **common IP address range** (for example, IP addresses owned by AWS or Google Cloud Compute), it might be worthwhile to **investigate the outlier**. The different IP address might indicate a **custom-built or third-party application** that doesn’t share the same **level of security** as the company’s core applications, which
reside on the common IP address range.

# Screenshotting

<aside>
💡 This is helpful because it gives you a **visual overview** of the program’s scope.

</aside>

- **Tools**
    - `Gowitness`
    - Aquatone
- First, look for common error messages from services known to be associated with **subdomain takeovers.**
- Second, you can look for **sensitive content**.
    - For example, if all the subdomains found on `*.corp.<example>.com` return a **403** access
    denied except one subdomain, which has a login to an **unusual website**, investigate that unusual site because it might be implementing custom behavior.
- Third, look for applications that **don’t match** ones that are typical on other subdomains.
    - If there is only one **PHP application** and all the other subdomains are **Ruby on Rails**
    applications, it may be worthwhile to focus on that one PHP application because the company’s expertise seems to be in Rails.

# Content Discovery

<aside>
💡 Once you’ve reviewed subdomains, you should look for interesting content.

</aside>

- **Tools**
    - Meg
    - GOBUSTER
    - Burp Pro
- When you need to go beyond file and directory brute-forcing, **Google Dorks**.
- Another approach to finding interesting content is to check the company’s **GitHub**. You might find open source repositories from the company or helpful information about the technologies it uses.
    - **Tools**
        - GITROB
        

# Previous Bugs

<aside>
💡 One of the last steps of reconnaissance is to familiarize yourself with previous bugs. Hacker write-ups, disclosed reports, CVEs, published exploits, and so on are good resources for this.

</aside>

Having covered all the major areas of reconnaissance, it’s time to move on to testing the application. As you’re testing, keep in mind that reconnaissance is an ongoing part of finding bug bounties. It’s always a good idea to revisit a target application because it constantly
evolves.

# `TESTING THE APPLICATION`

<aside>
💡 There’s no one-size-fits-all approach to testing an application. The methodology and techniques you use depend on the type of application you’re testing, similar to the way the program scope can define your recon.

</aside>

## The Technology Stack

<aside>
💡 One of the first tasks I do when testing a new application is identify the technologies being used. This includes, but isn’t limited to, frontend JavaScript frameworks, server-side application frameworks, third-party services, locally hosted files, remote files, and so on.

</aside>

- WAPPALYZER
- I leave the default configuration for Burp Suite enabled and walk through the site to understand the functionality and note what design patterns developers have used.
- If a site is built with Rails, you might know that URLs typically follow a /CONTENT_TYPE/RECORD_ID pattern, where the RECORD_ID is an autoincremented integer.
- If an API returns JSON or XML, you might recognize that those API calls unintentionally return sensitive information that isn’t rendered on the page.
- Content formats a site expects or accepts
    - XML files come in different shapes and sizes, Keep an eye out for sites that accept .docx, .xlsx, .pptx, or other XML file types.
- Third-party tools or services that are easily misconfigured
- Encoded parameters and how an application handles them
- Custom implemented authentication mechanisms, such as OAuth flows

## Functionality Mapping

<aside>
💡 Once I understand a site’s technologies, I move on to functionality mapping.

</aside>

- For example, does the site allow you to create webhooks with URLs? ⇒ SSRF
- Does a site allow for user impersonation? ⇒ Information Disclosure
- How and where these files are rendered? ⇒ RCE ,XXS and so on.
- For example, if you’re looking for a remote code execution vulnerability, `unsanitized HTML` returned in a response body wouldn’t be of interest.

<aside>
💡 Another testing approach is to follow a checklist. Both OWASP and `Dafydd Stuttard’s` Web Application Hacker’s Handbook provide comprehensive testing checklists for reviewing an Application

</aside>

## Finding Vulnerabilities

<aside>
💡 At this stage, you might assume you should run automated scanners, like Burp’s scanning engine to look for vulnerabilities. But most programs I’ve looked at don’t permit this, it’s unnecessarily noisy, and it requires no skill or knowledge. Instead,
you should focus on manual testing.

</aside>

- I start using the site as if I were a customer.
- I usually submit payloads wherever input is accepted and look for anomalies and unexpected behavior from the site.
- I typically use the payload `000'")};--//`, which includes all the special characters that could break the context the payload is rendered in, whether that’s HTML, JavaScript, or a backend SQL query.
- Finally, if the site uses a templating engine, I’ll also add payloads `{{8*8}} [[5*5]]`
- CSRFs
    
    The types of HTTP requests that change data and whether they’re using and validating CSRF tokens or checking the referrer or origin headers
    
- IDORs
    
    Whether there are any ID parameters that can be manipulated
    
- APP Logic
    
    Opportunities to repeat requests across two separate user accounts
    
- XXEs
    
    Any XML-accepting HTTP requests
    
- Information disclosures
    
    Any content that is guaranteed to be, or should be, kept private
    
- Open Redirects
    
    Any URLs that have a redirect-related parameter
    
- XXSs
    
    Any requests that echo URL parameters in the response
    
- SQLI
    
    Whether adding a single quote, bracket, or semicolon to a parameter changes a response
    
- RCEs
    
    Any type of file upload or image manipulation
    
- Race Conditions
    
    Delayed data processing or behaviors related to
    the time of use or time of check
    
- SSRFs
    
    Functionality that accepts URLs, such as webhooks or external integrations
    
- Unpatched
    
    Disclosed server information, such as versions of PHP, Apache, Nginx, and so on, that can reveal
    outdated technology
    

<aside>
💡 As previously mentioned, hacking web applications isn’t magic. Being a bug hunter requires one-third knowledge, one-third observation, and one-third perseverance. Digging deeper into the application and thoroughly testing without wasting your time is key. Unfortunately, recognizing the difference takes experience.

</aside>

# `GOING FURTHER`

<aside>
💡 Once you’ve completed your recon and have thoroughly tested all the functionality you can find, you should research other ways to make your bug search more efficient.

</aside>

- **Automating Your Work**
- **Looking at Mobile Apps**

You can hack mobile apps in one of two ways: testing the application code directly or testing the APIs the app interacts with.

To start testing mobile app APIs, you’ll need to proxy your phone traffic as you’re using the app through Burp.

- **Identifying New Functionality**

[These aren't the access_tokens you're looking for](https://philippeharewood.com/)

His write-ups routinely reference new functionality he’s discovered and the vulnerabilities he’s found before others can because of his quick identification.

Frans Rosen shares some of his **methodology for identifying new functionality** on the Detectify

[Detectify Blog](https://blog.detectify.com/)

- **Tracking JavaScript Files**

Jobert Abma, Brett Buerhaus, and Ben Sadeghipour have discussed approaches on how
they have tracked JavaScript files; you can find their write-ups with a quick Google search of their names and the word “reconnaissance.”

### - Learning the Technology

Additionally, you can look into the technologies, libraries, and software that you know a company is using and learn how they work in detail.
