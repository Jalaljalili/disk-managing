# LVM and Disk Management Commands

This guide provides an overview of commands for managing Logical Volume Management (LVM), extending disk space, and scanning disks.

---

## Table of Contents
- [LVM Management](#lvm-management)
- [Root Partition Management](#root-partition-management)
- [Disk Scanning](#disk-scanning)
- [Managing /sdb Partition](#managing-sdb-partition)

---

## LVM Management

The following commands are used for managing Logical Volume Management (LVM) operations such as creating physical volumes, extending volume groups, and resizing logical volumes.

1. **List block devices:**
   ```bash
   ls -l /dev/sd*

Displays details about block devices.

2. **Create a physical volume:**
   ```bash
    pvcreate /dev/sdb
    ```
    Initializes /dev/sdb as a physical volume for use in LVM.

    
