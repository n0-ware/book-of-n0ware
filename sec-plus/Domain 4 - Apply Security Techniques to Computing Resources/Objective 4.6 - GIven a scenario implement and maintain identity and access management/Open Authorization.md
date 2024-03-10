---
tags: 
topic: sec_iam
subTopic: oauth
source: CompTIA
family: sec_fundamentals
imageNameKey: SecPlus_oauth
cert: Sec+
---
# Open Authorization - OAuth
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

OAuth is a protocol designed for facilitating the secure sharing of information (resources) between sites and applications, especially in RESTful API-based systems. Unlike SOAP, OAuth is a more flexible architectural framework, making it suitable for various implementations, including mobile apps.

## Key Components

- **Identity Provider (IdP)**: The user creates a password-protected account at an IdP, which hosts their user profile.
- **OAuth Consumer Site**: An application or consumer site that wants access to the user's account without requiring the user's password.
- **Resource Server (API Server)**: Hosts functions that allow OAuth clients to access user attributes and resources.
- **Authorization Server**: Processes authorization requests, manages user consent, and issues access tokens.
- **Client**: Represents an app or consumer site that seeks authorization to access user resources.

## OAuth Workflow

1. **Client Registration**: The client app or service registers with the authorization server, providing a redirect URL, client ID (public), and a confidential client secret.
2. **User Approval**: The user approves the client's authorization request, granting it access to specific parts of their account.
3. **Access Token**: Depending on the chosen grant type (flow), the client receives an access token from the authorization server.
4. **Accessing Resources**: The client presents the access token to the resource server (API server) when requesting user resources.
5. **JWT Format**: OAuth uses JSON Web Tokens (JWT) for claims data, which can be passed in URLs and HTTP headers, providing authentication and integrity through digital signatures.

OAuth is widely adopted for securing APIs and enabling secure access to user data without exposing passwords to client applications. It offers versatility in different usage scenarios, making it suitable for a variety of authentication and authorization needs.
