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
11. **Resize the filesystem:**
    ```bash
    resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
    ``` 
12. **Remount or reboot to apply changes:**
    ```bash
    mount -o remount /dev/mapper/ubuntu--vg-ubuntu--lv
    OR
    reboot
    ```  
13. **Check disk space:**
    ```bash
    df -mh
    ```
## Root Partition Management
These commands are specifically for managing the root partition.
1. **Display logical volume details:**
    ```bash
    lvdisplay
    ```
2. **List block devices:**
    ```bash
    lsblk
    ```
3. **Check disk space usage:**
    ```bash
    df -mh
    ```
4. **Display physical volumes:**
    ```bash
    pvs
    ```
5. **Install required tools:**
    ```bash
    apt install cloud-guest-utils
    ```
6. **DGrow the partition:**
    ```bash
    growpart /dev/sda 3
    ```
7. **Resize the physical volume:**
    ```bash
    pvresize /dev/sda3
    ```
8. **Display volume groups:**
    ```bash
    vgs
    ```
9. **Extend the logical volume and resize filesystem:**
    ```bash
    lvextend -r -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
    ```
## Disk Scanning
Use the following commands to scan for newly attached disks or devices:
1. **DScan SCSI hosts:**
    ```bash
    for host in $(ls /sys/class/scsi_host); do
        echo ${host}
        echo "- - -" > /sys/class/scsi_host/${host}/scan
    done
    ```
2. **Rescan SCSI devices:**
    ```bash
    for host in $(ls /sys/class/scsi_device); do
        echo ${host}
        echo "1" > /sys/class/scsi_device/${host}/device/rescan
    done
    ```

## Managing /sdb Partition
Use these commands to manage the /sdb partition:
1. **Display partition information:**
    ```bash
    parted -l
    ```
2. **Display physical volume details:**
    ```bash
    pvs
    ```
3. **Resize the physical volume:**
    ```bash
    pvresize /dev/sdb
    ```
4. **Display updated physical volume details:**
    ```bash
    pvs
    ```
5. **Extend the logical volume and resize filesystem:**
    ```bash
    lvextend -r -l +100%FREE /dev/OS/home
    ```
## Notes
- Ensure you have proper permissions (root or sudo access) before running these commands.
- Back up critical data before performing LVM operations or resizing partitions.
- Verify the system and filesystem compatibility with LVM commands.
