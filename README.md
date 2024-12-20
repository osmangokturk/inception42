# inception42
This project is about Docker containers to be used for an web application. We will use a container as a webserver, a container as a database and a container for wordpress

# Virtual Machine (VM) on my Mac and installation on the VM
We will create a debian virtual machine to install make, docker.io and docker-compose to  host the containers.  Our aproach will be from the last to the bottom.

I have a macOS as the physical machine. I will have a debian virtual machine to host the containers. 
-from Mac to VM, I will setup portforwarding to be able to work from Mac terminal.
-in the VM I will install make to run the Makefile. Makefile would serve as a interface for VM to build, up, stop, start or down containers. 
-I will install docker.io that will create docker containers 
-I will install docker-compose so that I can create multiple containers simultanesously that are linked and work together. 

## Makefile
with the help of makefile, we will define or customize several commands that will do specific jobs. 




