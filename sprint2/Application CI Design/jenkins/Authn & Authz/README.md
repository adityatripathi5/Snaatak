# Jenkins - Authentication and Authorization

## Author Details

| **Author**      | **Created on** | **Version** | **Last updated by** | **Internal Reviewer** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer** |
| --------------- | -------------- | ----------- | ------------------- | --------------------- | --------------- | --------------- | --------------- |
| Aditya Tripathi | 16-05-25       | 1           | Aditya Tripathi     | Priyansh              | Priyanka        | Rishabh         | Piyush          |

---

## Table of Contents

1. [Introduction](#introduction)
2. [Why is it Important in Jenkins?](#why-is-it-important-in-jenkins)
3. [Types of Authentication in Jenkins](#types-of-authentication-in-jenkins)
4. [Types of Authorization in Jenkins](#types-of-authorization-in-jenkins)
5. [Authentication Comparison Table](#authentication-comparison-table)
6. [Authorization Comparison Table](#authorization-comparison-table)
7. [Best Practices](#best-practices)
8. [Conclusion and Recommendation](#conclusion-and-recommendation)
9. [Contact Information](#contact-information)
10. [References](#references)

---

## Introduction

This document outlines the authentication and authorization strategy adopted for **Jenkins**, the automation engine used in our CI/CD pipelines. Jenkins supports multiple access control mechanisms, allowing teams to secure and scale operations depending on team size and enterprise requirements.

Authentication is the process of verifying a user's identity, whereas authorization determines what actions the user is allowed to perform. Together, they form the backbone of secure and compliant CI/CD pipeline management.

---

## Why is it Important in Jenkins?

* Prevent unauthorized access to builds, jobs, and credentials.
* Control permissions based on roles (developer, admin, etc.).
* Integrate with enterprise identity systems (e.g., LDAP, SSO).
* Maintain audit trails and accountability.

---

## Types of Authentication in Jenkins

1. **Jenkins’ Built-in Authentication**
   Simple user management within Jenkins UI.

2. **LDAP Authentication**
   Integrates with enterprise directory services.

3. **Single Sign-On (SSO)**
   Uses external identity providers (Okta, Azure AD) via SAML or OpenID.

4. **OAuth 2.0 Plugin**
   Supports GitHub, Google, Bitbucket for login.

5. **Unix User Database**
   Uses system-level user accounts.

---

## Types of Authorization in Jenkins

1. **Anyone can do anything**
   No access restrictions.

2. **Legacy Mode**
   Obsolete and not recommended.

3. **Logged-in users can do anything**
   Only authenticated users can act, but all have admin access.

4. **Matrix-based Security**
   Granular permission control (users/groups vs. permissions).

5. **Project-based Matrix Authorization**
   Finer control at the project level.

6. **Role-based Authorization Strategy Plugin**
   Assigns permissions to roles, which are then assigned to users/groups.

---

## Authentication Comparison Table

| Method            | Ease of Setup | Security | Enterprise Ready | External Integration | Notes                       |
| ----------------- | ------------- | -------- | ---------------- | -------------------- | --------------------------- |
| Built-in          | Easy          | Basic    | No               | N/A                  | Good for small teams        |
| LDAP              | Medium        | Strong   | Yes              | LDAP, AD             | Enterprise environments     |
| SSO (SAML/OpenID) | Complex       | Strong   | Yes              | Okta, Azure AD       | Good for centralized access |
| OAuth2 Plugin     | Easy          | Good     | Limited          | GitHub, Google       | Developer-friendly          |
| Unix User DB      | Medium        | Basic    | No               | N/A                  | System-level control        |

---

## Authorization Comparison Table

| Method                      | Ease of Use | Granularity | Recommended Use Case               |
| --------------------------- | ----------- | ----------- | ---------------------------------- |
| Anyone can do anything      | Very Easy   | None        | Test environments                  |
| Logged-in users do anything | Easy        | None        | Very small teams                   |
| Matrix-based Security       | Medium      | High        | Teams needing fine-grained control |
| Project-based Matrix        | Complex     | Very High   | Multi-team/multi-project Jenkins   |
| Role-based Strategy         | Easy        | High        | Most production setups             |

---

## Best Practices

* Always disable "Anyone can do anything".
* Use **Built-in Auth** for small setups; prefer **LDAP/SSO** in enterprises.
* Assign roles using the **Role-based Authorization Strategy** plugin.
* Periodically audit users, roles, and permissions.
* Enable logging and audit trails.
* Restrict access to sensitive credentials and scripts.
* Use credential bindings instead of hardcoding secrets.

---

## Conclusion and Recommendation

Jenkins supports various authentication and authorization methods, including external options like LDAP, SSO, or OAuth.

> In our project, we use **Built-in Authentication** for user management and the **Role-based Authorization Strategy** for assigning permissions based on responsibilities.

This method aligns well with:

* Small-to-mid-sized team size
* Simpler setup and maintenance
* Role-based access control needs

We also plan to conduct **regular audits** to ensure secure and efficient access control.

---

## Contact Information

| Name            | Email Address                                                                           |
| --------------- | --------------------------------------------------------------------------------------- |
| Aditya Tripathi | [aditya.tripathi.snaatak@mygurukulam.co](mailto:aditya.tripathi.snaatak@mygurukulam.co) |

---

## References

* [Jenkins Authentication Docs](https://www.jenkins.io/doc/book/security/authentication/)
* [Jenkins Authorization Strategies](https://www.jenkins.io/doc/book/security/authorization/)
* [Role Strategy Plugin](https://plugins.jenkins.io/role-strategy/)
* [Using SSO in Jenkins](https://plugins.jenkins.io/saml/)
* [OAuth Plugin](https://plugins.jenkins.io/oic-auth/)

---
