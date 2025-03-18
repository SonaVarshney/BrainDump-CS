# Authentication

### Authentication vs Authorization
| Feature            | Authentication 🆔 | Authorization 🔑 |
|-------------------|----------------|----------------|
| **Definition** | Verifies **who** the user is. | Determines **what** the user is allowed to do. |
| **Purpose** | Confirms user identity. | Grants or restricts access to resources. |
| **Process** | Users provide credentials (e.g., username/password, biometrics, token). | System checks user permissions against access control policies. |
| **Data Used** | Username, password, OTP, biometrics, tokens, certificates. | Role-based permissions, access control lists (ACLs), policies. |
| **When It Happens** | First step in security (before authorization). | Happens **after** authentication. |
| **Example** | Logging into a website with a password. | Granting access to admin panel based on user role. |
| **Techniques** | Passwords, MFA, biometrics, social login, OAuth, OpenID Connect, SAML. | Role-Based Access Control (RBAC), Attribute-Based Access Control (ABAC), Access Control Lists (ACLs). |
| **Security Risks** | Brute force attacks, phishing, credential stuffing. | Privilege escalation, misconfigured access policies. |
| **Who Controls It?** | Verified by **identity providers (IdP)** or authentication services. | Enforced by **applications, APIs, or access management systems**. |
| **Can One Exist Without the Other?** | No, authorization needs authentication first. | Yes, authentication can exist without authorization (e.g., logging in without role-based access). |   

<br>

## Stateful vs Stateless Authentication

Authentication can be **stateful** or **stateless**, depending on how session data is managed. Understanding the difference is crucial for designing secure and scalable authentication systems.

---

### 1. Stateful Authentication  
Stateful authentication means that the server **maintains session state** for each authenticated user. It stores session-related data in memory or a database.  
A system is considered stateful if it remembers past interactions, while a stateless system does not retain any memory of past interactions.

#### How It Works  
1. User logs in and provides credentials.  
2. Server **validates credentials** and creates a session (e.g., stores a session ID in memory or a database).  
3. A **session token (e.g., session ID)** is sent to the client (usually in a cookie).  
4. For subsequent requests, the client **sends the session token** (cookie) back to the server.  
5. Server **looks up the session state** using the session ID and verifies authentication.  

#### Example Technologies  
- Traditional web apps (e.g., PHP, Django, Rails sessions)  
- Session-based authentication using server-side storage (Redis, databases)  
- Enterprise systems using centralized session stores  

#### Advantages  
- More control over sessions (force logout, revoke access).  
- Can store more session-related data (e.g., roles, permissions).  
- Supports real-time session tracking (useful for admin monitoring).  

#### Disadvantages  
- Scalability issues – Sessions need to be stored and synchronized across servers.  
- High memory usage – If too many users log in, storing session data can be expensive.  
- Load balancing complexity – Requires sticky sessions or distributed session storage (e.g., Redis).  

#### Common Use Cases  
- Banking apps (short lived session maintenance), enterprise portals  
- Internal applications with strict access control  
- Systems requiring immediate logout or session expiration  

---

### 2. Stateless Authentication  
Stateless authentication means the server **does NOT store any session state**. Instead, authentication data (e.g., user identity) is embedded in tokens (like JWT), which are verified with each request.  

#### How It Works  
1. User logs in and provides credentials.  
2. Server **validates credentials** and generates a **token (e.g., JWT)** containing user data (claims).  
3. The **token is sent to the client** (usually stored in local storage or a cookie).  
4. On each request, the client **sends the token** (e.g., in the Authorization header).  
5. Server **validates the token** (by checking the signature) but **does NOT store session state**.  

#### Example Technologies  
- JWT (JSON Web Tokens)  
- OAuth 2.0 / OpenID Connect  
- API authentication (e.g., REST, GraphQL)  
- Serverless & microservices  

#### Advantages  
- Highly scalable – No session storage required. Works well in distributed systems.  
- Works across microservices – No need for session sharing between servers.  
- Stateless API support – Ideal for RESTful APIs.  
- Better performance – No need to query databases for session validation.  

#### Disadvantages  
- Token cannot be revoked easily – Once issued, it remains valid until expiration.  
- Security risks – If a token is leaked, an attacker can use it until it expires.  
- Increased token size – JWTs contain claims (user data), making them larger than session IDs.  

#### Common Use Cases  
- Modern web & mobile apps using JWT  
- Microservices architecture (API authentication)  
- Serverless applications (Cloud Functions, AWS Lambda)  

---

### 3. Comparison: Stateful vs Stateless Authentication  

| Feature           | Stateful Authentication | Stateless Authentication |
|------------------|--------------------------|--------------------------|
| **Session Storage** | Stored on the server (DB, Redis, memory). | Not stored on the server (contained in tokens). |
| **Scalability** | Hard to scale (requires session synchronization). | Easily scalable (no session store needed). |
| **Performance** | Requires database or cache lookups. | Faster (tokens are self-contained). |
| **Session Expiry** | Server controls session expiration. | Token expires based on pre-set time. |
| **Logout Handling** | Server can invalidate session immediately. | Hard to revoke tokens before expiration. |
| **Security Risks** | Session hijacking, CSRF. | Token leakage, replay attacks. |
| **Use Cases** | Enterprise systems, banking apps. | APIs, microservices, serverless apps. |

---

### 4. Stateful vs Stateless Authentication in Real-World Systems  

| System Type | Preferred Authentication Method |
|------------|--------------------------------|
| **Web Applications** (Django, Laravel) | Stateful (Session-based) |
| **REST APIs** (Node.js, Flask) | Stateless (JWT, OAuth) |
| **Microservices Architecture** | Stateless (JWT, OAuth, API Keys) |
| **Cloud-Based Apps (AWS Lambda, Firebase)** | Stateless (JWT, OAuth) |
| **Enterprise Internal Systems** | Stateful (Session with LDAP, SAML) |

