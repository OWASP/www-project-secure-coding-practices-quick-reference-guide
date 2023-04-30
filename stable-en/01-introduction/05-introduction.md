---

layout: col-document
title: Secure Coding Practices
tags: SCP-QRG
document: OWASP Secure Coding Practices - Quick Reference Guide

---

{% include breadcrumb.html %}
# Introduction

This technology agnostic document defines a set of general software
security coding practices, in a checklist format, that can be integrated
into the software development lifecycle. Implementation of these
practices will mitigate most common software vulnerabilities.

Generally, it is much less expensive to build secure software than to
correct security issues after the software package has been completed,
not to mention the costs that may be associated with a security breach.

Securing critical software resources is more important than ever as the
focus of attackers has steadily moved toward the application layer. A
2009 SANS study found that attacks against web applications
constitute more than 60% of the total attack attempts observed on the
Internet.

When utilizing this guide, development teams should start by assessing
the maturity of their secure software development lifecycle and the
knowledge level of their development staff. Since this guide does not
cover the details of how to implement each coding practice, developers
will either need to have the prior knowledge or have sufficient
resources available that provide the necessary guidance. This guide
provides coding practices that can be translated into coding
requirements without the need for the developer to have an in depth
understanding of security vulnerabilities and exploits. However, other
members of the development team should have the responsibility, adequate
training, tools and resources to validate that the design and
implementation of the entire system is secure.

A glossary of important terms in this document is provided in appendix B.

Guidance on implementing a secure software development framework is
beyond the scope of this paper, however the following additional general
practices and resources are recommended:

-   Clearly define roles and responsibilities

-   Provide development teams with adequate software security training

-   Implement a secure software development lifecycle

-   Establish secure coding standards

    -   [OWASP Development Guide][guide] Project

-   Build a re-usable object library

    -   [OWASP Enterprise Security API][esapi] (ESAPI) Project

-   Verify the effectiveness of security controls

    -   [OWASP Application Security Verification Standard][asvs] (ASVS) Project

-   Establish secure outsourced development practices including defining
    security requirements and verification methodologies in both the
    request for proposal (RFP) and contract.


[asvs]: https://owasp.org/www-project-application-security-verification-standard/
[esapi]: https://owasp.org/www-project-enterprise-security-api/
[guide]: https://owasp.org/www-project-developer-guide/

\newpage
