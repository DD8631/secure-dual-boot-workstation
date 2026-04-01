# Security Hardening and Baseline Configuration

## Overview

This phase focused on establishing a secure baseline configuration for the Windows 11 environment after installation. The goal was to reduce attack surface, enable core security controls, and ensure the system was protected before being exposed to a network.

Security hardening was performed prior to regular use and before connecting the system to external networks.

---

## Objectives

* Enable core Windows security protections
* Reduce unnecessary system exposure
* Configure disk encryption
* Verify system integrity features
* Establish a secure baseline for future use

---

## Windows Security Configuration

System protections were verified and configured using **Windows Security**.

### Virus and Threat Protection

* Real-time protection: Enabled
* Cloud-delivered protection: Enabled
* Automatic sample submission: Enabled

These settings ensure active monitoring and rapid response to emerging threats.

---

### Tamper Protection

* Enabled

Tamper protection prevents unauthorized changes to security settings, including attempts to disable antivirus protections.

---

## Firewall Configuration

The built-in firewall, **Windows Defender Firewall**, was verified to be active.

### Configuration:

* Domain profile: Enabled
* Private profile: Enabled
* Public profile: Enabled

This ensures that inbound and outbound traffic is filtered across all network environments.

---

## Disk Encryption

Full disk encryption was implemented using **BitLocker**.

### Configuration:

* Encryption scope: Entire drive
* Encryption mode: XTS-AES
* Recovery key: Backed up to Microsoft account and external storage

Encryption protects data at rest and mitigates risk in the event of device loss or theft.

---

## Device Security

System integrity features were verified through Windows Security.

### Verified Settings:

* Secure Boot: Enabled
* Trusted Platform Module (TPM): Enabled
* Hardware-based security features: Available

These features help ensure that the system boots in a trusted state and has not been tampered with.

---

## Core Isolation (Memory Integrity)

Where supported, memory integrity (Hypervisor-Protected Code Integrity) was enabled.

### Purpose:

* Prevent execution of malicious or unsigned kernel-level code
* Strengthen protection against advanced attacks

---

## Remote Access and Attack Surface Reduction

Unnecessary remote access features were disabled to reduce exposure.

### Disabled:

* Remote Desktop
* Remote Assistance

### Additional Measures:

* File and printer sharing disabled during initial setup
* No unnecessary services enabled

---

## Network Configuration Strategy

To minimize exposure during setup:

* System remained offline during initial configuration
* Network connection was established only after security settings were verified

### Network Profile:

* Configured as **Public** network

This limits device discoverability and reduces exposure to other systems on the network.

---

## System Cleanup

Initial system review ensured that only necessary components were present.

### Actions:

* Reviewed installed applications
* Removed or avoided unnecessary software
* Maintained minimal baseline configuration

Reducing installed software decreases potential vulnerabilities.

---

## Security Considerations

### Defense in Depth

Multiple layers of protection were implemented, including:

* Antivirus and endpoint protection
* Firewall filtering
* Disk encryption
* Secure boot and hardware validation

---

### Principle of Least Exposure

Unnecessary services and features were disabled to reduce potential attack vectors.

---

### Secure Configuration Before Network Exposure

By delaying network connectivity until after hardening, the system avoided exposure during its most vulnerable state.

---

## Outcome

The system achieved a secure baseline configuration with:

* Active endpoint protection
* Fully enabled firewall
* Full disk encryption
* Verified system integrity features
* Reduced attack surface

This baseline provides a secure foundation for daily use, development, and future lab expansion.

---

## Lessons Learned

* Security configuration should be performed before connecting to a network
* Default settings are not always sufficient for a hardened system
* Disk encryption must be planned alongside system configuration tasks
* Reducing unnecessary services significantly lowers attack surface
* Establishing a baseline early simplifies future security management
