# Ubuntu Installation and Dual-Boot Configuration

## Overview

This phase focused on installing Ubuntu alongside Windows 11 to create a dual-boot environment. The installation leveraged previously reserved unallocated disk space and required careful handling of BitLocker encryption to ensure a successful setup.

---

## Objectives

* Install Ubuntu alongside Windows 11
* Utilize pre-allocated unallocated disk space
* Configure GRUB bootloader for OS selection
* Maintain integrity of the Windows installation
* Resolve encryption-related installation conflicts

---

## Installation Media Preparation

A bootable Ubuntu USB installer was created using:

* **Rufus**
* Ubuntu Desktop LTS ISO

### Rufus Configuration:

* Partition Scheme: GPT
* Target System: UEFI (non-CSM)
* File System: FAT32

This ensured compatibility with the system’s UEFI firmware and existing Windows installation.

---

## Boot Process

The system was booted into the Ubuntu installer using the ThinkPad boot menu:

* Accessed via `F12` during startup
* Selected USB device in **UEFI mode**

This launched the Ubuntu live environment.

---

## Live Environment

After booting:

* Selected **“Try or Install Ubuntu”**
* Entered the live desktop environment
* Launched installer via **“Install Ubuntu”** shortcut

---

## Installation Configuration

### Initial Settings

* Keyboard layout configured
* Selected **Normal Installation**
* Enabled:

  * Download updates during installation
  * Install third-party software

---

## BitLocker Conflict and Resolution

During installation, the installer detected that the Windows partition was protected by **BitLocker**.

### Issue:

* Installer blocked partition changes
* Option to proceed was unavailable
* System prompted to return to Windows

### Attempted Approach:

* BitLocker was suspended
* Suspension did not persist across reboot

### Final Resolution:

* BitLocker was fully turned off
* Drive was allowed to decrypt completely

This allowed the installer to safely modify disk partitions.

---

## Installation Type Selection

After resolving the BitLocker issue, the installer presented available installation options.

### Selected:

> **Install Ubuntu alongside Windows Boot Manager**

This option automatically:

* Detected existing Windows installation
* Used the previously unallocated disk space
* Configured partitions appropriately

---

## Partition Allocation

A partition slider was presented to allocate disk space between operating systems.

### Configuration:

* Ubuntu allocated a portion of the ~345GB unallocated space
* Windows partition remained unchanged

Ubuntu automatically created:

* Root (`/`) partition
* Swap space

---

## Bootloader Configuration

The installer configured the GRUB bootloader.

### Result:

* GRUB installed as primary boot manager
* System presents OS selection menu at startup

---

## Installation Completion

The installation completed without further issues.

Steps:

1. System prompted for restart
2. USB installer removed when instructed
3. System rebooted

---

## Post-Installation Behavior

Upon reboot:

* GRUB menu displayed successfully
* Available options:

  * Ubuntu
  * Windows Boot Manager

Ubuntu was set as the default boot option.

---

## Validation

Both operating systems were tested:

* Ubuntu booted successfully
* Windows booted successfully via GRUB

No data loss or corruption was observed.

---

## Post-Installation Security Step

After confirming system stability:

* **BitLocker was re-enabled in Windows**
* Full disk encryption was applied to entire drive

Recovery keys were verified and backed up.

---

## Key Considerations

### Importance of Unallocated Space

Pre-allocating disk space during Windows installation simplified the Ubuntu setup and avoided risky partition resizing.

### BitLocker Interaction

BitLocker can prevent Linux installers from modifying disk structures. Full decryption was required to proceed safely.

### UEFI Consistency

Maintaining UEFI mode across both installations ensured compatibility with GRUB and Secure Boot.

---

## Outcome

This phase successfully established a dual-boot environment with:

* Windows 11 (encrypted with BitLocker)
* Ubuntu (fully functional Linux environment)
* GRUB bootloader for OS selection

The system is now capable of supporting development, security testing, and lab expansion.

---

## Lessons Learned

* BitLocker can interfere with multi-boot setups if not properly managed
* Suspending encryption may not persist across reboots
* Full decryption is sometimes required for safe partition changes
* Verifying disk layout before installation prevents critical errors
* GRUB provides a flexible and reliable boot management solution
