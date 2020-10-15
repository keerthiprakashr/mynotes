# 1. Azure Active Directory: App Developer perspective

There is ovewhelming amount of infomation on avaialble on Azure Active Directory. App developers often get lost in the ocean of documents and references.

In this post I am trying to list links where Application developers can find information of what they need quickly. In this post I am focussing only from application developers point of view only!

# 2. Below are the links to few topics to understand the big picture of Azure AD

> * Introduction of Azure AD : https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis
> 
> * Terminology : https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis#terminology
> 
> * Features Of Azure Active Directory : https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis#which-features-work-in-azure-ad
> 
> * Azure AD Licenses : https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis#what-are-the-azure-ad-licenses

## 2.1. * Uses of Azure Active Directory
1. Authentication and Authorization of Users. 
    * Example: Login for mobile app, custome website, desktop app etc..

2. Service to Service A&A
    * Allowing a secure access of Azure SQL server without password from a app hosted in Azure

3. Manage access to Azure Resources
    Example : Azure Portal, Azure CLI, Powershell, APIs

4. And Many more : see the list here https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis#who-uses-azure-ad


# 3. A&A Protocols
It is important to understand the below state of the art A&A protocols. These protocols are independent of Azure AD. There are many more protocols in use, below two are good to start with.

## 3.1. OAuth2 and OpenID Connect Protocols 
 To understand OAuth2 and OpenId connect protocols one must start with understanding of below terminology and protocol flow.

### 3.1.1. Roles as defined in specifications:
* Resource owner :
      An entity capable of granting access to a protected resource.
      When the resource owner is a person, it is referred to as an
      end-user.
* Resource server : 
      The server hosting the protected resources, capable of accepting
      and responding to protected resource requests using access tokens.
* Client : 
      An application making protected resource requests on behalf of the
      resource owner and with its authorization.  The term "client" does
      not imply any particular implementation characteristics (e.g.,
      whether the application executes on a server, a desktop, or other
      devices).
* Authorization server :
      The server issuing access tokens to the client after successfully
      authenticating the resource owner and obtaining authorization.

* Security Tokens, JWTs and Claims : Please read and make it clear for yourself the what is JWT. This is independent of A&A protocols. Read about JWT [here](https://auth0.com/learn/json-web-tokens/).

* Read about HTTP Authorization header
      
>       References : 
>         * Specifications read [here](https://tools.ietf.org/html/rfc6749)
>         * Find more readable content, books and videos [here](https://oauth.net/2/)
>         * JWT read [here](https://auth0.com/learn/json-web-tokens/)

### 3.1.2. Application Types
* Based on whether the _client_ app is Web App, Mobile app, desktop app or a web api, they must be secured differently. So the protocol flow differs slightly between them. 
 
* Specification defines two types of clients based on the ability to maintain the confidentiality of client credentials(secretes). They are confidential and public clients.
 
* Based above definitation in spec, _client_ applications can be categorized as below.
>     1. Single Page App (SPA) : These are browser Javascript based apps
>     2. Public client App : Desktop, Mobile, and other devices natively without a browser.
>     3. Confidential client App : Web App backend server and Web APIs.
  
Read more on the types of applications from microsoft docs [here](https://docs.microsoft.com/en-us/azure/active-directory/develop/authentication-flows-app-scenarios#single-page-public-client-and-confidential-client-applications)
