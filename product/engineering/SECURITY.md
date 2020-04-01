
# Host OS Hardening

  * Apply 'least privilege' in general. Only give users access, who need it. Don't access things you don't need to.
  * Normally, only Jenkins should access production servers.
  * Use ssh keys with passphrase or stored on an encrypted disk (with passphrase to boot)
  * Minimize the number of open ports.
  * Use CloudFlare or another DDOS protection mechanism.

# Container Security Practices

  * Update CRI (Docker, rkt) — Referring above mentioned docker CVE, it is important to keep docker version updated
  * Deploy Only Trusted Docker Images - A malicious container can be loaded if an attacker has replaced the original image with the malicious one So, it is important to allow containers from trusted sources only
  * Start With A Clean OS build - It helps to ensure that host machine is secure from boot
  * Scan the Image For Known Vulnerabilities
  * Don't mount volumes the container does not need access to.
