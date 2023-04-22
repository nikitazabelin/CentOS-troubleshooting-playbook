# CentOS-troubleshooting-playbook
CentOS-troubleshooting-playbook


Disk space full error
File system corruption
Incorrect or missing entries in the fstab file
Permission denied errors when changing directories or accessing files
Permission denied errors when trying to execute a command or run a script
Errors when creating symbolic or hard links
System running out of memory
Inability to run certain commands or programs
Unexpected system reboots and process restarts
Inability to obtain an IP address or connect to a network
Network connectivity issues (e.g., DNS resolution failure, firewall blocking traffic)
Permission issues (e.g., unable to modify or delete files, unable to execute certain commands)
Service management issues (e.g., unable to start, stop, or restart services)
Package management issues (e.g., dependencies not resolved, package installation failure)
System performance issues (e.g., high CPU or memory usage, slow disk I/O)
SELinux-related permission denied errors
Boot issues (e.g., booting into emergency mode, kernel panic)
HTTP error 403: forbidden yum occurs when we try to install a package using yum

<details>
<summary>Disk space full error</summary>

## Introduction
When the disk space on your CentOS system is full, you may encounter errors when trying to write to or access files on the disk. This can cause your system to slow down or even crash, and it can also prevent you from installing or updating software packages.

In this guide, we'll show you how to identify when your disk space is running low, and how to free up disk space so that your system can function properly.

## Identifying the Problem
The first step in troubleshooting disk space issues is to identify whether this is the cause of the problem you're encountering. Here are some common signs that your disk space is running low:

- You receive error messages indicating that there is no space left on the disk.
- Your system runs slowly or freezes up, especially when trying to access or write to files.
- You're unable to install or update software packages due to insufficient disk space.

To check the available disk space on your CentOS system, you can use the df command:

```
df -h
``` 

This will display the disk usage information for all mounted file systems, including the amount of free space available.

If the output shows that your disk is almost full or completely full, you'll need to free up some space in order to resolve the issue.


## Freeing Up Disk Space
There are several ways to free up disk space on a CentOS system. Here are some common methods:

### 1. Clean up log files
Log files can take up a lot of disk space over time, especially if they're not rotated or deleted regularly. You can use the logrotate command to manage log files on your system:

```
sudo logrotate -f /etc/logrotate.conf
```
This will force logrotate to run and clean up any old log files.

### 2. Delete temporary files
Temporary files can also consume a lot of disk space. You can use the tmpwatch command to automatically delete files in the system's temporary directories that are older than a certain number of days:

```
sudo tmpwatch 7 /tmp
sudo tmpwatch 7 /var/tmp
```
This will remove any files in the /tmp and /var/tmp directories that are more than 7 days old.

### 3. Uninstall unused software and other big files
Uninstalling software that you no longer need can also free up disk space. You can use the yum package manager to remove packages that you no longer need:

```
sudo yum remove package-name
```
Replace package-name with the name of the package that you want to remove.

You can also use these commands to find big files and remove them if it is possible
```
find / -mount -size +8096 -ls
find / -mount -name core -ls
du -sh /* (repeat for subsequent dirs on /)
```

### 4. Clear the YUM cache
The yum package manager caches downloaded packages in order to speed up future installations. However, this cache can consume a significant amount of disk space over time. You can clear the YUM cache by running the following command:

```
sudo yum clean all
```
### 5. Resize the disk partition
If none of the above methods work or if you need more space than you can free up, you can resize the disk partition to increase its capacity. However, this process can be risky and should only be attempted by experienced users.

### Conclusion
By following the above steps, you should be able to free up disk space on your CentOS system and resolve any disk space-related issues that you may encounter. If you continue to experience issues after trying these steps, it's recommended to seek help from a qualified Linux administrator.

</details>
<details>
<summary>File system corruption</summary>

## Introduction
File system corruption can occur on your CentOS system due to various reasons such as power failure, hardware issues, software bugs, or even malware attacks. This can cause data loss or make it difficult to access files and directories on the file system. In this guide, we will go through the steps to troubleshoot and resolve file system corruption issues on CentOS.

## Understanding the Issue
When your file system is corrupt, you may encounter one or more of the following symptoms:

- Unable to access files or directories on the file system
- Unexpected system crashes or hangs
- Applications or services failing to start or behaving abnormally
- Unusually slow performance or disk activity
- Error messages indicating file system corruption or integrity issues
- If you notice any of these symptoms, there's a good chance that your file system is corrupt and needs to be fixed.

## Troubleshooting Steps
Here are the steps you can follow to troubleshoot and fix file system corruption issues on CentOS:

### 1. Check Disk Space
Before you begin, make sure that your disk has enough free space. A full disk can cause file system corruption, so ensure that you have enough free space to work with.

You can check the disk usage on your system by running the following command:

```
df -h
```

This will show you the disk usage in human-readable format. Look for any file system that has a high usage percentage or is at 100% capacity. If you find any such file system, you may need to delete unnecessary files or expand the file system to free up space.

### 2. Run File System Check
Next, you can run a file system check to detect and repair any file system errors. CentOS uses the fsck utility for file system checks.

To run a file system check on your root file system, boot your system into recovery mode and select the option to run a file system check. Alternatively, you can run the following command to check the file system when the system is running:

```
sudo fsck -f /dev/sdaX
```
Replace /dev/sdaX with the device file of the file system you want to check. This will run a file system check and attempt to fix any errors it finds.

### 3. Restore from Backup
If the file system check doesn't resolve the issue, and you have a backup of your system, you can restore the file system from the backup. This will help you recover your data and get your system up and running again.

### 4. Reinstall the Operating System
If none of the above steps work, and you don't have a backup, you may need to reinstall the operating system. This will wipe your system and install a fresh copy of CentOS. Remember to backup your data before proceeding with a reinstallation.

### Conclusion
File system corruption can cause data loss and system instability, but following the steps in this guide can help you troubleshoot and fix the issue on your CentOS system. Remember to regularly backup your data to avoid losing important files in case of any future file system corruption issues.
</details>

<details>
<summary>Incorrect or missing entries in the fstab file</summary>

## Introduction
The fstab file is a configuration file that defines how file systems are mounted and accessed in your CentOS system. If there are incorrect or missing entries in the fstab file, you may encounter issues with file system mounting and access. In this guide, we will go through the steps to troubleshoot and fix incorrect or missing entries in the fstab file in CentOS.

## Understanding the Issue
When there are incorrect or missing entries in the fstab file, you may encounter one or more of the following symptoms:

- Unable to mount file systems on boot
- Unable to access file systems or directories
- Incorrect file system permissions or ownership
- Error messages indicating fstab file issues
If you notice any of these symptoms, there's a good chance that your fstab file has incorrect or missing entries and needs to be fixed.

## Troubleshooting Steps
Here are the steps you can follow to troubleshoot and fix incorrect or missing entries in the fstab file in CentOS:

### 1. Check fstab File
The first step is to check the fstab file for any incorrect or missing entries. You can do this by running the following command:

```
cat /etc/fstab
```
This will show you the contents of the fstab file. Look for any file system entries that are incorrect or missing.

### 2. Correct fstab Entries
Once you've identified any incorrect or missing entries in the fstab file, you can correct them by editing the fstab file. You can edit the fstab file using a text editor such as nano or vi.

To edit the fstab file using nano, run the following command:

```
sudo nano /etc/fstab
```
This will open the fstab file in nano. Make the necessary changes to the file and save the changes by pressing Ctrl+X, followed by Y, and then Enter.

To edit the fstab file using vi, run the following command:

```
sudo vi /etc/fstab
```
This will open the fstab file in vi. Use the arrow keys to navigate to the line you want to edit, make the necessary changes, and save the changes by typing :wq and then pressing Enter.

### 3. Test File System Mounting
Once you've corrected the entries in the fstab file, you can test the file system mounting by running the following command:

```
sudo mount -a
```
This will attempt to mount all file systems specified in the fstab file. If there are any errors, it will show you the error messages, which you can use to further troubleshoot the issue.

### 4. Reboot the System
After making changes to the fstab file, it's a good idea to reboot the system to ensure that the changes are applied correctly. You can do this by running the following command:

```
sudo reboot
```
## Conclusion
Incorrect or missing entries in the fstab file can cause issues with file system mounting and access, but following the steps in this guide can help you troubleshoot and fix the issue on your CentOS system. Remember to take a backup of the fstab file before making any changes to it, so that you can revert to the original file if needed.

</details>


<details>
<summary>Permission denied errors when changing directories or accessing files</summary>

If you encounter "Permission denied" errors when changing directories or accessing files in CentOS, it may be due to incorrect file permissions or ownership settings. This issue can be caused by a number of reasons, including user error, incorrect configuration, or system issues.

## Symptoms
- You are unable to change directories to a specific folder or access a file, and you receive a "Permission denied" error message.
- When trying to run a script, you receive a "Permission denied" error message.
- You are unable to create, modify, or delete files in a specific folder, and you receive a "Permission denied" error message.
## Causes
- Incorrect file permissions or ownership settings on the affected file or directory.
- The user trying to access the file or directory does not have the necessary permissions to do so.
- The file or directory is owned by a different user or group.
- The file or directory is located on a file system that is mounted with the "noexec" or "nodev" option.
## Solutions
1. Check the file permissions and ownership: Use the ls -l command to view the permissions and ownership of the file or directory. Make sure that the user or group trying to access the file has the necessary permissions. Use the chown and chmod commands to change the ownership and permissions of the file or directory, respectively.

2. Check the user permissions: Ensure that the user has the necessary permissions to access the file or directory. If not, add the user to the appropriate group or change the ownership or permissions of the file or directory.

3. Check the mount options: If the file or directory is located on a file system that is mounted with the "noexec" or "nodev" option, remount the file system with the appropriate options. Use the mount command to view the current mount options and the remount command to change the options.

4. Check for file system errors: Use the fsck command to check for any file system errors that may be causing the "Permission denied" errors.

5. Check for SELinux issues: If SELinux is enabled on your system, it may be blocking access to the file or directory. Use the sestatus command to check the SELinux status, and use the setenforce command to temporarily disable SELinux to see if it is the cause of the issue.

## Conclusion
"Permission denied" errors when changing directories or accessing files in CentOS can be frustrating, but they are usually caused by incorrect file permissions or ownership settings. By following the troubleshooting steps above, you should be able to identify and resolve the issue.

</details>


<details>
<summary>Permission denied errors when trying to execute a command or run a script</summary>

If you encounter "Permission denied" errors when trying to execute a command or run a script in CentOS, it may be due to incorrect file permissions or ownership settings. This issue can be caused by a number of reasons, including user error, incorrect configuration, or system issues.

## Symptoms
- When trying to execute a command or run a script, you receive a "Permission denied" error message.
- You are unable to change the permissions of the script to make it executable.
- When trying to execute a command or run a script as root, you receive a "Permission denied" error message.
## Causes
- Incorrect file permissions or ownership settings on the script or command file.
- The user trying to execute the script or command does not have the necessary permissions to do so.
- The file or directory is located on a file system that is mounted with the "noexec" or "nodev" option.
## Solutions
1. Check the file permissions and ownership: Use the ```ls -l``` command to view the permissions and ownership of the file. Make sure that the user or group trying to execute the file has the necessary permissions. Use the ```chown``` and ```chmod``` commands to change the ownership and permissions of the file, respectively.

2. Check the user permissions: Ensure that the user has the necessary permissions to execute the file. If not, add the user to the appropriate group or change the ownership or permissions of the file.

3. Check the ```mount``` options: If the file or directory is located on a file system that is mounted with the "noexec" or "nodev" option, ```remount``` the file system with the appropriate options. Use the mount command to view the current mount options and the remount command to change the options.

4. Check for file system errors: Use the ```fsck``` command to check for any file system errors that may be causing the "Permission denied" errors.

5. Check for SELinux issues: If SELinux is enabled on your system, it may be blocking access to the file or directory. Use the ```sestatus``` command to check the SELinux status, and use the setenforce command to temporarily disable SELinux to see if it is the cause of the issue.

6. Check for file system corruption: If none of the above solutions work, it is possible that there is file system corruption on your system. Use the ```fsck``` command to check for file system errors, and use the appropriate tool to fix the errors.

## Conclusion
"Permission denied" errors when trying to execute a command or run a script in CentOS can be frustrating, but they are usually caused by incorrect file permissions or ownership settings. By following the troubleshooting steps above, you should be able to identify and resolve the issue.

</details>
<details>
<summary>Errors when creating symbolic or hard links</summary>

## Issue description
When trying to create a symbolic or hard link to a file or directory, the following error message is displayed: ln: failed to create symbolic link/hard link: Permission denied.

## Possible causes
- Insufficient permissions to create the link.
- The file or directory you are trying to link to does not exist.
- The file system is mounted as read-only.
## Solution
Follow the steps below to troubleshoot and fix this issue:

### 1. Verify the existence of the file or directory
Before creating a link, ensure that the file or directory you are linking to exists. You can do this by running the following command:

```
ls -l /path/to/file_or_directory
```
If the file or directory does not exist, create it using the appropriate command.

### 2. Check the file system permissions
Make sure you have sufficient permissions to create a link. You can use the ```ls -l``` command to check the permissions of the file or directory you are linking to.

If you do not have the necessary permissions, use the chmod command to change the permissions of the file or directory. For example, to give write permissions to the file owner, run:

```
chmod u+w /path/to/file_or_directory
```
### 3. Check if the file system is mounted as read-only
If the file system is mounted as read-only, you will not be able to create a link. You can check if the file system is mounted as read-only by running the following command:

```
mount | grep " / "
```
Look for the output that contains ro (read-only) in the options column.

To remount the file system as read-write, run the following command:

```
mount -o remount,rw /
```
Replace / with the mount point of the file system.

### 4. Check the file system for errors
If the above steps do not resolve the issue, check the file system for errors. You can do this by running the following command:

```
fsck /dev/sdaX
```
Replace /dev/sdaX with the appropriate partition device.

### 5. Create the link
After verifying the file or directory exists, you have sufficient permissions, and the file system is mounted as read-write, you can create the link using the appropriate command. For example:

```
ln -s /path/to/file_or_directory /path/to/link
```
Replace /path/to/file_or_directory with the path to the file or directory you want to link to, and /path/to/link with the path to the link you want to create.

### Conclusion
By following the above steps, you should be able to troubleshoot and fix the issue of errors when creating symbolic or hard links on CentOS.
</details>
<details>
<summary>System running out of memory</summary>

Sometimes, a system running CentOS may experience issues related to running out of memory. This can cause the system to become slow, freeze, or even crash. In this guide, we will cover how to troubleshoot this issue and resolve it on a CentOS system.

## Identifying the Issue
If your CentOS system is running out of memory, you may notice the following symptoms:

- The system is running very slowly
- The system freezes or crashes
- You receive error messages related to lack of memory when trying to run applications or perform certain tasks
## Checking Memory Usage
The first step in troubleshooting a memory issue is to check the memory usage on your system. You can do this by running the following command in the terminal:

```
free -m
```
This will show you the total amount of memory on your system, as well as how much is currently in use and how much is free.

## Checking for Memory Leaks
If your system is running out of memory due to a memory leak, you will need to identify the process or application that is causing the leak. You can do this by using the top command:

```
top
```
This will show you a list of processes currently running on your system, sorted by the amount of memory they are using. If you notice a process that is using an unusually large amount of memory, it may be causing the memory leak.

## Resolving the Issue
There are several steps you can take to resolve a system running out of memory issue:

### 1. Close Unnecessary Applications
The first step is to close any applications or processes that are not necessary. This will free up memory for other applications and may resolve the issue.

### 2. Increase Swap Space
If your system is still running out of memory after closing unnecessary applications, you may need to increase the swap space. You can do this by following these steps:

Check the current swap space on your system by running the following command:

```
swapon --show
```
If the output shows that there is no swap space, you will need to create a new swap file:

```
sudo fallocate -l [size]G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```
Replace [size] with the desired size of the swap file in GB.

If the output shows that there is already a swap partition, you can increase the size of the existing partition by using the dd command:

```
sudo dd if=/dev/zero of=/swapfile bs=1G count=[size] conv=notrunc
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```
Replace [size] with the desired increase in size in GB.

### 3. Upgrade Memory
If your system is still running out of memory after increasing the swap space, you may need to upgrade the memory on your system.

## Conclusion
A system running out of memory can be a frustrating issue to deal with, but by following these steps, you should be able to identify the cause of the issue and resolve it on your CentOS system.

</details>

<details>
<summary>Inability to run certain commands or programs</summary>

</details>

<details>
<summary>Unexpected system reboots and process restarts</summary>

</details>
<details>
<summary>Inability to obtain an IP address or connect to a network</summary>

</details>

<details>
<summary>Network connectivity issues (e.g., DNS resolution failure, firewall blocking traffic)</summary>

</details>

<details>
<summary>Permission issues (e.g., unable to modify or delete files, unable to execute certain commands)</summary>

</details>

<details>
<summary>Service management issues (e.g., unable to start, stop, or restart services)</summary>

</details>

<details>
<summary>Package management issues (e.g., dependencies not resolved, package installation failure)</summary>

</details>

<details>
<summary>System performance issues (e.g., high CPU or memory usage, slow disk I/O)</summary>

</details>

<details>
<summary>SELinux-related permission denied errors</summary>


<details>
<summary>Boot issues (e.g., booting into emergency mode, kernel panic)</summary>



<details>
<summary>HTTP error 403: forbidden yum occurs when we try to install a package using yum</summary>

</details>
