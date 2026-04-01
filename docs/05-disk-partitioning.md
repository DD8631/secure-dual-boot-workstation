# Disk Partitioning Strategy

## Overview

This document outlines the disk partitioning approach used during the installation of Windows 11 and Ubuntu. Proper partition planning was critical to ensuring a stable and low-risk dual-boot configuration.

---

## Objectives

* Allocate disk space for both operating systems
* Avoid resizing partitions after installation
* Maintain compatibility with UEFI and GPT standards
* Reduce risk when working with disk encryption

---

## Disk Configuration

### Hardware

* **Total Disk Size:** ~1 TB NVMe SSD

---

### Final Layout

The disk was partitioned as follows:

* EFI System Partition (~200 MB)
* MSR (Microsoft Reserved) Partition (~16 MB)
* Windows (C:) Partition (~585 GB)
* Recovery Partition (~780 MB)
* **Unallocated Space (~345 GB)**

The unallocated space was intentionally preserved for the Ubuntu installation.

---

## Partitioning Approach

### Clean Disk Preparation

During Windows installation:

* All existing partitions were deleted
* The disk was reduced to a single block of unallocated space

This ensured a clean and predictable starting point.

---

### Manual Partition Creation

Rather than allowing Windows to automatically consume the entire disk:

1. Selected unallocated space
2. Created a new partition for Windows (~600 GB)
3. Allowed Windows to generate required system partitions automatically

This approach ensured control over disk usage and preserved space for Linux.

---

## Key Design Decisions

### Preserving Unallocated Space

A significant portion of the disk (~345 GB) was intentionally left unallocated.

#### Benefits:

* Allowed Ubuntu to install without modifying existing partitions
* Avoided resizing operations on encrypted volumes
* Reduced risk of data corruption

---

### Avoiding Post-Installation Resizing

Resizing partitions after installation—especially when **BitLocker** is enabled—introduces complexity and potential failure points.

By allocating space during the initial setup:

* Partition changes were minimized
* Installation process remained predictable

---

### Alignment with UEFI and GPT

The system was configured using:

* UEFI firmware
* GPT partitioning scheme

This ensured:

* Compatibility with modern operating systems
* Support for Secure Boot
* Proper interaction with the GRUB bootloader

---

## Verification Process

After Windows installation, disk layout was verified using Disk Management.

### Validation Checks:

* Windows partition size confirmed (~585 GB)
* Unallocated space confirmed (~345 GB)
* System partitions present and correctly sized

Verification ensured readiness for Ubuntu installation.

---

## Interaction with Ubuntu Installation

During Ubuntu setup:

* Installer detected unallocated space
* Option to install alongside Windows Boot Manager was available
* No manual partitioning was required

Ubuntu automatically:

* Used available unallocated space
* Created required partitions (root and swap)

---

## Risk Considerations

### Potential Issues Avoided

* Accidental overwrite of Windows partition
* Partition resizing errors
* Encryption conflicts during disk modification

---

## Outcome

The partitioning strategy resulted in:

* Clean separation between operating systems
* Minimal installation complexity
* Reduced risk during setup
* Smooth Ubuntu installation process

---

## Lessons Learned

* Disk planning is critical in dual-boot configurations
* Leaving unallocated space simplifies Linux installation
* Avoiding post-installation resizing reduces risk
* Verification of disk layout is essential before proceeding
* Proper partitioning enables smoother interaction with encryption and bootloaders
