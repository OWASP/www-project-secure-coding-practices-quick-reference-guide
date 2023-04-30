---

layout: col-document
title: Secure Coding Practices
tags: SCP-QRG
document: OWASP Secure Coding Practices - Quick Reference Guide

---

{% include breadcrumb.html %}
# Appendix B: Glossary

**Abuse case:** Describes the intentional and
  unintentional misuses of the software. Abuse cases should challenge the
  assumptions of the system design.

**Access control:** A set of controls that grant or deny a user, or
  other entity, access to a system resource. This is usually based on
  hierarchical roles and individual privileges within a role, but also
  includes system to system interactions.

**Account disabling:** Account disabling after an established number of invalid
  login attempts (e.g., five attempts is common). The account must
  be disabled for a period of time sufficient to discourage brute
  force guessing of credentials, but not so long as to allow for a
  denial-of-service attack to be performed

**Authentication:** A set of controls that are used to verify the
  identity of a user, or other entity, interacting with the software.

  Authentication failure responses should not indicate which part of
  the authentication data was incorrect. For example, instead of
  \"Invalid username\" or \"Invalid password\", just use \"Invalid
  username and/or password\" for both. Error responses must be truly
  identical in both display and source code

**Availability:** A measure of a system\'s accessibility and usability.

**Calculation errors:** Avoid calculation errors by understanding your programming
  language\'s underlying representation and how it interacts with
  numeric calculation. Pay close attention to byte size
  discrepancies, precision, signed/unsigned distinctions,
  truncation, conversion and casting between types, \"not-a-number\"
  calculations, and how your language handles numbers that are too
  large or too small for its underlying representation

**Canonicalize:** To reduce various encodings
  and representations of data to a single simple form.

**Communication security:** A set of controls that help ensure the
  software handles the sending and receiving of information in a secure
  manner.

**Confidentiality:** To ensure that information is disclosed only to authorized parties.

**Contextual output encoding:**
  Encoding output data based on how it will be utilized by the
  application. The specific methods vary depending on the way the output
  data is used. If the data is to be included in the response to the
  client, account for inclusion scenarios like: the body of an HTML
  document, an HTML attribute, within JavaScript, within a CSS or in a URL.
  You must also account for other use cases like SQL queries, XML and LDAP.
  Consider HTML entity encoding, but this may not work in all cases.

**Cross Site Request Forgery (CSRF):**
  An external website or application forces a client to make an unintended
  request to another application that the client has an active session
  with. Applications are vulnerable when they use known, or predictable,
  URLs and parameters; and when the browser automatically transmits all
  required session information with each request to the vulnerable
  application.

**Cryptographic practices:** A set of controls that ensure cryptographic
  operations within the application are handled securely.

**Data protection:** A set of controls that help ensure the software
  handles the storing of information in a secure manner.

**Database security:** A set of controls that ensure that software
  interacts with a database in a secure manner and that the database is
  configured securely.

**Error handling and logging:** A set of practices that ensure the
  application handles errors safely and conducts proper event logging.

**Exploit:** To take advantage of a vulnerability.
  Typically this is an intentional action designed to compromise the
  software\'s security controls by leveraging a vulnerability.

**File management:** A set of controls that cover the interaction
  between the code and other system files.

**General coding practices:** A set of controls that cover coding
  practices that do not fit easily into other categories.

**Hazardous character:** Any character
  or encoded representation of a character that can effect the intended
  operation of the application or associated system by being interpreted
  to have a special meaning, outside the intended use of the character.
  These characters may be used to:

  * Altering the structure of existing code or statements
  * Inserting new unintended code
  * Altering paths
  * Causing unexpected outcomes from program functions or routines
  * Causing error conditions
  * Compromise downstream applications or systems

  If any potentially hazardous characters
  must be allowed as input, be sure that you implement additional
  controls like output encoding, secure task specific APIs and
  accounting for the utilization of that data throughout the
  application . Examples of common hazardous characters include:
  > \< \> \" \' % ( ) & + \\ \\\' \\\"

  * Check for new line characters (%0d, %0a, \\r, \\n)
  * Check for "dot-dot-slash\" (../ or ..\\) path alterations
    characters. In cases where UTF-8 extended character set
    encoding is supported, address alternate representation like:
    %c0%ae%c0%ae/

**HTML eEntity encode:** The process of
  replacing certain ASCII characters with their HTML entity equivalents.
  For example, encoding would replace the less than character \"\<\" with
  the HTML equivalent \"&lt;\". HTML entities are \'inert\' in most
  interpreters, especially browsers, which can mitigate certain client
  side attacks.

**Impact:** A measure of the negative effect to the
  business that results from the occurrence of an undesired event; what
  would be the result of a vulnerability being exploited.

**Input validation:** A set of controls that verify the properties of
  all input data matches what is expected by the application including
  types, lengths, ranges, acceptable character sets and does not include
  known hazardous characters.

**Integrity:** The assurance that information is
  accurate, complete and valid, and has not been altered by an
  unauthorized action.

**Log event data:** This should include the following:

  1. Time stamp from a trusted system component
  2. Severity rating for each event
  3. Tagging of security relevant events, if they are mixed with other log entries
  4. Identity of the account/user that caused the event
  5. Source IP address associated with the request
  6. Event outcome (success or failure)
  7. Description of the event

  Implement monitoring to identify attacks against multiple user
  accounts, utilizing the same password. This attack pattern is used
  to bypass standard lockouts, when user IDs can be harvested or
  guessed.

**Memory management:** A set of controls that address memory and buffer usage.

**Mitigate:** Steps taken to reduce the severity of
  a vulnerability. These can include removing a vulnerability, making a
  vulnerability more difficult to exploit, or reducing the negative impact
  of a successful exploitation.

**Multi-Factor Authentication (MFA):** An authentication process that requires
  the user to produce multiple distinct types of credentials.
  Typically this is based on something:

  * they have, for example a mobile/cell phone
  * something they know, for example a PIN
  * something they are, for example data from a biometric reader

**Output encoding:** A set of controls addressing the use of encoding to
  ensure data output by the application is safe.

**Parameterized queries / prepared statements:**
  Keeps the query and data separate through the use of
  placeholders. The query structure is defined with place holders, the SQL
  statement is sent to the database and prepared, and then the prepared
  statement is combined with the parameter values. The prevents the query
  from being altered, because the parameter values are combined with the
  compiled statement, not a SQL string.

**Password complexity**: Password complexity requirements established by policy or
  regulation. Authentication credentials should be sufficient to
  withstand attacks that are typical of the threats in the deployed
  environment. (e.g., requiring the use of alphabetic as well as
  numeric and/or special characters).

**Password length:** Password length requirements established by policy or
  regulation. Eight characters is commonly used, but 16 is better or
  consider the use of multi-word pass phrases

**Persistent logins**: Disallow persistent logins and enforce periodic session
  terminations, even when the session is active. Especially for
  applications supporting rich network connections or connecting to
  critical systems. Termination times should support business
  requirements and the user should receive sufficient notification
  to mitigate negative impacts

**Safe updates:** Method of updating the application from trusted sources.
  If the application utilizes automatic
  updates, then use cryptographic signatures for your code and
  ensure your download clients verify those signatures. Use
  encrypted channels to transfer the code from the host server

**Sanitize data:** The process of making
  potentially harmful data safe through the use of data removal,
  replacement, encoding or escaping of the characters.

**Security controls:** An action that
  mitigates a potential vulnerability and helps ensure that the software
  behaves only in the expected manner.

**Security requirements:** A set of
  design and functional requirements that help ensure the software is
  built and deployed in a secure manner.

**Sequential authentication:**
  When authentication data is requested on successive pages rather than
  being requested all at once on a single page.

**Session management:** A set of controls that help ensure web
  applications handle HTTP sessions in a secure manner.

  Do not expose session identifiers in URLs, error messages or logs.
  Session identifiers should only be located in the HTTP cookie
  header. For example, do not pass session identifiers as GET
  parameters

**State data:** When data or parameters are used,
  by the application or server, to emulate a persistent connection or
  track a client\'s status across a multi-request process or transaction.

**System:** A generic term covering the operating
  systems, web server, application frameworks and related infrastructure.

**System configuration:** A set of controls that help ensure the
  infrastructure components supporting the software are deployed securely.

**Threat Agent:** Any entity which may have a
  negative impact on the system. This may be a malicious user who wants to
  compromise the system\'s security controls; however, it could also be an
  accidental misuse of the system or a more physical threat like fire or
  flood.

**Trust boundaries:** Typically a trust
  boundary constitutes the components of the system under your direct
  control. All connections and data from systems outside of your direct
  control, including all clients and systems managed by other parties,
  should be consider untrusted and be validated at the boundary before
  allowing further system interaction.

**Vulnerability:** A weakness that makes the system susceptible to attack or damage.

\newpage
