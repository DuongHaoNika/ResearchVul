## What is authentication?

Authentication is the process of verifying the identity of a user or client.

## What is the difference between authentication and authorization?

- Authentication is the process of verifying that a user is who they claim to be. 
- Authorization involves verifying whether a user is allowed to do something.

## What is broken authentication?

Broken authentication is an umbrella term for several vulnerabilities that attackers exploit to impersonate legitimate users online

## How do authentication vulnerabilities arise?

Most vulnerabilities in authentication mechanisms occur in one of two ways:

- The authentication mechanisms are weak because they fail to adequately protect against brute-force attacks.

- Logic flaws or poor coding in the implementation allow the authentication mechanisms to be bypassed entirely by an attacker. This is sometimes called `broken authentication`.

## What is the impact of vulnerable authentication?

__Unauthorized Access to Sensitive Information__

__Impersonation of Legitimate Users__

__Escalation of Privileges__



## Vulnerabilities in password-based login

### Brute-force attacks

__Brute-forcing usernames__

__Brute-forcing passwords__

__Username enumeration__


## Vulnerabilities in other authentication mechanisms

## Vulnerabilities in OAuth

## How to prevent

__Implement Multi-Factor Authentication (MFA)__

Include a one-time password (OTP) sent via email or SMS, a biometric scan

__Enforce Strong Password Policies__

Require users to create strong passwords that include a mix of lowercase and uppercase letters, numbers, and special characters.

__Limit Failed Login Attempts__

- Implement a system that locks out user accounts after a specified number of failed login attempts (e.g., 3 or 5).
- Notify system administrators of potential brute-force attacks or suspicious login activity.

__Secure Session Management__

- Generate new, random session IDs with high entropy after each login.
- Ensure that session IDs are not exposed in URLs and are invalidated after users log out.
- Implement proper session expiration policies to prevent sessions from remaining active indefinitely.

__Secure Credential Management__



