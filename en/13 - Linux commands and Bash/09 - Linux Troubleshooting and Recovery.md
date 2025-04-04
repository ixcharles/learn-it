
# Linux Troubleshooting and Recovery

This course covers essential techniques for diagnosing, recovering, and troubleshooting Linux systems. Learn how to resolve boot failures, recover lost files, fix corrupted filesystems, and restore system functionality efficiently.

## Table of Contents
1. [Basic System Recovery Concepts](#basic-system-recovery-concepts)
2. [Recovering a Corrupted Filesystem](#recovering-a-corrupted-filesystem)
3. [Recovering Lost Files and Directories](#recovering-lost-files-and-directories)
4. [Resolving Package Management Issues](#resolving-package-management-issues)
5. [Resolving Boot Issues](#resolving-boot-issues)
6. [Kernel Panic and Boot Troubleshooting](#kernel-panic-and-boot-troubleshooting)
7. [Advanced Networking Troubleshooting](#advanced-networking-troubleshooting)
8. [Resolving Performance Bottlenecks](#resolving-performance-bottlenecks)
9. [Analyzing Core Dumps and Debugging Applications](#analyzing-core-dumps-and-debugging-applications)
10. [Full System Recovery and Backup Strategies](#full-system-recovery-and-backup-strategies)

## 1. Basic System Recovery Concepts
- **Definition**: System recovery involves using tools like Live CDs or rescue modes to restore an unbootable or damaged Linux system.
- **Example**:
  - Boot into rescue mode:
    ```bash
    sudo systemctl rescue
    ```
- **Explanation**: Rescue mode allows system access when normal boot fails, enabling troubleshooting and recovery.

## 2. Recovering a Corrupted Filesystem
- **Definition**: Filesystem corruption can occur due to power failures or hardware issues, requiring tools like `fsck`.
- **Example**:
  - Check and repair filesystem:
    ```bash
    sudo fsck -y /dev/sda1
    ```
- **Explanation**: `fsck` scans and fixes errors on a filesystem, preventing data loss.

## 3. Recovering Lost Files and Directories
- **Definition**: Tools like `extundelete` and `TestDisk` help restore accidentally deleted files.
- **Example**:
  - Recover a deleted file from an ext4 partition:
    ```bash
    sudo extundelete /dev/sda1 --restore-all
    ```
- **Explanation**: `extundelete` scans a disk for recently deleted files and attempts recovery.

## 4. Resolving Package Management Issues
- **Definition**: Corrupt or broken package installations can cause system instability and need manual intervention.
- **Example**:
  - Fix broken packages in Debian-based systems:
    ```bash
    sudo dpkg --configure -a
    ```
- **Explanation**: This command attempts to reconfigure broken packages, ensuring a working system.

## 5. Resolving Boot Issues
- **Definition**: Problems with the bootloader (GRUB, LILO) can prevent Linux from booting.
- **Example**:
  - Reinstall GRUB:
    ```bash
    sudo grub-install /dev/sda
    sudo update-grub
    ```
- **Explanation**: This restores the GRUB bootloader, fixing boot issues caused by misconfigurations or corruption.

## 6. Kernel Panic and Boot Troubleshooting
- **Definition**: Kernel panics indicate serious system failures, often related to hardware, drivers, or kernel configurations.
- **Example**:
  - View the last kernel panic logs:
    ```bash
    journalctl -k -b -1
    ```
- **Explanation**: Kernel logs help identify the cause of crashes and determine corrective actions.

## 7. Advanced Networking Troubleshooting
- **Definition**: Diagnosing network issues involves checking firewalls, DNS, routing, and connectivity.
- **Example**:
  - Check network interface details:
    ```bash
    ip a
    ```
- **Explanation**: This command lists network interfaces and their status, helping diagnose connectivity problems.

## 8. Resolving Performance Bottlenecks
- **Definition**: High resource usage can slow down a system, requiring monitoring and optimization.
- **Example**:
  - Check CPU and memory usage:
    ```bash
    top
    ```
- **Explanation**: `top` provides real-time process monitoring to identify resource-intensive applications.

## 9. Analyzing Core Dumps and Debugging Applications
- **Definition**: Core dumps store program state at the time of a crash, aiding debugging.
- **Example**:
  - Analyze a core dump using `gdb`:
    ```bash
    gdb /path/to/executable core
    ```
- **Explanation**: `gdb` helps debug application crashes by analyzing memory and runtime errors.

## 10. Full System Recovery and Backup Strategies
- **Definition**: A robust backup strategy ensures data can be restored in case of failures.
- **Example**:
  - Create a full system backup with `tar`:
    ```bash
    tar -cvpzf /backup/system.tar.gz --exclude=/backup /
    ```
- **Explanation**: This command creates a compressed archive of the entire system, excluding the backup directory itself.

## Conclusion

### Key Takeaways:
1. Live CDs and rescue modes allow recovery of unbootable systems.
2. Filesystem checks (`fsck`) and recovery tools (`extundelete`, `TestDisk`) help restore lost or corrupted data.
3. Fixing package management issues can restore system functionality.
4. Troubleshooting bootloader problems is essential for resolving boot failures.
5. Core dumps and debugging tools help analyze system and application crashes.

### Practical Exercise:
1. Simulate a corrupted filesystem and attempt recovery using `fsck`.
2. Delete a test file and use `extundelete` or `TestDisk` to restore it.
3. Break and fix GRUB by manually reinstalling it.
4. Use `top` and `iotop` to analyze system performance and identify bottlenecks.
5. Generate a core dump and analyze it using `gdb`.
