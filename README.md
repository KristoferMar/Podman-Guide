# Podman-Guide

Run a container from a image in the background with a special tak 

<pre>
podman run -d -p 8080:80 --name httpd-basic quay.io/your-registry/httpd-parent:2.4
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
-t is equivalent to --tty, meaning a pseudo-tty (pseudo-terminal) is to be allocated for the container.
-i is the same as --interactive. When used, standard input is kept open into the container.
-d, or its long form --detach, means the container runs in the background (detached). Podman then prints the container id.

It's also possible to use combinations such as the following to access any given pod 
<pre>
-it
</pre>
