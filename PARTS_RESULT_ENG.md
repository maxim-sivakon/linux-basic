# Report on the project "UNIX/Linux Operating Systems (Basic)"

Installing and updating the Linux system. Basics of administration.

## Part 1. Installing the OS

- Installed Ubuntu - checked the version using the command: `cat /etc/issue'
  ![linux](assets/images/part_1.png)

## Part 2. Creating a user

- Create a new user in the adm group: `sudo useradd -g adm gylbertk` and set a new password `sudo passwd gylbertk`

![linux](assets/images/part_2_1.png)


- Brought out the user: `cat /etc/passwd' - total:

![linux](assets/images/part_2_2.png)


- Or just find it: `grep -w '^gylbertk' /etc/passwd`

![linux](assets/images/part_2_3.png)


## Part 3. Configuring the OS network

- Set the name of the machine as gylbertk-1: `sudo hostnamectl set-hostname gylbertk-1`

![linux](assets/images/part_3_1.png)


- Set the time zone corresponding to my current location: `sudo timedatectl set-timezone Asia/Novosibirsk`

![linux](assets/images/part_3_2.png)

- Output the name of the network interfaces using the console command: `ifconfig -a`

![linux](assets/images/part_3_3.png)

----
- The lo interface is a virtual Internet interface by default in any Linux system and works at 127.0.0.1 and is designed to access your own computer!
----

![linux](assets/images/part_3_4.png)

- Received a list of the IP address of the device on which we work from the DHCP server

----
- DHCP is a Dynamic Host Configuration Protocol - a dynamic Host Configuration protocol!
----

- Identified and displayed the external ip address of the gateway (ip) and the internal IP address of the gateway, aka the default ip address (gw)

![linux](assets/images/part_3_5.png)


- Set static ip, gw, dns settings (used a public DNS server, for example 1.1.1.1 or 8.8.8.8) - used the command `sudo vim /etc/netplan/00-installer-config.yaml`

![linux](assets/images/part_3_6.png)


- Rebooted the `reboot` VM. Make sure that the static network settings (ip, gw, dns) correspond to those specified in the previous paragraph.

![linux](assets/images/part_3_7.png)


- Successfully pinged remote hosts 1.1.1.1 and ya.ru

![linux](assets/images/part_3_8.png)

## Part 4. OS Update

- Made an attempt to update the system with the command: `sudo apt upgrade`

![linux](assets/images/part_4_1.png)

## Part 5. Using the **sudo command**

----
- The sudo command ( substitute user and do, substitute user and execute) allows strictly defined users to execute specified programs with administrative privileges without entering the root superuser password. To be more precise, the sudo command allows you to execute programs on behalf of any user, but if the ID or name of this user is not specified, then it is assumed to be executed on behalf of the root superuser. Thus, using sudo allows you to execute privileged commands to ordinary users without having to enter the root superuser password. The list of users and the list of their rights in relation to the system resources can be configured optimally to ensure comfortable and safe operation. For example, the sudo command in Ubuntu Linux is used in a mode that allows you to perform any system administration tasks without interactive login under the root account.
----
- Changed the hostname of the OS on behalf of the user created in paragraph Part 2 (using sudo). `sudo usermod -ag sudo gylbertk` and after checking it out!

![linux](assets/images/part_5.png)

- we also check the rights and change the host name by switching to the user in paragraph Part 2

![linux](assets/images/part_5_1.png)


## Part 6. Installing and configuring the Time service

- Current time:

![linux](assets/images/part_6_1.png)

- I got the time, the time zone in which I was now.

![linux](assets/images/part_6_2.png)


## Part 7. Installing and using Text Editors


- Installed text editors **VIM**, **NANO**, **MCEDIT**, **JOE**. commands such as: `sudo apt install vim' - `sudo apt install nano' - `sudo apt install joe`

### Working with VIM
- Created a file test_vim.txt using the `vim' command test_vim.txt `. I specified my nickname in the file, saved it and left. To edit, we use the `i` key - the `insert` mode is turned on to disable it, the `esc` key and the exit from the editor itself are `shift` + `:` and we write `:wq` + `insert`

![linux](assets/images/part_7_1.png)

- opened it again and edited it:

![linux](assets/images/part_7_2.png)

- I opened it again and found the word I needed with the command `/`:

![linux](assets/images/part_7_3.png)

- opened it again and replaced one word with another `:s/what_word to replace/what_to replace`:

![linux](assets/images/part_7_4.png)

### Working with NANO
- Created a file test_vim.txt using the `nano' command test_nano.txt `. I specified my nickname in the file, saved it and exited by pressing `control + O` (plus confirmed the file name by clicking on `inter`) and to save and exit the editor `control + X`

![linux](assets/images/part_7_5.png)

- opened it again and edited it and pressed `control + X` and selected the `N` option to close the file without saving changes:

![linux](assets/images/part_7_6.png)

- result:

![linux](assets/images/part_7_7.png)

- I opened it again and found the word I need `control + W` as a result, the cursor moves to the beginning of the word on the searched word:

![linux](assets/images/part_7_8.png)

- replace the word I need with `control + \`:

![linux](assets/images/part_7_9.png)

### Working with JOE
- Created a file test_joe.txt using the `joe' command test_joe.txt `. I specified my nickname in the file, saved it and left. To save` use the keys `control + K` and to exit `control + x'

![linux](assets/images/part_7_10.png)

- opened it again and edited it and pressed `control + C` and selected the `Y` option to close the file without saving changes:

![linux](assets/images/part_7_11.png)

- result:

![linux](assets/images/part_7_12.png)

- I opened it again and need to find some word - to start, move the cursor to the beginning of the entire text `control + k and immediately press the control button F`: and the found word cursor moves to the end of the searched word

![linux](assets/images/part_7_13.png)

- next, it's tedious to replace one word with another ` control + k and immediately press the control button F, we look for the word and immediately the R button` and press `Y` to confirm

![linux](assets/images/part_7_14.png)

- result:

![linux](assets/images/part_7_15.png)







## Part 8. Installation and basic configuration of the service **SSHD**


- Installed the SSHd service with the command `sudo apt install openssh-server`

![linux](assets/images/part_8_1.png)

- Added autostart of the service when booting the system with the command `sudo systemctl enable ssh`

![linux](assets/images/part_8_2.png)

- And checked that the service is running `sudo systemctl status ssh`

![linux](assets/images/part_8_3.png)

- Reconfigured the SSHd service to port 2022. Pre-open the service config `/etc/ssh/sshd_config` and changed it to port 2022

![linux](assets/images/part_8_4.png)

- Used the ps command, showed the presence of the sshd process `ps -e | grep sshd`

![linux](assets/images/part_8_5.png)

----
- `ps` - allows you to view processes in the current shell by using the **-e** flag to select all processes and set **grep** to search for a process
----

- then restarted the configuration with the command `sudo systemctl reload ssh` or restarting the entire service `sudo systemctl restart ssh` and rebooted the system with the command `reboot` and checked the open ports `netstat -tan`

![linux](assets/images/part_8_6.png)

----
### Key value -tan:

- **-t** is used to show tcp ports;
- **-a** shows all ports;
- **-n** shows ip addresses in numeric form.

### Value of output columns:


- **Proto** — protocol (tcp, udp).
- **Recv-Q** — the number of bytes placed in the TCP/IP receive buffer, but not transmitted to the application. If this number is high, then you need to check the performance of the application that works with this port.
- **Send-Q** — the number of bytes placed in the TCP/IP send buffer but not sent, or sent but not acknowledged. A high value may be due to server network congestion.
- **Local Address** — the local address of the server.
- **Foreign Address** — the address of the second party.
- **State** — the state of connection, or listening. (LISTENING — socket is waiting for a connection request, CONNECTED — socket is connected, DISCONNECTING — socket is disconnected)

### Value 0.0.0.0:
- This is the default IP address on the local machine
----

## Part 9. Installing and using utilities **top**, **htop**

- Installed the `top` utility with the command: `sudo apt install top`
- Installed the 'htop` utility with the command: `sudo apt install htop`

### Working with top

- Example of work:
  ![linux](assets/images/part_9_1.png)

- **uptime**: 7 min;
- **number of authorized users**: 1 user;
- **total system load**: 0.00, 0.00, 0.00
- **total number of processes**: 112
- **cpu load**: 0.0 us, 0.0 sy, 0.0 ni, 100 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
- **memory loading**: 981.0 total, 169.3 free, 193.6 used, 618.1 buff/cache
- **pid of the process taking up the most memory**: 950
- **pid of the process taking up the most CPU time**: 950

### Working with htop

- Example of work:
  ![linux](assets/images/part_9_2.png)

----

- Output of the htop command sorted by **PID**:

![linux](assets/images/part_9_3.png)

- Output of the htop command sorted by **PERCENT_CPU**:

![linux](assets/images/part_9_4.png)

- Output of the htop command sorted by **PERCENT_MEM**:

![linux](assets/images/part_9_5.png)

- Output of the htop command sorted by **TIME**:

![linux](assets/images/part_9_6.png)

- Output of the htop command with filtering for the **sshd process**:

![linux](assets/images/part_9_7.png)

- Process search **syslog**:

![linux](assets/images/part_9_8.png)

- Added output of **hostname**, **clock** and **uptime**:

![linux](assets/images/part_9_9.png)

## Part 10. Using the **fdisk utility**

- Launched the fdisk -l command. `sudo fdisk -l`

![linux](assets/images/part_10_1.png)

- **Hard drive name**: dev/sda2;
- **Hard Disk Size**: 16 GiB;
- **Number OF sectors**: 33548288;
- **Swap size** (looked with the command `swapon --show'): 2.3 GiB.

![linux](assets/images/part_10_2.png)

## Part 11. Using the **df utility**

### Launched `df`
- Launched the `df` command:

![linux](assets/images/part_11_1.png)

- **partition size**: 16,445,308
- **occupied space size**: 5,813,576
- **free space size**: 97,776,644
- **percentage of usage**: 38%
- **unit of measurement in output**: in kilobytes.
-
### Launched `df -Th`
- Ran the command `df -Th':
- option `-h` to output the dimensions in readable form, in megabytes or gigabytes;
  - the `-T` option to output information only about the specified file systems.

![linux](assets/images/part_11_2.png)

- **partition size**: 16G
- **occupied space size**: 5.6G
- **free space size**: 9.4G
- **usage percentage**: 38%
- **file system type for partition**: ext4.


## Part 12. Using the **du utility**


Used the `-s` flag to output only the total size of the folder
- Size of /home, /var, /var/log folders in bytes: `sudo du -s /home /var /var/log`

![linux](assets/images/part_12_1.png)

- Size of folders /home, /var, /var/log in human-readable form: `sudo du -sh /home /var /var/log`

![linux](assets/images/part_12_2.png)

- Contents in /var/log (not general, but each nested element): `sudo du -s /home /var /var/log`

![linux](assets/images/part_12_3.png)

## Part 13. Installing and using the **ncdu utility**

- Installed the utility with the command `sudo apt-get install ncdu`

![linux](assets/images/part_13_1.png)

- Output the sizes of folders /home, /var, /var/log:
- /home

![linux](assets/images/part_13_2.png)

- /var

![linux](assets/images/part_13_3.png)

- /var/log

![linux](assets/images/part_13_4.png)


## Part 14. Working with system logs

- Opened for viewing:
- /var/log/dmesg

![linux](assets/images/part_14_1.png)

- /var/log/syslog

![linux](assets/images/part_14_2.png)

- /var/log/auth.log

![linux](assets/images/part_14_3.png)

The time of the last successful authorization is 20:49:16, the user name is student and the login method is by LOGIN (screenshot below).

![linux](assets/images/part_14_4.png)

----
![linux](assets/images/part_14_5.png)

----

- Restarted the SSHD service with the command `sudo systemctl restart ssh` and found a system record about it in /var/log/syslog:

![linux](assets/images/part_14_6.png)


## Part 15. Using the Task Scheduler **CRON**

Open the task scheduler for editing: `crontab -e`
- Using the task scheduler, I run the uptime command every 2 minutes:

![linux](assets/images/part_15_1.png)

![linux](assets/images/part_15_2.png)

- I display a list of current tasks for CRON with the command `crontab -l`

![linux](assets/images/part_15_3.png)

- Deleted all existing tasks with the `crontab -r` command and checked the list of current tasks

![linux](assets/images/part_15_4.png)