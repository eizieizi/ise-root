# Cisco ISE Root Access

This repository contains a bash script which allows to escape the CARS vshell of Cisco ISE and therefore allows root access without root patch which is normally needed to do change configurations on the file system or databases. 

## Run TLS Analyzer

Execute the script (only tested on Linux Mint 20.1) in your working directory, it will create a subfolder called "logs" and download the logs from ESA after supplying credentials and hostname. 

You can also manually create a logs folder in the working directory and copy the logs manually into the folder to skip automatic download. The Script will ask you if you would like to use the existing logs. 

  ```sh
test@test-pc:~/Documents/Python/esa-tls-analyzer$ python3 /home/test/Documents/Python/esa-tls-analyzer/esa-tls-analyzer.py
./logs folder not existing, creating
Downloading Logs from ESA
Please enter ESA Hostname for FTP Login (for example: esa01.test.at): esa01.test.at
Please enter ESA Admin Username: admin
Please enter ESA Admin Password: 
Downloading File: mail.@20190516T183759.c
Downloading File: mail_logs.@20210228T173106.s
Downloading File: mail.@20190516T185309.s
Downloading File: mail_logs_text.@20190517T084759.s
Downloading File: mail_logs.@20200607T174936.s
Downloading File: mail_logs.@20201213T195441.s
Downloading File: mail_logs.current
Downloading File: mail_logs.@20200818T173344.s
Downloading File: mail_logs.@20210315T233403.c
Downloading File: mail_logs.@20200912T180853.s
Downloading File: mail_logs.@20201018T123644.s
Downloading File: mail_logs.@20201119T090259.s
Downloading File: mail_logs.@20210216T045532.s
Downloading File: mail_logs.@20210226T125825.c

 Would you like to re-use existing Logs? If answering no, the script will fetch logs via FTP from ESA yes/no: yes
```
![TLS-Versions](/images/used_tls_versions.png)
![Cipher-Versions](/images/used_tls_ciphers.png)
