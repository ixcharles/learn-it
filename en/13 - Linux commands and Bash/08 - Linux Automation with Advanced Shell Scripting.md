
# Linux Automation with Advanced Shell Scripting

This course focuses on automating complex tasks with advanced shell scripting techniques. Learn to streamline server setups, system monitoring, backups, and more using Bash scripts, and integrate them with other tools for maximum efficiency.

## Table of Contents
1. [Introduction to Shell Script Automation](#introduction-to-shell-script-automation)
2. [Writing Modular and Reusable Scripts](#writing-modular-and-reusable-scripts)
3. [Automating Server Setup and Configuration](#automating-server-setup-and-configuration)
4. [Handling File and Directory Backups in Scripts](#handling-file-and-directory-backups-in-scripts)
5. [Integrating Bash with Other Scripting Languages](#integrating-bash-with-other-scripting-languages)
6. [Creating and Using Bash Libraries](#creating-and-using-bash-libraries)
7. [Using Crontab for Scheduled Automation](#using-crontab-for-scheduled-automation)
8. [Automating Database Backups and Maintenance](#automating-database-backups-and-maintenance)
9. [Writing Complex Scripts for System Monitoring and Alerts](#writing-complex-scripts-for-system-monitoring-and-alerts)
10. [Version Control Integration in Bash Scripts](#version-control-integration-in-bash-scripts)

## 1. Introduction to Shell Script Automation
- **Definition**: Shell scripting allows for the automation of repetitive tasks, enabling efficiency and reliability in system administration.
- **Example**:
  - **Basic Script Example**:
    ```bash
    #!/bin/bash
    echo "Automating tasks with Bash scripts!"
    ```
- **Explanation**: Shell scripting can automate tasks such as file manipulation, system monitoring, and service management by executing commands automatically.

## 2. Writing Modular and Reusable Scripts
- **Definition**: Modular scripts are divided into reusable functions, making them more maintainable and scalable.
- **Example**:
  - **Function Example**:
    ```bash
    function backup() {
      cp $1 $2
      echo "Backup of $1 completed to $2"
    }
    backup /home/user/data /backup
    ```
- **Explanation**: By defining reusable functions like `backup()`, scripts become easier to manage and extend.

## 3. Automating Server Setup and Configuration
- **Definition**: Automation scripts can streamline the setup of servers, ensuring consistency and reducing the chance for manual errors.
- **Example**:
  - **Automate Package Installation**:
    ```bash
    #!/bin/bash
    apt update && apt install -y nginx vim
    systemctl start nginx
    ```
- **Explanation**: This script installs necessary packages and starts a service automatically during server provisioning.

## 4. Handling File and Directory Backups in Scripts
- **Definition**: Backup scripts help automate the process of creating backups of files and directories, ensuring data safety.
- **Example**:
  - **Simple Backup Script**:
    ```bash
    #!/bin/bash
    tar -czf /backup/$(date +\%F).tar.gz /home/user/data
    ```
- **Explanation**: The script creates a timestamped backup of the `/home/user/data` directory using `tar` for compression.

## 5. Integrating Bash with Other Scripting Languages (Python, Perl)
- **Definition**: Integrating Bash with languages like Python or Perl allows you to leverage the strengths of both: Bash for system tasks and Python/Perl for more complex logic.
- **Example**:
  - **Call Python Script from Bash**:
    ```bash
    #!/bin/bash
    python3 myscript.py
    ```
  - **Call Bash from Python**:
    ```python
    import subprocess
    subprocess.run(["bash", "myscript.sh"])
    ```
- **Explanation**: Bash can invoke Python or Perl scripts to perform advanced operations that are not feasible in pure shell scripting.

## 6. Creating and Using Bash Libraries
- **Definition**: Bash libraries consist of a collection of functions and utilities that can be reused across different scripts.
- **Example**:
  - **Create Library File (`lib.sh`)**:
    ```bash
    #!/bin/bash
    function print_date() {
      echo "Today's date: $(date)"
    }
    ```
  - **Include Library in Script**:
    ```bash
    #!/bin/bash
    source lib.sh
    print_date
    ```
- **Explanation**: Libraries allow code reuse and modularity. The `source` command is used to include external scripts.

## 7. Using Crontab for Scheduled Automation
- **Definition**: `cron` is used to schedule tasks to run automatically at specified intervals, which is essential for regular maintenance and monitoring.
- **Example**:
  - **Schedule Backup with Crontab**:
    ```bash
    crontab -e
    # Add the following line to run a backup script every day at 2 AM
    0 2 * * * /home/user/backup.sh
    ```
- **Explanation**: This sets up a scheduled job to automatically run the backup script every day at 2 AM.

## 8. Automating Database Backups and Maintenance
- **Definition**: Automating database backups ensures that data is regularly backed up without human intervention.
- **Example**:
  - **Automate MySQL Backup**:
    ```bash
    #!/bin/bash
    mysqldump -u user -p password dbname > /backup/dbname_$(date +\%F).sql
    ```
- **Explanation**: This script dumps the MySQL database into a `.sql` file, with the date appended to the filename for uniqueness.

## 9. Writing Complex Scripts for System Monitoring and Alerts
- **Definition**: Complex scripts can monitor system health (CPU, memory, disk, etc.) and send alerts based on conditions.
- **Example**:
  - **Monitor Disk Usage**:
    ```bash
    #!/bin/bash
    disk_usage=$(df / | grep / | awk '{ print $5 }' | sed 's/%//g')
    if [ $disk_usage -gt 90 ]; then
      echo "Warning: Disk usage is above 90%" | mail -s "Disk Alert" admin@example.com
    fi
    ```
- **Explanation**: This script checks disk usage and sends an email alert if it exceeds 90%.

## 10. Version Control Integration in Bash Scripts (Git)
- **Definition**: Integrating Git with Bash scripts helps maintain version control for automation scripts, enabling easy rollbacks and collaboration.
- **Example**:
  - **Add and Commit Changes to Git**:
    ```bash
    git add myscript.sh
    git commit -m "Updated backup script"
    git push origin main
    ```
- **Explanation**: By using Git, you can track changes to your scripts, collaborate with others, and ensure version history is maintained.

## Conclusion

### Key Takeaways:
1. Shell scripts can automate repetitive tasks, saving time and reducing human error.
2. Writing modular scripts improves code maintainability and scalability.
3. Tools like `cron` can schedule tasks for regular execution, automating system maintenance.
4. Integrating Bash with other scripting languages like Python or Perl expands your automation capabilities.
5. Version control, through Git, helps track changes to automation scripts and collaborate effectively.

### Practical Exercise:
1. Write a script to automate the installation of a software package and its dependencies.
2. Create a backup script that runs daily at a specific time and stores backups with timestamped filenames.
3. Automate system health monitoring (CPU, memory, disk) and send email alerts for abnormal conditions.
4. Develop a Bash script that integrates with a Python script for advanced data processing tasks.
5. Version control your automation scripts by pushing them to a Git repository and managing script updates. 
