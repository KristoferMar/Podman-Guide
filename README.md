# Podman-Guide

Run a container from a image in the background with a special tak 
<pre>
podman run -d -p 8080:80 --name httpd-basic quay.io/user_name/httpd-parent:2.4
</pre>

<i>ps</i> Lists running containers and the "-a" flag lists all running containers
<pre>
podman ps -a
</pre>

Stops a container
<pre>
podman stop pod_name/pod_id
</pre>

Restarts a stopped container
<pre>
podman restart pod_name/pod_id
</pre>

Deletes a container (the -f flag deletes the container even if it's no stopped)
<pre>
podman rm pod_name/pod_id
</pre>

Access a pod
<pre>
podman exec -it httpd-basic /bin/bash
</pre>

Environmant variables:
- Environment variables are set with the "-e" falg. An example could be the following: 

<pre>
podman run --name mysql-basic \
> -e MYSQL_USER=user1 -e MYSQL_PASSWORD=mypa55 \
> -e MYSQL_DATABASE=items -e MYSQL_ROOT_PASSWORD=r00tpa55 \
> -d registry_name/user_name/image_name:tag
</pre>

podman flags: 
<pre>
-t is equivalent to --tty, meaning a pseudo-tty (pseudo-terminal) is to be allocated for the container.
-i is the same as --interactive. When used, standard input is kept open into the container.
-d, or its long form --detach, means the container runs in the background (detached). Podman then prints the container id.

-l stands for latest
</pre>

It's also possible to use combinations such as the following to access any given pod 
<pre>
-it
</pre>

# Persistent Storage

- This enables us to create a directory outside the container and store files in that can be picked up by another container if we terminate the first one. This way our storage is persited to the host machine and is accessable by the container.

<pre>
mkdir -pv /home/student/local/mysql

sudo semanage fcontext -a -t container_file_t '/home/student/local/mysql(/.*)?'

sudo restorecon -R /home/student/local/mysql

ls -Zd /home/student/local/mysql

podman unshare chown -Rv 27:27 /home student/local/mysql

</pre>

# Directories
How to create nested directories 
- -v Print shell input lines as they are read.
- -p for creating "parent" and all underlaying "children" folders.
<pre>
mkdir -pv /home/student/local/mysql
</pre>

# Linux flags

This flag stands for 'add'
<pre>
-a 
</pre>

This flag stands for 'type'
<pre>
-t
</pre>

# Debugging

## Logging 

You can access the container log in the following way
<pre>
podman logs mysql-db
</pre>
