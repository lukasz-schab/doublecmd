# Security Policy

Security issues are taken seriously. This document describes which parts of this repository are covered by this security policy and how security vulnerabilities should be reported.

## Supported Versions

This repository is a fork of the upstream Double Commander project.

Security support provided by this repository primarily applies to the current `master` branch and to changes introduced specifically in this fork.

| Version / Branch | Supported |
| ---------------- | --------- |
| `master` | :white_check_mark: |
| Fork-specific tagged releases explicitly marked as supported | :white_check_mark: |
| Older or unmaintained branches | :x: |
| Upstream Double Commander releases not modified by this fork | See upstream project |

A vulnerability affecting unmodified upstream Double Commander code may also be reported here if it was discovered while reviewing this repository. However, such vulnerabilities may need to be coordinated with the upstream Double Commander maintainers.

Security support does not imply that every historical release or upstream version receives backported security fixes.

## Reporting a Vulnerability

**Do not publicly disclose a suspected vulnerability before it has been reviewed and, where appropriate, remediated.**

The preferred reporting method is GitHub Private Vulnerability Reporting / Security Advisories for this repository:

1. Open the repository on GitHub.
2. Go to **Security**.
3. Open **Advisories**.
4. Select **Report a vulnerability**.

If private vulnerability reporting is not available, do **not** publish exploit details, proof-of-concept code, credentials, sensitive data, or technical reproduction steps in a public GitHub issue.

Instead, create a minimal public issue requesting a private security contact channel without disclosing sensitive technical information.

## What to Include in a Report

A useful security report should contain, where possible:

- a clear description of the vulnerability;
- the affected component, file, module, plugin, or functionality;
- affected versions, branches, commits, or platforms;
- vulnerability class, for example:
  - command injection;
  - path traversal;
  - arbitrary file write;
  - unsafe archive extraction;
  - DLL / shared-library hijacking;
  - insecure plugin loading;
  - SQL injection;
  - authentication or authorization bypass;
  - insecure temporary-file handling;
  - TLS / certificate validation issues;
  - memory-safety issues;
  - unsafe deserialization;
  - sensitive information disclosure;
- prerequisites required for exploitation;
- attack vector and required attacker capabilities;
- step-by-step reproduction instructions;
- a minimal proof of concept, when appropriate;
- expected and actual behavior;
- potential security impact;
- relevant logs, stack traces, screenshots, or packet captures;
- suggested remediation, if known.

If applicable, the report may also contain:

- CWE classification;
- CVSS v4.0 vector and score;
- affected operating systems;
- affected architectures;
- affected compiler/runtime versions;
- information about whether the vulnerability also affects the upstream Double Commander project.

Please remove passwords, authentication tokens, personal information, private keys, or other unrelated sensitive data before submitting evidence.

## Response Targets

The following are target response times rather than contractual guarantees:

| Stage | Target |
| ----- | ------ |
| Initial acknowledgement | within 3 business days |
| Initial technical triage | within 7 business days |
| Status update for an active investigation | at least every 7 days |
| Critical vulnerability remediation target | as soon as reasonably possible |
| Other confirmed vulnerabilities | based on severity, complexity, and upstream dependencies |

Complex vulnerabilities, cross-platform issues, upstream dependencies, or fixes requiring architectural changes may require additional time.

## Triage Process

After receiving a report, the maintainer will attempt to:

1. confirm that the report concerns the correct repository and component;
2. reproduce the reported behavior;
3. determine whether the issue is security-relevant;
4. identify affected versions, branches, and platforms;
5. assess exploitability and impact;
6. determine whether the issue originates from:
   - this fork;
   - upstream Double Commander;
   - a third-party dependency;
   - build or CI/CD infrastructure;
7. establish an appropriate remediation strategy;
8. coordinate with upstream or third-party maintainers when required.

A report may be closed as not applicable if the reported behavior:

- cannot be reproduced;
- does not cross a security boundary;
- requires assumptions that cannot occur in supported configurations;
- affects only unsupported code;
- represents expected behavior rather than a vulnerability.

Additional evidence may be requested before making that determination.

## Severity Assessment

Confirmed vulnerabilities may be assessed using:

- **CVSS v4.0**;
- relevant **CWE** classifications;
- practical exploitability;
- required privileges;
- user interaction;
- affected platforms;
- impact on confidentiality, integrity, and availability;
- exploit prerequisites;
- realistic attack scenarios.

Automated scanner severity alone is not considered sufficient to determine the final severity of a vulnerability.

Findings produced by SAST, CodeQL, Semgrep, dependency scanners, secret scanners, fuzzers, or similar automated tools are treated as leads until technically validated.

## Coordinated Disclosure

Please allow a reasonable amount of time for investigation and remediation before publicly disclosing a vulnerability.

For confirmed vulnerabilities, disclosure may include:

- a GitHub Security Advisory;
- a remediation commit;
- an affected-version statement;
- a CVE identifier, when appropriate;
- technical details sufficient for users to understand the risk and remediation.

Where the vulnerability originates in upstream Double Commander or a third-party component, disclosure timing may be coordinated with the relevant maintainers.

Researchers are encouraged to avoid public disclosure while remediation and coordinated disclosure are actively in progress.

## Security Research Guidelines

Good-faith security research is welcome.

Researchers should:

- test only systems, software, and data they are authorized to access;
- minimize impact on users and infrastructure;
- avoid destructive testing;
- avoid modifying or deleting unrelated data;
- stop testing if unintended access to sensitive information occurs;
- collect only the minimum evidence necessary to demonstrate the issue;
- securely delete sensitive information obtained unintentionally;
- report vulnerabilities through the private reporting process.

Researchers must not:

- use vulnerabilities to access unrelated third-party systems or data;
- perform denial-of-service attacks against public infrastructure;
- use social engineering against project contributors or users;
- publish credentials, personal information, private keys, tokens, or confidential data;
- intentionally introduce vulnerabilities or malicious code.

## Automated Security Findings

This repository may use several automated security-analysis mechanisms, including:

- CodeQL;
- dependency analysis;
- secret scanning;
- GitHub Actions security analysis;
- static-analysis heuristics;
- supply-chain security checks.

An automated alert does **not** automatically mean that a confirmed vulnerability exists.

Security findings should be validated against:

- actual source-to-sink data flow;
- attacker control over the input;
- sanitization and validation;
- trust boundaries;
- operating-system behavior;
- platform-specific mitigations;
- realistic exploitation prerequisites.

False positives should be documented and suppressed narrowly rather than by globally disabling a security control.

## Upstream Vulnerabilities

This repository is based on the Double Commander project.

If a vulnerability affects code that has not been modified by this fork, remediation may require changes in the upstream project.

Where appropriate, the issue may therefore be reported or coordinated with the upstream maintainers.

A vulnerability should not be publicly duplicated across multiple repositories while coordinated disclosure is still in progress.

## Third-Party Dependencies

Some vulnerabilities may originate in third-party libraries, tools, plugins, compilers, runtimes, operating-system components, GitHub Actions, or other dependencies.

When this occurs, remediation may include:

- updating the affected dependency;
- disabling or replacing the vulnerable component;
- applying a workaround;
- introducing additional validation or sandboxing;
- waiting for an upstream security fix.

The security status of a third-party dependency is not automatically equivalent to the security status of the application using it. Exploitability must be evaluated in the context of this project.

## Security-Sensitive Areas

Particular attention should be paid to functionality involving:

- file-system operations;
- archive extraction;
- symbolic and hard links;
- file permissions;
- temporary files and directories;
- command and process execution;
- shell integration;
- URL and protocol handlers;
- network communication;
- TLS certificate validation;
- plugins;
- dynamic libraries;
- external tools;
- filesystem paths received from untrusted sources;
- configuration file parsing;
- credentials and secrets;
- Windows shell and DLL loading behavior;
- Linux/macOS shared-library loading;
- privileged operations;
- IPC and inter-process communication.

Because Double Commander is a file manager, vulnerabilities involving filesystem trust boundaries may have significantly greater impact than similar issues in applications that do not directly manipulate files.

## Acknowledgements

Researchers who responsibly disclose confirmed vulnerabilities may be acknowledged in the corresponding security advisory or release notes, unless they request anonymity.

Thank you for helping improve the security of this project.
