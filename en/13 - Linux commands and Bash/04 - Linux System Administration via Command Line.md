
# Linux System Administration via Command Line

This course covers essential Linux system administration tasks through the command line, empowering you to manage users, processes, storage, networking, and more. By mastering these commands, you'll be able to perform routine system maintenance and troubleshooting efficiently.

## Table of Contents
1. [Managing Users and Groups](#managing-users-and-groups)
2. [System Processes and Process Management](#system-processes-and-process-management)
3. [Memory and Resource Monitoring](#memory-and-resource-monitoring)
4. [System Log Files and Monitoring](#system-log-files-and-monitoring)
5. [Disk and File System Management](#disk-and-file-system-management)
6. [Package Management and Software Installation](#package-management-and-software-installation)
7. [Networking Commands and Tools](#networking-commands-and-tools)
8. [Managing Firewall Rules with iptables](#managing-firewall-rules-with-iptables)
9. [System Shutdown, Reboot, and Power Management](#system-shutdown-reboot-and-power-management)
10. [Working with Systemd Services and Unit Files](#working-with-systemd-services-and-unit-files)

## 1. Managing Users and Groups
- **Definition**: Linux provides commands to manage users and groups, enabling the setup of access control and permissions.
- **Example**:
  - **Create User**:
    ```bash
    useradd newuser
    passwd newuser
    ```
  - **Create Group**:
    ```bash
    groupadd newgroup
    ```
- **Explanation**: `useradd` creates a new user, `passwd` sets the password, and `groupadd` creates a new group.

## 2. System Processes and Process Management
- **Definition**: Processes represent running programs, and Linux provides tools to manage their status, prioritization, and termination.
- **Example**:
  - **View Processes**:
    ```bash
    ps aux
    ```
  - **Kill Process**:
    ```bash
    kill -9 PID
    ```
  - **Set Process Priority**:
    ```bash
    nice -n 10 command
    ```
- **Explanation**: `ps` shows processes, `kill` terminates processes by PID, and `nice` adjusts process priority.

## 3. Memory and Resource Monitoring
- **Definition**: Monitoring memory and system resources is crucial for diagnosing performance issues.
- **Example**:
  - **Free Memory**:
    ```bash
    free -h
    ```
  - **Disk Usage**:
    ```bash
    df -h
    ```
  - **Disk Space Usage**:
    ```bash
    du -sh /path/to/dir
    ```
- **Explanation**: `free` shows memory usage, `df` displays disk space usage, and `du` shows the disk usage of a specific directory.

## 4. System Log Files and Monitoring
- **Definition**: System logs capture a history of events and errors, useful for debugging and system health checks.
- **Example**:
  - **View System Logs**:
    ```bash
    tail -f /var/log/syslog
    ```
  - **Journal Logs**:
    ```bash
    journalctl
    ```
- **Explanation**: `tail -f` displays the most recent logs, and `journalctl` is used for accessing logs managed by `systemd`.

## 5. Disk and File System Management
- **Definition**: Disk and file system management involves partitioning, formatting, and mounting storage devices.
- **Example**:
  - **Create Partition**:
    ```bash
    fdisk /dev/sda
    ```
  - **Format Disk**:
    ```bash
    mkfs.ext4 /dev/sdb1
    ```
  - **Mount Disk**:
    ```bash
    mount /dev/sdb1 /mnt
    ```
- **Explanation**: `fdisk` partitions a disk, `mkfs` formats it, and `mount` attaches the filesystem to a directory.

## 6. Package Management and Software Installation
- **Definition**: Linux distributions manage software packages using package managers like `apt` (Debian-based) and `yum` (RHEL-based).
- **Example**:
  - **Install Package** (APT):
    ```bash
    sudo apt update
    sudo apt install package_name
    ```
  - **Install Package** (YUM):
    ```bash
    sudo yum install package_name
    ```
  - **Remove Package**:
    ```bash
    sudo apt remove package_name
    ```
- **Explanation**: `apt` and `yum` allow for installing and removing software packages across different distributions.

## 7. Networking Commands and Tools
- **Definition**: Networking commands help in configuring network interfaces, checking connectivity, and troubleshooting.
- **Example**:
  - **View Network Configuration**:
    ```bash
    ifconfig
    ```
  - **Check Network Status**:
    ```bash
    ip a
    ```
  - **Ping Host**:
    ```bash
    ping google.com
    ```
  - **Download File**:
    ```bash
    wget https://example.com/file
    ```
- **Explanation**: `ifconfig` shows network interfaces, `ping` checks connectivity, and `wget` downloads files from the web.

## 8. Managing Firewall Rules with iptables
- **Definition**: `iptables` is used to configure and manage firewall rules to secure the system from unwanted traffic.
- **Example**:
  - **List Rules**:
    ```bash
    sudo iptables -L
    ```
  - **Allow Incoming SSH**:
    ```bash
    sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    ```
- **Explanation**: `iptables` helps configure firewall rules for network security. Use `-A` to add rules and `-L` to list them.

## 9. System Shutdown, Reboot, and Power Management
- **Definition**: Linux provides commands to safely shut down, restart, and manage power settings.
- **Example**:
  - **Shutdown**:
    ```bash
    sudo shutdown now
    ```
  - **Reboot**:
    ```bash
    sudo reboot
    ```
  - **Power Off**:
    ```bash
    sudo poweroff
    ```
- **Explanation**: `shutdown`, `reboot`, and `poweroff` manage system power and state transitions.

## 10. Working with Systemd Services and Unit Files
- **Definition**: `systemd` is the default service manager on many Linux distributions, used to manage services and systemd unit files.
- **Example**:
  - **Start Service**:
    ```bash
    sudo systemctl start service_name
    ```
  - **Enable Service**:
    ```bash
    sudo systemctl enable service_name
    ```
  - **Check Service Status**:
    ```bash
    sudo systemctl status service_name
    ```
- **Explanation**: `systemctl` is the command-line tool used to interact with `systemd` services.

## Conclusion

### Key Takeaways:
1. Managing users and groups ensures proper access control and security.
2. Understanding process management and monitoring tools is vital for troubleshooting system performance.
3. Disk and file system management tools allow for efficient storage organization and maintenance.
4. Package management helps automate the installation, update, and removal of software on Linux.
5. Network tools and firewall configuration ensure secure and reliable communication across systems.

### Practical Exercise:
1. Write a script that adds a new user, creates a group, and assigns the user to the group.
2. Use `top` or `htop` to monitor system resources, then kill a resource-intensive process.
3. Set up a cron job that automatically checks disk usage and sends an email if usage exceeds a certain threshold.
4. Create a firewall rule using `iptables` that blocks all incoming traffic except SSH.
