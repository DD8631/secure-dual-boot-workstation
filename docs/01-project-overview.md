# Project Overview

## Purpose

This project documents the design and implementation of a secure dual-boot workstation using Windows 11 and Ubuntu. The system was built to support cybersecurity learning, Linux development, and future lab expansion while maintaining a secure and stable Windows environment.

The primary goal was to create a repeatable and well-documented deployment process that balances usability, security, and flexibility.

---

## Goals

* Build a clean Windows 11 installation with a secure baseline
* Implement full disk encryption using **BitLocker**
* Configure a dual-boot environment with Ubuntu
* Preserve system integrity during partitioning and OS installation
* Establish a foundation for future cybersecurity lab development
* Document all steps, decisions, and challenges

---

## System Architecture

The system is structured as a dual-boot environment:

* **Windows 11**

  * Primary operating system
  * Encrypted with BitLocker
  * Used for daily tasks and secure operations

* **Ubuntu**

  * Secondary operating system
  * Installed alongside Windows
  * Used for development, Linux administration, and security tooling

* **GRUB Bootloader**

  * Manages operating system selection at startup
  * Provides flexibility between environments

---

## Key Design Decisions

### Manual Disk Partitioning

During Windows installation, disk space was intentionally divided to leave unallocated space for Ubuntu. This eliminated the need for resizing encrypted partitions later and reduced risk during setup.

### Encryption Management Strategy

BitLocker was temporarily disabled to allow safe partition modification and re-enabled after successful installation. This ensured both security and compatibility with the Linux installer.

### UEFI and GPT Configuration

The system was configured using UEFI firmware and GPT partitioning to support modern security features such as Secure Boot and ensure compatibility across both operating systems.

---

## Use Cases

This workstation is intended to support:

* Cybersecurity learning and experimentation
* Linux development and system administration
* Testing dual-boot and encryption interactions
* Building and hosting a future home lab environment
* Practicing system hardening and recovery procedures

---

## Scope

This project focuses on:

* Operating system installation and configuration
* Disk partitioning strategy
* Encryption management
* Bootloader configuration
* Troubleshooting and recovery

Future work will expand into lab environments, virtualization, and network-based security testing.

---

## Outcome

The final system provides:

* A stable dual-boot environment
* Full disk encryption on Windows
* Functional GRUB bootloader
* Verified recovery key management
* A documented and repeatable setup process

This project establishes a strong foundation for continued development in cybersecurity and systems engineering.

---

## Key Takeaways

* Planning disk layout early simplifies complex configurations
* Security features can introduce constraints that must be managed carefully
* Dual-boot systems require coordination between operating systems and firmware
* Troubleshooting and documentation are essential parts of system design

---

## Next Steps

Planned improvements include:

* Expanding into a cybersecurity home lab
* Adding additional operating systems (e.g., Kali Linux)
* Creating a reusable system image (gold image baseline)
* Automating portions of the setup process
* Enhancing system hardening and monitoring
