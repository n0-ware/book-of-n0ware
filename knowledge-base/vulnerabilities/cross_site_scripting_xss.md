# Cross-Site Scripting (XSS)
- Tags[^1]

[^1]: #owasp #xss #injection #webapp 
## Description
[Cross-Site Scripting](cross_site_scripting_xss.md), or *XSS*, is classified as an injection attack according to the [*OWASP Top 10 2021*](https://owasp.org/www-project-top-ten/). XSS involves *injecting* malicious JavaScript into web application with the hope that it is executed by other users. 

Achieving XSS on a target can lead to multiple outcomes, including:
- Stealing cookies for [session hijacking](session_hijacking.md)
- Running a keylogger
- Redirecting to an entirely different website
- Resetting their password
- Placing an order
- And more

## Types
There are four different types of XSS

### Document Object Model (DOM)
DOM is a programming interface for `HTML` and `XML` documents. DOM represents the page in a way that other programs can alter the document structure, style, and content. Since a web page is just a document, it can be rendered in multiple ways, most commonly either in a browser or as the `HTML` source-code. 

DOM-based XSS is where malicious JavaScript is executed directly in a users browser without the need for a new page to load or data to be submitted to backend code. This is 100% contained in the browser, and execution occurrs when the JavaScript code in the website acts on inputer or user interaction

[Example](#DOM)
## Finding

## Examples
### DOM
A websites JavaScript gets contents from the `window.locaiton.hash`

