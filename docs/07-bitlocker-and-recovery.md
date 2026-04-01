# BitLocker Encryption and Recovery Management

## Overview

This phase focused on managing **BitLocker** during the dual-boot installation process. While BitLocker provides strong data-at-rest protection, it introduced challenges when modifying disk partitions for the installation of Ubuntu.

---

## Objectives

* Enable disk encryption for Windows 11
* Safely manage BitLocker during partition modifications
* Resolve conflicts between BitLocker and Ubuntu installer
* Securely store and verify recovery keys
* Re-enable encryption after successful dual-boot setup

---

## Initial Encryption State

After Windows installation, device encryption was automatically enabled. The system began encrypting the primary volume in the background.

### Observations:

* Encryption status showed **“in progress”**
* System remained usable during encryption
* Recovery key was generated and associated with the user’s Microsoft account

---

## BitLocker Behavior During Installation

When attempting to install Ubuntu alongside Windows, the installer detected that the Windows volume was encrypted.

### Result:

* Ubuntu installer blocked partition changes
* Installation could not proceed
* Prompt required returning to Windows

---

## Attempted Mitigation: Suspend BitLocker

An initial attempt was made to suspend BitLocker protection.

### Process:

* Accessed BitLocker management settings
* Selected **Suspend protection**
* Rebooted system into Ubuntu installer

### Outcome:

* Suspension did not persist across reboot
* BitLocker automatically resumed protection
* Installer continued to block partition modifications

---

## Root Cause

BitLocker integrates with the system’s Trusted Platform Module (TPM) and secure boot chain. Changes in boot flow—such as switching to a USB installer—can cause BitLocker to re-enable protection automatically.

This behavior is designed to:

* Prevent unauthorized disk modifications
* Protect system integrity during boot changes

---

## Final Resolution: Full Decryption

To proceed with installation, BitLocker was fully disabled.

### Steps:

1. Opened BitLocker management settings
2. Selected **Turn off BitLocker**
3. Allowed the drive to fully decrypt

### Result:

* Disk returned to an unencrypted state
* Ubuntu installer was able to proceed without restrictions

---

## Post-Installation Re-Encryption

After successfully installing Ubuntu and verifying system stability:

* BitLocker was re-enabled
* Full disk encryption was applied using the **entire drive** option
* Encryption mode set to **XTS-AES**

---

## Recovery Key Management

Multiple recovery keys were generated during the process.

### Reasons:

* Initial encryption setup
* Re-enabling BitLocker after decryption
* Changes to boot configuration (GRUB installation)

### Key Storage Location:

Recovery keys were stored in the associated Microsoft account:
https://account.microsoft.com/devices/recoverykey

---

## Key Identification

Each recovery key includes a **Key ID**. When prompted during boot:

* The system displays a Key ID
* The corresponding recovery key must be selected from stored keys

---

## Important Considerations

### Multiple Recovery Keys

Having multiple keys is expected after significant system changes. All keys should be retained.

### Dual-Boot Interaction

The introduction of a secondary bootloader (GRUB) can occasionally trigger BitLocker recovery prompts due to changes in the boot chain.

### Recovery Preparedness

Loss of the recovery key results in permanent loss of access to encrypted data. Secure backup of all keys is critical.

---

## Security Implications

BitLocker provided:

* Protection against offline data access
* Defense against physical device compromise
* Secure storage of sensitive data

However, encryption must be carefully managed when:

* Modifying partitions
* Installing additional operating systems
* Altering boot configuration

---

## Outcome

BitLocker was successfully:

* Managed during installation
* Temporarily disabled to allow disk changes
* Re-enabled after system stabilization

The system now maintains:

* Full disk encryption on Windows
* Functional dual-boot configuration
* Verified recovery key access

---

## Lessons Learned

* BitLocker can block Linux installations when active
* Suspension of protection may not persist across reboot
* Full decryption is sometimes required for safe disk modification
* Recovery key management is essential for system access
* Bootloader changes can impact encryption behavior
