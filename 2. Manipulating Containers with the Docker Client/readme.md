<!-- @format -->

# Docker commands


### in this section i will dive into basic commands


> ##### creating and running the contianer. (run)

```
docker run <image name>
```

example
```
> docker run redis
1:C 10 Sep 2021 21:14:45.476 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 10 Sep 2021 21:14:45.476 # Redis version=6.2.5, bits=64, commit=00000000, modified=0, pid=1, just started
1:C 10 Sep 2021 21:14:45.476 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 10 Sep 2021 21:14:45.477 * monotonic clock: POSIX clock_gettime
1:M 10 Sep 2021 21:14:45.478 * Running mode=standalone, port=6379.
1:M 10 Sep 2021 21:14:45.478 # Server initialized
1:M 10 Sep 2021 21:14:45.478 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 10 Sep 2021 21:14:45.479 * Ready to accept connections
```

you can supply additional command to run like this 
```
docker run busybox echo hi there
hi there
```

```
docker run busybox ls
bin
dev
etc
home
proc
root
sys
tmp
usr
var
```
this will list all dircitoy inside container

> #### note about additional commands
> echo, ls work becouse there exist in  busybox image.
> if you try to do this in image that don't exits like.
> an error will occure
>
>```
>PS C:\Users\Ahmad> docker run hello-world ls
>docker: Error response from daemon: OCI runtime create >failed: container_linux.go:380: starting container process >caused: exec: "ls": executable file not found in $PATH: >unknown.
>```
> this error happen becouse hello-world image don't have ls command inside it

----
> ##### list all running conatiners. (ps)

```
docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED             STATUS             PORTS      NAMES
e7187f9dd90a   redis     "docker-entrypoint.s…"   About an hour ago   Up About an hour   6379/tcp   stupefied_albattani
```

this will get all conatiner that are running for now.
but conatiner must be running for time.

if you want to get al container that have been created you can add **--all**
```
docker ps --all
CONTAINER ID   IMAGE         COMMAND                  CREATED             STATUS                           PORTS      NAMES
77c1a8169315   busybox       "ls"                     7 minutes ago       Exited (0) 7 minutes ago                    nice_hellman
eb70fe226deb   busybox       "echo hi there"          19 minutes ago      Exited (0) 19 minutes ago                   funny_panini
83efbd535598   busybox       "sh"                     20 minutes ago      Exited (0) 20 minutes ago                   elegant_sammet
6d39a719fbfa   busybox       "sh"                     About an hour ago   Exited (130) 22 minutes ago                 funny_bassi
e7187f9dd90a   redis         "docker-entrypoint.s…"   About an hour ago   Up About an hour                 6379/tcp   stupefied_albattani
1260db03d1d4   redis         "docker-entrypoint.s…"   2 days ago          Exited (255) About an hour ago   6379/tcp   elastic_mclean
9496ec80d93e   hello-world   "/hello"                 2 days ago          Exited (0) 2 days ago                       nostalgic_robinson
c76db3303aaf   busybox       "ping google.com"        2 days ago          Exited (137) 2 days ago                     trusting_lichterman
```

> you can see all conatiner that are running, exit ones from status you can know if conatiner is running or closes.
> #### note you can delete all containers from your machine by this command
> ```
>docker system prune
>WARNING! This will remove:
>  - all stopped containers
>  - all networks not used by at least one container
>  - all dangling images
>  - all dangling build cache
>
> Are you sure you want to continue? [y/N]
>```
> #### but be carefull this will remove all images and cache you can use it  when you want to save space