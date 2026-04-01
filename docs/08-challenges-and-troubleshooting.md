# Challenges and Troubleshooting

## Overview

This document outlines the key challenges encountered during the build of a secure dual-boot workstation and the steps taken to resolve them. These issues primarily involved interactions between Windows security features and Linux installation requirements.

---

## BitLocker Blocking Ubuntu Installation

### Issue

During the installation of Ubuntu, the installer detected that the Windows partition was protected by **BitLocker**.

### Symptoms

* Installer displayed a warning about encrypted volumes
* Option to proceed with installation was unavailable
* User was prompted to return to Windows

### Cause

BitLocker prevents modification of disk partitions while encryption is active. This is a security feature designed to protect against unauthorized changes to disk structure.

### Resolution

* BitLocker was initially suspended but automatically resumed after reboot
* Full decryption of the drive was performed by turning off BitLocker
* Installation proceeded successfully once encryption was fully disabled

---

## BitLocker Suspension Did Not Persist

### Issue

Attempting to suspend BitLocker protection did not allow installation to proceed.

### Symptoms

* BitLocker appeared suspended in Windows
* After reboot, Ubuntu installer still detected encryption
* Installer continued to block partition changes

### Cause

BitLocker suspension may not persist when boot flow changes significantly (e.g., booting from external USB). The Trusted Platform Module (TPM) and Secure Boot chain can trigger automatic reactivation.

### Resolution

* BitLocker was fully disabled instead of suspended
* Drive was allowed to decrypt completely before retrying installation

---

## System Boot Failure (Black Screen)

### Issue

After attempting installation and rebooting, the system failed to display any output.

### Symptoms

* Black screen on startup
* No visible boot sequence
* System appeared unresponsive

### Cause

Likely caused by an interrupted or inconsistent boot state during transition between encrypted and unencrypted configurations, or firmware confusion during boot device selection.

### Resolution

* Forced shutdown by holding power button
* Accessed boot menu using `F12`
* Selected Windows Boot Manager manually
* System successfully recovered and booted into Windows

---

## Recovery Key Confusion

### Issue

Multiple BitLocker recovery keys were present for the same device.

### Symptoms

* More than one recovery key listed in Microsoft account
* Uncertainty about which key to use

### Cause

BitLocker generates new recovery keys when:

* Encryption is re-enabled
* Boot configuration changes (e.g., GRUB installation)
* Significant system modifications occur

### Resolution

* Verified that each key includes a unique Key ID
* Matched Key ID displayed on system with stored keys
* Retained all recovery keys for safety

---

## GRUB Bootloader Behavior

### Issue

After installation, the system defaulted to Ubuntu instead of Windows.

### Symptoms

* GRUB menu appeared at startup
* Ubuntu selected as default boot option

### Cause

GRUB typically prioritizes the most recently installed operating system.

### Resolution

* Verified both operating systems were accessible
* Accepted default behavior for flexibility
* Identified method to change default if needed

---

## Disk Preparation Risk Avoidance

### Issue

Improper partitioning during Windows installation could have prevented successful dual-boot setup.

### Risk

* If entire disk was allocated to Windows, resizing would be required
* Resizing encrypted partitions introduces additional risk

### Resolution

* Manually created Windows partition during installation
* Left ~345GB unallocated space for Ubuntu
* Verified disk layout before proceeding

---

## Key Takeaways

* Security features like BitLocker can interfere with system configuration tasks
* Suspending encryption is not always sufficient; full decryption may be required
* Boot issues can often be resolved through manual boot selection
* Recovery key management is critical when working with encryption
* Proper planning during initial setup prevents major issues later
* Troubleshooting is an expected and valuable part of system configuration

---

## Outcome

All issues were successfully resolved without data loss. The final system achieved:

* Functional dual-boot configuration
* Fully encrypted Windows environment
* Stable boot process using GRUB
* Verified recovery key access

This troubleshooting process provided practical experience in managing system security, disk configuration, and boot processes in a real-world scenario.
