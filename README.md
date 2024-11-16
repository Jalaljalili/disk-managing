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

3. **Display physical volume information:**
    ```bash
    pvdisplay
    ```

4. **Display volume group information:**
    ```bash
    vgdisplay
    ```
5. **Extend an existing volume group:**
    ```bash
    vgextend ubuntu-vg /dev/sdb
    ```
6. **Display logical volume information:**
    ```bash
    lvdisplay
    ```
7. **Extend a logical volume:**
    ```bash
    lvextend -L +50G /dev/mapper/ubuntu--vg-ubuntu--lv
    ```
    Increases the size of the logical volume by 50GB.

8. **Check device mapper details:**
    ```bash
    ls -l /dev/dm*
    ```
9. **Get block device UUIDs:**
    ```bash
    blkid
    ```
10. **Check the filesystem for errors:**
    ```bash
    e2fsck /dev/mapper/ubuntu--vg-ubuntu--lv
    ```  
