# Hardware and Tools

## Overview

This document outlines the hardware platform and tools used to build the secure dual-boot workstation. Defining the environment ensures that the setup is reproducible and provides context for system behavior during installation and troubleshooting.

---

## Hardware Platform

### System

* **Model:** Lenovo ThinkPad E15
* **Processor:** Intel Core i7
* **Memory:** 32 GB RAM
* **Storage:** 1 TB NVMe SSD

The ThinkPad platform was selected due to its reliability, strong Linux compatibility, and support for modern firmware features such as UEFI and Trusted Platform Module (TPM).

---

## Peripheral Devices

### USB Flash Drives

* Multiple 32 GB USB 3.0 flash drives

Used for:

* Windows 11 installation media
* Ubuntu installation media
* Future recovery and tooling use

---

## Operating Systems

### Windows 11

* Installed as the primary operating system
* Provides a stable and secure environment for daily use
* Integrated with device encryption using **BitLocker**

---

### Ubuntu (LTS)

* Installed as a secondary operating system

* Provides a Linux-based environment for development and security tasks

* Selected for long-term stability and support

* **Distribution:** Ubuntu Desktop LTS

---

## Installation Tools

### Windows Installation Media

* Created using the official media creation tool from **Microsoft**
* Configured to support UEFI-based installation

---

### USB Imaging Tool

* **Rufus**

Used to:

* Create bootable Ubuntu installation media
* Configure USB with GPT partition scheme and UEFI compatibility

---

## System Configuration Tools

### Windows Disk Management

* Used to verify disk layout after installation
* Confirmed presence of unallocated space for Ubuntu

---

### Windows Security Interface

* Used to verify system protection features
* Confirmed firewall, antivirus, and system integrity settings

---

### BitLocker Management

* Used to enable, disable, and monitor disk encryption
* Managed recovery key generation and storage

---

## Firmware and Boot Environment

### UEFI Firmware

* System configured to boot in UEFI mode
* Required for:

  * GPT partitioning
  * Secure Boot compatibility
  * Dual-boot support with modern operating systems

---

### Boot Menu Access

* Accessed via `F12` during system startup
* Used to select between:

  * Windows Boot Manager
  * USB installation media

---

## Networking (Initial State)

* System initially configured offline during setup
* Network connection established after security baseline verification

This approach minimized exposure during initial system configuration.

---

## Summary

The selected hardware and tools provided a stable and compatible environment for building a secure dual-boot workstation. The combination of modern firmware, sufficient system resources, and reliable tooling enabled a smooth installation process and supported effective troubleshooting.

This environment also provides a strong foundation for future expansion into virtualization and cybersecurity lab development.
