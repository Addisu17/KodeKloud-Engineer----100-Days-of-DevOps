Day 37: Copy File to Docker Container

One big reason for a winning attitude is that you will take the necessary steps and not quit when the going gets difficult.

– Don M.Green

The Nautilus DevOps team possesses confidential data on App Server 3 in the Stratos Datacenter. 
A container named ubuntu_latest is running on the same server.

Copy an encrypted file /tmp/nautilus.txt.gpg from the docker host to the ubuntu_latest container located at /home/. 
Ensure the file is not modified during this operation.

[banner@stapp03 ~]$ docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
b7879582e170   ubuntu    "/bin/bash"   5 minutes ago   Up 5 minutes             ubuntu_latest
[banner@stapp03 ~]$ 
[banner@stapp03 ~]$ ls -la /tmp/
total 48
drwxrwxrwt 10 root root 4096 Jul 17 14:22 .
dr-xr-xr-x  1 root root 4096 Jul 17 14:25 ..
drwxrwxrwt  2 root root 4096 Jul 17 14:05 .ICE-unix
drwxrwxrwt  2 root root 4096 Jul 17 14:05 .X11-unix
drwxrwxrwt  2 root root 4096 Jul 17 14:05 .XIM-unix
drwxrwxrwt  2 root root 4096 Jul 17 14:05 .font-unix
-rwxr-xr-x  1 root root  198 Jul 17 14:19 docker-container.sh
-rw-r--r--  1 root root  105 Jul 17 14:19 nautilus.txt.gpg
drwx------  3 root root 4096 Jul 17 14:05 systemd-private-3d1ecd178de84553afca92ada9749f17-dbus-broker.service-ytJj0P
drwx------  3 root root 4096 Jul 17 14:05 systemd-private-3d1ecd178de84553afca92ada9749f17-rtkit-daemon.service-NTrh5Y
drwx------  3 root root 4096 Jul 17 14:05 systemd-private-3d1ecd178de84553afca92ada9749f17-systemd-logind.service-73syah
drwx------  3 root root 4096 Jul 17 14:05 systemd-private-3d1ecd178de84553afca92ada9749f17-upower.service-B4xk5D
[banner@stapp03 ~]$ pwd
/home/banner
[banner@stapp03 ~]$ ls -la
total 20
drwx------ 2 banner banner 4096 Jul 17 14:05 .
drwxr-xr-x 1 root   root   4096 Jul 17 14:05 ..
-rw-r--r-- 1 banner banner   18 Feb 15  2024 .bash_logout
-rw-r--r-- 1 banner banner  141 Feb 15  2024 .bash_profile
-rw-r--r-- 1 banner banner  492 Feb 15  2024 .bashrc
[banner@stapp03 ~]$ 
[banner@stapp03 ~]$ ls -la /home/
total 12
drwxr-xr-x 1 root   root   4096 Jul 17 14:05 .
dr-xr-xr-x 1 root   root   4096 Jul 17 14:25 ..
drwx------ 2 banner banner 4096 Jul 17 14:05 banner
[banner@stapp03 ~]$ 
[banner@stapp03 ~]$ docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/home/
Successfully copied 2.05kB to ubuntu_latest:/home/
[banner@stapp03 ~]$ 
[banner@stapp03 ~]$ docker exec ubuntu_latest ls -l /home/nautilus.txt.gpg
-rw-r--r-- 1 root root 105 Jul 17 14:19 /home/nautilus.txt.gpg
[banner@stapp03 ~]$ 
[banner@stapp03 ~]$ docker exec ubuntu_latest ls -l /home/
total 8
-rw-r--r-- 1 root   root    105 Jul 17 14:19 nautilus.txt.gpg
drwxr-x--- 2 ubuntu ubuntu 4096 Jul 13 16:06 ubuntu
[banner@stapp03 ~]$ 