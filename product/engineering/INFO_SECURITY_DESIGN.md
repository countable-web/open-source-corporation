# Information Security Design at Countable

## Purpose

Track infosec system design best-practices

## Scope

This document focuses on design of actual systems, not processes for performing work (covered elsewhere).

## Web Application Host OS Hardening

  * Apply 'least privilege' in general. Only give users/systems access to sensitive information to the extent who need it, and only the minimum level.
  * Normally, only Jenkins should access production servers.
  * Sensitive information should be protected by 2 factors. Use ssh keys with passphrase or stored on an encrypted disk (with passphrase to boot)
  * Minimize the number of open ports (in AWS security group for example)
  * Use CloudFlare or another DDOS and attack detection protection mechanism.

## Container Security Practices [1]

Countable's applications are always containerized. That consistent design lets us re-use security hardening work across projects.

  * Update CRI (Docker, rkt) — Referring above mentioned docker CVE, it is important to keep docker version updated
  * Deploy Only Trusted Docker Images - A malicious container can be loaded if an attacker has replaced the original image with the malicious one So, it is important to allow containers from trusted sources only
  * Start With A Clean OS build - It helps to ensure that host machine is secure from boot
  * Scan the Image For Known Vulnerabilities
  * Don't mount volumes the container does not need access to.

[1] https://medium.com/@dpkumar/your-container-is-in-security-risk-by-design-8a7034f2f9b1
