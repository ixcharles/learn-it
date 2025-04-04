
# Mastering Linux System Administration and Optimization

This course covers essential skills for advanced Linux system administration, including performance tuning, system services, disk management, resource control, high availability, and scaling with virtualization and automation.

## Table of Contents
1. [Understanding and Configuring System Services](#understanding-and-configuring-system-services)
2. [Performance Tuning for CPU, Memory, and Disk](#performance-tuning-for-cpu-memory-and-disk)
3. [File System and Disk Management](#file-system-and-disk-management)
4. [System Logging and Log Rotation](#system-logging-and-log-rotation)
5. [Kernel Configuration and Compilation](#kernel-configuration-and-compilation)
6. [Resource Management and Control](#resource-management-and-control)
7. [High Availability and Load Balancing in Linux](#high-availability-and-load-balancing-in-linux)
8. [Backup Strategies and Disaster Recovery Planning](#backup-strategies-and-disaster-recovery-planning)
9. [Scaling and Virtualization](#scaling-and-virtualization)
10. [Continuous Integration and Deployment in Linux](#continuous-integration-and-deployment-in-linux)

## 1. Understanding and Configuring System Services
- **Definition**: `systemd` manages services, startup processes, and system states in modern Linux distributions.
- **Example**:
  - Enable and start a service:
    ```bash
    sudo systemctl enable nginx
    sudo systemctl start nginx
    ```
- **Explanation**: `systemctl` controls system services, ensuring automatic startup and proper operation.

## 2. Performance Tuning for CPU, Memory, and Disk
- **Definition**: Optimizing CPU scheduling, memory management, and disk I/O enhances system performance.
- **Example**:
  - Adjust CPU governor for performance:
    ```bash
    echo "performance" | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    ```
- **Explanation**: This forces the CPU to run at maximum speed for improved performance.

## 3. File System and Disk Management
- **Definition**: Managing storage efficiently using RAID, LVM, and different file systems optimizes disk performance and reliability.
- **Example**:
  - Create and mount an LVM partition:
    ```bash
    sudo pvcreate /dev/sdb
    sudo vgcreate my_vg /dev/sdb
    sudo lvcreate -L 10G -n my_lv my_vg
    sudo mkfs.ext4 /dev/my_vg/my_lv
    ```
- **Explanation**: Logical Volume Management (LVM) allows flexible disk allocation and resizing.

## 4. System Logging and Log Rotation
- **Definition**: Log management tools (`journald`, `logrotate`) help monitor system activity and prevent excessive log file growth.
- **Example**:
  - View recent logs:
    ```bash
    journalctl -xe
    ```
  - Configure log rotation:
    ```bash
    sudo nano /etc/logrotate.d/nginx
    ```
- **Explanation**: `journalctl` shows system logs, while `logrotate` prevents logs from consuming too much space.

## 5. Kernel Configuration and Compilation
- **Definition**: Customizing the Linux kernel allows for performance enhancements and hardware optimizations.
- **Example**:
  - Download, configure, and compile a new kernel:
    ```bash
    wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.5.tar.xz
    tar -xf linux-6.5.tar.xz
    cd linux-6.5
    make menuconfig
    make -j$(nproc)
    sudo make modules_install && sudo make install
    ```
- **Explanation**: This process compiles a custom kernel for improved control over system performance and features.

## 6. Resource Management and Control
- **Definition**: `cgroups` and `systemd` allow fine-grained control of CPU, memory, and disk I/O per process.
- **Example**:
  - Limit CPU usage of a process:
    ```bash
    sudo cgcreate -g cpu:/limited
    echo 50000 | sudo tee /sys/fs/cgroup/cpu/limited/cpu.cfs_quota_us
    sudo cgexec -g cpu:limited /usr/bin/my_program
    ```
- **Explanation**: `cgroups` can restrict CPU, memory, and I/O usage to prevent system overloading.

## 7. High Availability and Load Balancing in Linux
- **Definition**: Techniques like clustering and load balancing improve uptime and distribute workloads efficiently.
- **Example**:
  - Set up HAProxy as a load balancer:
    ```bash
    sudo apt install haproxy
    sudo nano /etc/haproxy/haproxy.cfg
    ```
- **Explanation**: HAProxy evenly distributes traffic across multiple servers for improved availability.

## 8. Backup Strategies and Disaster Recovery Planning
- **Definition**: Implementing regular backups and disaster recovery ensures minimal data loss.
- **Example**:
  - Automate incremental backups:
    ```bash
    rsync -av --delete /home /backup/home
    ```
- **Explanation**: `rsync` efficiently backs up files while preserving permissions and timestamps.

## 9. Scaling and Virtualization
- **Definition**: Virtualization and containerization (Docker, LXC, KVM) allow for efficient resource usage and scalability.
- **Example**:
  - Launch a Docker container:
    ```bash
    docker run -d --name webserver -p 80:80 nginx
    ```
- **Explanation**: Containers enable lightweight, fast deployment of applications.

## 10. Continuous Integration and Deployment in Linux
- **Definition**: CI/CD pipelines automate software testing and deployment.
- **Example**:
  - Automate deployment with GitHub Actions:
    ```yaml
    name: Deploy
    on: push
    jobs:
      deploy:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2
          - run: ./deploy.sh
    ```
- **Explanation**: This ensures smooth and automated deployments whenever code changes.

## Conclusion

### Key Takeaways:
1. `systemd` simplifies service management, improving startup and reliability.
2. Performance tuning optimizes CPU, memory, and disk performance.
3. `LVM` and RAID provide flexible storage management.
4. Log rotation prevents excessive disk usage and helps maintain system performance.
5. `cgroups` and high availability tools ensure efficient resource control.
6. Virtualization and CI/CD streamline scalability and deployment.

### Practical Exercise:
1. Configure a system service using `systemctl` and ensure it starts at boot.
2. Optimize CPU and memory performance using `sysctl` parameters.
3. Set up and mount an LVM-based storage volume.
4. Implement log rotation for a specific service.
5. Deploy a simple web application using Docker and automate its deployment with a CI/CD pipeline.
