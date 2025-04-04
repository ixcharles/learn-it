
# Introduction to Linux Commands and Bash Shell Basics

This course provides an essential overview of Linux commands and Bash shell basics, offering foundational knowledge for working with the Linux terminal. Mastery of these commands is critical for any developer working on Linux-based systems.

## Table of Contents
1. [Introduction to the Linux Command Line](#introduction-to-the-linux-command-line)
2. [Navigating the Filesystem](#navigating-the-filesystem)
3. [Understanding and Managing File Permissions](#understanding-and-managing-file-permissions)
4. [Working with Directories](#working-with-directories)
5. [Viewing and Manipulating File Content](#viewing-and-manipulating-file-content)
6. [Introduction to File Wildcards and Globbing](#introduction-to-file-wildcards-and-globbing)
7. [Basic File Operations](#basic-file-operations)
8. [Redirection and Pipes](#redirection-and-pipes)
9. [Understanding Environment Variables](#understanding-environment-variables)
10. [Basic Text Editing with Nano and Vim](#basic-text-editing-with-nano-and-vim)

## 1. Introduction to the Linux Command Line
- **Definition**: The command line in Linux allows users to interact with the operating system through text-based commands.
- **Example**: Opening a terminal window and typing `ls` to list files.
- **Explanation**: The terminal is a powerful interface for managing files, running applications, and configuring system settings.

## 2. Navigating the Filesystem
- **Definition**: The command line allows navigation through the directory structure using commands like `cd`, `pwd`, and `ls`.
- **Example**: 
  - `cd /home/user/Documents` (change directory)
  - `pwd` (print current working directory)
  - `ls` (list files in the current directory)
- **Explanation**: These commands enable efficient movement between directories and viewing the contents of your file system.

## 3. Understanding and Managing File Permissions
- **Definition**: Linux files and directories have permissions for the owner, group, and others to read, write, and execute.
- **Example**: 
  - `chmod 755 file.txt` (set permissions to rwx for owner, rx for group and others)
  - `chown user:group file.txt` (change file ownership)
  - `chgrp group file.txt` (change file group)
- **Explanation**: Permissions control access to files and directories, ensuring security and proper access control.

## 4. Working with Directories
- **Definition**: Directories organize files in Linux, and commands like `mkdir`, `rmdir`, and `ln` help manage them.
- **Example**:
  - `mkdir new_directory` (create a directory)
  - `rmdir empty_directory` (remove an empty directory)
  - `ln -s /path/to/file link_name` (create a symbolic link)
- **Explanation**: Directories help structure files, and symbolic links create shortcuts to files or directories.

## 5. Viewing and Manipulating File Content
- **Definition**: Commands like `cat`, `more`, `less`, `head`, and `tail` allow users to view and manipulate file contents.
- **Example**:
  - `cat file.txt` (display entire file content)
  - `head file.txt` (show the first 10 lines of a file)
  - `tail file.txt` (show the last 10 lines of a file)
- **Explanation**: These commands are essential for quickly inspecting and navigating through files without opening an editor.

## 6. Introduction to File Wildcards and Globbing
- **Definition**: Wildcards allow users to match patterns in filenames for batch processing.
- **Example**: 
  - `ls *.txt` (list all `.txt` files in the current directory)
  - `rm *.log` (remove all `.log` files)
- **Explanation**: Wildcards expand flexibility when working with multiple files at once, saving time and effort.

## 7. Basic File Operations
- **Definition**: Linux provides several commands to manage files, such as copying, moving, removing, and creating files.
- **Example**:
  - `cp file1.txt file2.txt` (copy file1.txt to file2.txt)
  - `mv file1.txt /path/to/new/location` (move file1.txt to a new directory)
  - `rm file.txt` (delete file.txt)
  - `touch newfile.txt` (create an empty file)
- **Explanation**: These basic file operations are the foundation for managing files in Linux.

## 8. Redirection and Pipes
- **Definition**: Redirection and pipes allow users to control the flow of input and output between commands.
- **Example**:
  - `ls > file_list.txt` (redirect output of `ls` to a file)
  - `cat file.txt | grep "pattern"` (search for a pattern in the file using pipe)
- **Explanation**: Redirection (`>`, `<`) and pipes (`|`) enable powerful combinations of commands for advanced data processing.

## 9. Understanding Environment Variables
- **Definition**: Environment variables store system information and configuration settings.
- **Example**:
  - `echo $PATH` (display the system's PATH variable)
  - `export MY_VAR="value"` (set a custom environment variable)
- **Explanation**: These variables are crucial for configuring the system, and they influence how applications and scripts run.

## 10. Basic Text Editing with Nano and Vim
- **Definition**: Nano and Vim are text editors available in the terminal for creating and editing files.
- **Example**:
  - `nano file.txt` (open file in Nano editor)
  - `vim file.txt` (open file in Vim editor)
- **Explanation**: Nano is beginner-friendly, while Vim is a more advanced editor with powerful features for efficient editing.

## Conclusion

### Key Takeaways:
1. The Linux command line is a powerful tool for managing the system and automating tasks.
2. File navigation and manipulation are essential skills in the Linux environment.
3. Understanding file permissions and ownership is crucial for system security.
4. Mastering redirection, pipes, and environment variables can streamline workflows.
5. Familiarity with text editors like Nano and Vim is essential for efficient file editing.

### Practical Exercise:
1. Use the `cd`, `ls`, and `pwd` commands to navigate to various directories in your system.
2. Create a directory, set its permissions, and create a file inside it using `mkdir`, `chmod`, and `touch`.
3. Open a file using `nano` or `vim`, edit it, save, and close the editor.
4. Experiment with file redirection by saving the output of a command like `ls` to a file.
