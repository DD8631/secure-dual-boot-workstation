# Windows 11 Installation and Disk Preparation

## Overview

This phase of the project focused on performing a clean installation of Windows 11 and preparing the disk for a future dual-boot configuration with Ubuntu. The key requirement during this process was to intentionally preserve unallocated disk space for the Linux installation.

---

## Objectives

* Perform a clean Windows 11 installation
* Remove all existing partitions
* Manually create a primary Windows partition
* Reserve unallocated space for Ubuntu
* Ensure compatibility with UEFI and GPT partitioning

---

## Installation Media Preparation

A bootable Windows 11 USB installer was created using the official media creation tool provided by Microsoft. The tool formatted the USB drive and prepared it for UEFI-based installation.

---

## Boot Process

The system was booted into the installer using the ThinkPad boot menu:

* Accessed via `F12` during startup
* Selected USB device in **UEFI mode**

This ensured compatibility with modern partitioning and security features.

---

## Disk Preparation

### Removing Existing Partitions

During installation, all existing partitions on the internal SSD were deleted to ensure a clean starting point. This included:

* System partitions
* Recovery partitions
* Primary data partitions

After deletion, the disk showed a single block of unallocated space.

---

### Partition Strategy

Instead of allowing Windows to consume the entire disk, a manual partition was created.

**Configuration:**

* Total disk size: ~1TB
* Windows partition: ~585GB
* Remaining space: ~345GB (left unallocated)

This approach ensured that sufficient contiguous space remained available for the Ubuntu installation.

---

### Partition Creation Process

1. Selected **Unallocated Space**
2. Clicked **New**
3. Specified size in MB (~600000 MB)
4. Allowed Windows to automatically create required system partitions

Windows created:

* EFI System Partition
* MSR (Microsoft Reserved)
* Primary partition (C:)
* Recovery partition

---

## Installation Completion

Windows was installed on the newly created primary partition. After installation:

* Initial setup was completed
* System booted successfully into Windows 11
* No errors or conflicts were observed

---

## Disk Layout Verification

Disk layout was verified using Windows Disk Management.

### Final Structure:

* EFI System Partition (~200MB)
* MSR Partition (~16MB)
* Windows (C:) (~585GB)
* Recovery Partition (~780MB)
* **Unallocated Space (~345GB)**

The presence of unallocated space confirmed that the system was correctly prepared for dual-boot installation.

---

## Key Considerations

### Why Manual Partitioning Was Necessary

Allowing Windows to use the entire disk would have required resizing partitions later, which introduces unnecessary risk when encryption is enabled.

### UEFI and GPT Alignment

The installation was performed in UEFI mode with GPT partitioning to ensure compatibility with:

* Secure Boot
* Modern OS requirements
* Future Linux installation

---

## Outcome

This phase successfully established a clean and controlled Windows 11 environment while preserving disk space for Ubuntu. The system was now ready for:

* Security baseline configuration
* Dual-boot Linux installation
* Further development and lab setup

---

## Lessons Learned

* Always plan disk layout before OS installation
* Leaving unallocated space simplifies dual-boot setups significantly
* Verifying partition layout early prevents reinstallation later
* UEFI boot mode is critical for modern systems and security features
