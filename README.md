# Secure Dual-Boot Workstation

## Overview

This project documents the design and implementation of a secure dual-boot workstation using Windows 11 and Ubuntu. The system was built with a focus on security, stability, and flexibility to support cybersecurity learning, Linux development, and future lab expansion.

---

## Key Features

* Clean Windows 11 installation with secure baseline configuration
* Full disk encryption using BitLocker
* Dual-boot setup with Ubuntu
* GRUB bootloader for OS selection
* Manual disk partitioning strategy
* Documented troubleshooting and recovery process

---

## System Architecture

* **Windows 11**

  * Primary OS
  * Encrypted with BitLocker
  * Used for secure daily operations

* **Ubuntu**

  * Secondary OS
  * Used for development and security tooling

* **GRUB Bootloader**

  * Handles OS selection at startup

---

## Documentation

### Project Foundation

* [Project Overview](docs/01-project-overview.md)
* [Hardware and Tools](docs/02-hardware-and-tools.md)

### System Build

* [Windows 11 Installation](docs/03-windows-11-install.md)
* [Security Hardening](docs/04-security-hardening.md)
* [Disk Partitioning Strategy](docs/05-disk-partitioning.md)

### Dual-Boot Setup

* [Ubuntu Installation](docs/06-ubuntu-install.md)
* [BitLocker and Recovery](docs/07-bitlocker-and-recovery.md)

### Troubleshooting and Reflection

* [Challenges and Troubleshooting](docs/08-challenges.md)
* [Future Improvements](docs/09-future-improvements.md)

---

## Key Skills Demonstrated

* Operating system installation and configuration
* Disk partition planning and management
* Dual-boot system setup and bootloader configuration
* BitLocker encryption management
* System hardening and security baseline implementation
* Troubleshooting boot and installation issues
* Technical documentation and project structuring

---

## Challenges Encountered

Key issues addressed during this project include:

* BitLocker blocking Linux installation
* Encryption suspension not persisting across reboot
* System boot failure (black screen) and recovery
* Recovery key management and identification

See full details:
[Challenges and Troubleshooting](docs/08-challenges.md)

---

## Outcome

The final system provides:

* Secure Windows environment with full disk encryption
* Fully functional Ubuntu installation
* Reliable dual-boot configuration
* Verified recovery and troubleshooting procedures
* A documented and repeatable build process

---

## Future Work

Planned areas for expansion include:

* Building an isolated cybersecurity lab environment
* Adding additional operating systems and tools
* Creating reusable system images
* Expanding system monitoring and hardening

See full details:
[Future Improvements](docs/09-future-improvements.md)

---

## Author Notes

This project was built as part of a transition into cybersecurity and systems-focused development. It reflects a hands-on approach to learning through building, troubleshooting, and documenting real-world configurations.

