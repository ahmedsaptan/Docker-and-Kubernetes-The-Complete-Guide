<!-- @format -->

# Docker commands

create and run the contianer

```
docker run <image name>
```
---
this will echo "hi there"
```
docker run busybox echo hi there
```
---

```
docker run busybox ls
```
this will list all dircitoy inside container


note those command echo, ls work becouse there exist in busybox image,
if you try to do this in image that don't exits like image "hello-wolrd" you will get an error

```
PS C:\Users\Ahmad> docker run hello-world ls
docker: Error response from daemon: OCI runtime create failed: container_linux.go:380: starting container process caused: exec: "ls": executable file not found in $PATH: unknown.
```

----
## list all container that are running now

```
PS C:\Users\Ahmad> docker ps
CONTAINER ID   IMAGE     COMMAND             CREATED         STATUS         PORTS     NAMES
c76db3303aaf   busybox   "ping google.com"   6 seconds ago   Up 6 seconds             trusting_lichterman
```

to get all container that have been create and it's running or not

```
docker ps --all
```