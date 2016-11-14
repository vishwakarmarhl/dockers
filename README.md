
# dockers repository
Docker files for various container configuration

# Use the Docker Hub for this
docker pull vishwakarmarhl/ubunitydesk

# Alternately Execute a DockerFile and tag as follows

$ docker build -t vishwakarmarhl/ubunitydesk:v01 . -f DockerFile 
$ docker run -it -p 53022:22 -p 53023:5900 -p 53021:80 vishwakarmarhl/ubunitydesk:v01 /bin/bash
$ docker-machine ls

# Run AAH & VNC Server for provisioning access to this environment from outside
$ service ssh restart
$ export USER=crusader
$ vncserver -geometry 1440x900 -rfbport 5900
$ ps -eaf | grep vnc

# You could also connect to this instance using SSH from the host
$ ssh -p 52022 crusader@192.168.99.100

# To persist any changes commit using the container id
$ docker ps
  CONTAINER ID        IMAGE                            COMMAND             CREATED             STATUS              PORTS
  4f2bdae9b5c2        vishwakarmarhl/ubunitydesk:v01   "/bin/bash"         5 seconds ago       Up 4 seconds        0.0.0.0:53022->22/tcp, 0.0.0.0:53021->80/tcp, 0.0.0.0:53023->5900/tcp

$ docker commit 4f2bdae9b5c2 vishwakarmarhl/ubunitydesk:v01


