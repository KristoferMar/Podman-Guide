# Podman-Guide

Run a container from a image in the background with a special tak 

<pre>
podman run -d -p 8080:80 --name httpd-basic quay.io/your-registry/httpd-parent:2.4
</pre>

Access a pod
<pre>
podman exec -it httpd-basic /bin/bash
</pre>

podman flags: 
-t is equivalent to --tty, meaning a pseudo-tty (pseudo-terminal) is to be allocated for the container.
-i is the same as --interactive. When used, standard input is kept open into the container.
-d, or its long form --detach, means the container runs in the background (detached). Podman then prints the container id.

It's also possible to use combinations such as the following to access any given pod 
<pre>
-it
</pre>
