# Security Hardening and Remediation

This repository contains documentation, guides, and hands-on work I performed to improve the security posture of an Ubuntu server connected via Azure Arc. The hardening steps address recommendations from Microsoft Defender for Cloud, focusing on SSH access control and system configuration.

## Included Guides

- [SSH Security Hardening](ssh-hardening.md)  
  Step-by-step instructions I followed to secure SSH access on my Azure Ubuntu VM, including configuration settings, best practices, and how I verified the hardening.

- [Defender for Cloud Remediation](defender-remediation.md)  
  Documentation of how I reviewed and remediated "Unhealthy" recommendations flagged by Microsoft Defender for Cloud.
  ## 📸 Visual Evidence

### 🔐 SSH Hardening

**Before Hardening**  
[![SSH Before Hardening] <https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/1c002c5b49e021c4cde2fd697ce4bbb44a16492a/images/images%20ssh-before.png> 

**After Hardening**  
[![SSH After Hardening]<https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/07787aca5a2e539bdfc6a2ede1180452110dc00d/images/images%20ssh-after.png.png>

### 🛡️ Defender for Cloud Remediation

**Unhealthy Recommendations**  
[![Defender Unhealthy]<https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/b1d811466b6e10f6ca2b46768aadb4238c298bca/images/defender-unhealthy.png.png>
**After Remediation**  
[![Defender Remediated]<https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/48f504fa0b5705f44acdd992d1c584d7a75639e4/images/defender-healthy.png%20(2).png>


## Purpose

This project serves as:

- A record of the hardening steps I applied in a live Azure environment  
- A guide that others can follow or replicate  
- Evidence of practical skills in system hardening, cloud security, and compliance remediation

It is also designed to help system administrators and contributors:

- Understand the hardening measures implemented  
- Replicate the documented steps reliably  
- Track and review remediation efforts effectively

## Contributing

If you identify a security issue or have a suggestion for improvement, feel free to:

- Open an issue with relevant details  
- Submit a pull request referencing the appropriate guide  

Thank you for your interest and contributions!

## Author

👤 **Babatunde Qodri**  
This project was completed independently using my Azure subscription as part of my hands-on cybersecurity learning journey.

---
