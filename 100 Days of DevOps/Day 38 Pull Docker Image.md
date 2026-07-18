Day 38: Pull Docker Image

To master a new technology, you will have to play with it.

– Jordan Peterson

Nautilus project developers are planning to start testing on a new project. As per their meeting with the DevOps team, they want to test containerized environment application features. As per details shared with DevOps team, we need to accomplish the following task:

a. Pull busybox:musl image on App Server 2 in Stratos DC and re-tag (create new tag) this image as busybox:media.

------------------------------------------------------------------------------
[steve@stapp02 ~]$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[steve@stapp02 ~]$ 
[steve@stapp02 ~]$ docker --version 
Docker version 26.1.3, build b72abbb
[steve@stapp02 ~]$ 
[steve@stapp02 ~]$ docker pull busybox:musl
musl: Pulling from library/busybox
a5156bff9914: Pull complete 
Digest: sha256:8635836765b0c4c43970660219739baa58b0883c2e429e4b8918f7dd1519455c
Status: Downloaded newer image for busybox:musl
docker.io/library/busybox:musl
[steve@stapp02 ~]$ 
[steve@stapp02 ~]$ docker tag busybox:musl busybox:media
[steve@stapp02 ~]$ 
[steve@stapp02 ~]$ docker images | grep busybox
busybox      media     5a93558ae921   2 months ago   1.53MB
busybox      musl      5a93558ae921   2 months ago   1.53MB
[steve@stapp02 ~]$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[steve@stapp02 ~]$ 
[steve@stapp02 ~]$ date
Sat Jul 18 20:33:34 UTC 2026
[steve@stapp02 ~]$ 