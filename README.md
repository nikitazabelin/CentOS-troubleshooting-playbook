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
<details>
<summary>Incorrect or missing entries in the fstab file</summary>


</details>


<details>
<summary>Permission denied errors when changing directories or accessing files</summary>


</details>


<details>
<summary>Permission denied errors when trying to execute a command or run a script</summary>


</details>
<details>
<summary>Errors when creating symbolic or hard links</summary>

</details>
<details>
<summary>System running out of memory</summary>

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
