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



