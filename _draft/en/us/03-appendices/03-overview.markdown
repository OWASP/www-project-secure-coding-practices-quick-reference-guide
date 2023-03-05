---

layout: col-document
title: Secure Coding Practices - Draft
tags: SCPQRG

---

{% include breadcrumb.html %}
\newpage
# Appendix A: Software Security and Risk Principles Overview {#software-security-and-risk-principles-overview .list-paragraph}

Building secure software requires a basic understanding of security
principles. While a comprehensive review of security principles is
beyond the scope of this guide, a quick overview is provided.

The goal of software security is to maintain the
*[confidentiality](#Confidentiality), [integrity](#Integrity)*, and
[*availability*](#Availability) of information resources in order to
enable successful business operations. This goal is accomplished through
the implementation of [*security controls*](#Security_Controls). This
guide focuses on the technical controls specific to
[*mitigating*](#Mitigate) the occurrence of common software
[*vulnerabilities*](#Vulnerability). While the primary focus is web
applications and their supporting infrastructure, most of the guidance
can be applied to any software deployment platform.

It is helpful to understand what is meant by risk, in order to protect
the business from unacceptable risks associated with its reliance on
software. Risk is a combination of factors that threaten the success of
the business. This can be described conceptually as follows: a [*threat
agent*](#Threat_Agent) interacts with a [*system*](#System), which may
have a *[vulnerability](#Vulnerability)* that can be
[*exploited*](#Exploit) in order to cause an [*impact*](#Impact). While
this may seem like an abstract concept, think of it this way: a car
burglar (threat agent) goes through a parking lot checking cars (the
system) for unlocked doors (the vulnerability) and when they find one,
they open the door (the exploit) and take whatever is inside (the
impact). All of these factors play a role in secure software
development.

There is a fundamental difference between the approach taken by a
development team and that taken by someone attacking an application. A
development team typically approaches an application based on what it is
intended to do. In other words, they are designing an application to
perform specific tasks based on documented functional requirements and
use cases. An attacker, on the other hand, is more interested in what an
application can be made to do and operates on the principle that \"any
action not specifically denied, is allowed\". To address this, some
additional elements need to be integrated into the early stages of the
software lifecycle. These new elements are [*security
requirements*](#Security_Requirements) and [*abuse cases*](#Abuse_Case).
This guide is designed to help with identifying high level security
requirements and addressing many common abuse scenarios.

It is important for web development teams to understand that client side
controls like client based input validation, hidden fields and interface
controls (e.g., pull downs and radio buttons), provide little if any
security benefit. An attacker can use tools like client side web proxies
(e.g. OWASP ZAP, Burp) or network packet capture tools (e.g.,
WireShark) to analyze application traffic and submit custom built
requests, bypassing the interface all together. Additionally, Flash,
Java Applets and other client side objects can be decompiled and
analyzed for flaws.

Software security flaws can be introduced at any stage of the software
development lifecycle, including:

-   Not identifying security requirements up front

-   Creating conceptual designs that have logic errors

-   Using poor coding practices that introduce technical vulnerabilities

-   Deploying the software improperly

-   Introducing flaws during maintenance or updating

Furthermore, it is important to understand that software vulnerabilities
can have a scope beyond the software itself. Depending on the nature of
the software, the vulnerability and the supporting infrastructure, the
impacts of a successful exploitation can include compromises to any or
all of the following:

- The software and its associated information

- The operating systems of the associated servers

- The backend database

- Other applications in a shared environment

- The user\'s system

- Other software that the user interacts with
