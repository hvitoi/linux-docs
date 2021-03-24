# Encryption

- Hard Drive encryption

  - `MacOS`: FileVault
  - `Windows`: BitLocker
  - `Linux`: LUKS (Linux Hard Disk Encryption)

- Other multi-platform tools
  - VeraCrypt

## LUKS / Cryptsetup

- `Cryptsetup` is a utility used to set up disk encryption based on the `DMCrypt` kernel module
- Because `dm-crypt` is a `block-level encryption layer`, it only encrypts whole block devices, e.g. partitions and loop devices
