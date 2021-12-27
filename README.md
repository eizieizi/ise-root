# Cisco ISE Root Access

This repository contains a bash script which allows to escape the CARS vshell of Cisco ISE and therefore allows root access without root patch. Normally TAC is needed to do configuration changes on the file system or databases. 

## Get Root Access

Root access is only possible with physical/virtual access to the ISE Nodes.
It is necessary to start a live CD and execute the supplied script from there.

Basically, the script:

  * mounts the /dev/sda2 (Root) and /dev/sda3 (persisting configuration) partitions of ISE
  * creates a backup of 
  ```sh
/etc/sudoers 
/etc/passwd
/etc/shadow

to /dev/sda3/rootaccess_restore/ 
The Backup is only created at the first time the script is executed, to be able to restore to a non-rooted vanilla ISE.

```

 * adds a new user with the supplied User & Pass and changes the Standard Shell (/opt/system/bin/carssh.sh) to /bin/bash 
 * adds the new user to the sudoers file. 


The whole Script is tested with Ubuntu 20.04 as Live CD and ISE 3.1



  ```sh
Import Output of Successful Scrip execution 
```



### Partitons of ISE & Logic of Script


  ```sh

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   600G  0 disk
├─sda1   8:1    0  1000M  0 part /boot
├─sda2   8:2    0  17.6G  0 part /
├─sda3   8:3    0   100M  0 part /storedconfig
├─sda4   8:4    0     1K  0 part
├─sda5   8:5    0   7.8G  0 part [SWAP]
├─sda6   8:6    0     2G  0 part /tmp
└─sda7   8:7    0 571.6G  0 part /opt
sr0     11:0    1  1024M  0 rom

```

ISE has 2 important partitins for Root Access - /dev/sda2 is the root fileystem. The Script creates the root users here but also needs to copy /etc/passwd and /etc/shadow to /dev/sda3/startup-config-*/etc which holds the ISE CARS Application Configuration.

On a normal running ISE,  /dev/sda3 is mounted into /storedconfig.


