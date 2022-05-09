# Docker-Compose-Urbackup


How to Install UrBackup Server using Docker Container

September 28, 2022 admin Backup, Docker, Virtualization 1

UrBackup is a free, powerful backup tool available for Windows, Mac, and also Linux. On my previous tutorial, you can see how to install Urbackup Server on Ubuntu. But today, I am going to show you how to install UrBackup Server using Docker Container. So basically I am going to deploy a new Urbackup server container on top of Docker. First thing first, we need to have Docker engine installed on the system. You can read the following tutorial to install Docker on several systems:

    Debian 9
    Ubuntu 18.04
    Manjaro 18.0
    Fedora 28

After installing Docker, now we are ready to install or create Urbackup container. 
Steps to Install UrBackup Server using Docker Container
A. Pull the Latest UrBackup Image

In Terminal, use this command to download/pull the latest version of UrBackup Server docker image.

```

 # docker pull uroni/urbackup-server
 
 ```

This will download the image from the internet. It will take few minutes depends on your internet speed. 
B. Create UrBackup Container

After we pull the latest version of Urbackup server image, now we are ready to run a new docker container with this command

```

<img src='./src/1.png' width='200'/> 
<img src='./src/2.png' width='200'/> 

#docker run -d --name urbackup-server-1 -v /media/backups:/backups -v /media/database:/var/urbackup -p 55413-55415:55413-55415 -p 35623:35623/udp uroni/urbackup-server

```

You can change the urbackup-server-1 into something else. And also please note that the command will use and mount the /media/backups and /media/database directory in the host to store the backup. 

Now make sure if this new container is up and running with ps command

```
#docker ps
```

Output

C. Configure the UrBackup via Web Interface

Open a web browser and then type the docker host IP address followed by the Urbackup port 55414. For example:

```
#192.168.100.200:55414
```

You should see the following 

Install UrBackup Server using Docker Container
D. Add UrBackup Client

Our backup server is up and running. Now, we can add the client to backup to this new server. We need to install UrBackup client on each computer we want to backup. You can download the Urbackup client from this link. Select your operating system from the list.

Once installed, the UrBackup Server will automatically detects the clients if they are in the same network. For more advanced options, you can open the Settings page on the client. 





