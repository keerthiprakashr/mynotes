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

## 2.1. Uses of Azure Active Directory
1. Authentication and Authorization of Users. 
    * Example: Login for mobile app, custome website, desktop app etc..

2. Service to Service A&A
    * Allowing a secure access of Azure SQL server without password from a app hosted in Azure

3. Manage access to Azure Resources
    Example : Azure Portal, Azure CLI, Powershell, APIs

4. And Many more : see the list here https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis#who-uses-azure-ad


# 3. A&A Protocols
It is important to understand the below state of the art A&A protocols. These protocols are independent of Azure AD. There are many more protocols in use, below two are good to start with.
 
Note: There are SDKs available both from Microsoft and even from open source, which implement the protocols and flows. Developers need not to implement all this ground up. These SDKs are avaialble in multiple programming langauges. Links at the end of this page.
 
* Microsoft Identity platform: https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-overview
 
In the above link you can also see a graphics which helps identity right SDKs for most common app scenarios.
 
```
a) OAuth2 and OpenIdConnect
b) SAML 2.0

```
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
  
> Read more on the types of applications from microsoft docs [here](https://docs.microsoft.com/en-us/azure/active-directory/develop/authentication-flows-app-scenarios#single-page-public-client-and-confidential-client-applications)

### 3.1.3 OAuth2&OpenIDConnect flows

Below are the different flows 
1. Authorization code Flow : Read [Specification](https://tools.ietf.org/html/rfc6749#section-4.1), [Microsoft Implementation](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)
2. Implicit Grant Flow:  Read [Specification](https://tools.ietf.org/html/rfc6749#section-4.2), [Microsoft Implementation](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-implicit-grant-flow)
3. Device code Flow : Read [Specification](https://tools.ietf.org/html/rfc8628),  [Microsoft Implementation](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code)
4. Resource Owner Flow : Read [Specification](https://tools.ietf.org/html/rfc6749#section-4.3), [Microsoft Implementation](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc)
5. Client Credential Flow : Read [Specification](https://tools.ietf.org/html/rfc6749#section-4.4), [Microsoft Implementation](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow)
6. On-behalf Flow : Read [Microsoft Implementation](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow)

## 3.2 SAML 2.0 (Security Assertion Markup Language 2.0)

The Security Assertion Markup Language (SAML), developed by the Security Services Technical Committee of [OASIS](https://www.oasis-open.org/org). SAML V2.0 is formally approved as an OASIS Standard in March 2005. Specifications can be downloaded as zip file [here](http://docs.oasis-open.org/security/saml/v2.0/saml-2.0-os.zip).

How Azure AD uses SAML 2.0 can be read [here](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-saml-protocol-reference).

# 4. Single-Sign-On(SSO)

SSO is improves user expirience by avoid to ask user to login separately in to every application of the organization.

SSO can be achieved using any of the protocols like SAML 2.0 or OpenID Connect or Integrated Windows Authentication. 

* To plan SSO deployment, refer [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/plan-sso-deployment).

* SSO Options [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/sso-options)

* To Choose a right method, refer [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/sso-options#choosing-a-single-sign-on-method)

* SSO for apps using SAML, refer [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/sso-options#saml-sso). Note: this is used in case Forms Authentication, which does not implement above two protocols.

* Integrated Windows Authentication (IWA) SSO is for an on-premise application. Refer [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/sso-options#integrated-windows-authentication-iwa-sso). 

* Password based SSO, refer [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/sso-options#password-based-sso). This is in case 

* OAuth2 and OpenIdConnect is the recomended method for new apps. Read [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/sso-options#openid-connect-and-oauth).

* For Linked sign-on, refer [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/configure-linked-sign-on).

* SSO for Market place apps, refer [here](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/one-click-sso-tutorial).

* Learn More about SSO Scenarios [here] (https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/what-is-single-sign-on)


# 5. Multi-Tenant Apps from Azure AD perspective
Multi-tenant apps are available to users in both their home tenant(AAD where app is registered) and other tenants (AADs).

Read more [here](https://docs.microsoft.com/en-us/azure/active-directory/develop/single-and-multi-tenant-apps).

# 6. Permission and Consent
Refer https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-permissions-and-consent

# 7. Azure AD Service Principle



# 8. SDKs and Quick start apps

Refer https://docs.microsoft.com/en-us/azure/active-directory/develop/msal-overview



