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

mybuild: it will invoke build function of docker-compose that the specifications are given the file. 

PIC HERE

myup: 

## Docker-compse.yaml file
the file is given in the repository. It starts with a version statment that indicates how thise file format  is. Here the version 3 ,s the feature-rich version for service orchestrations.

The file will have 3 main sections: services, volumes and networks.  Will have 3 services,2 volumes, and 1 network. 
### Services:
### 1-Nginx:
container name,  
build  (refer to the path to the folder that contains Dockerfile. AS here we have our own requirements to build an image we will use the build directive, if the image is ready in an image hub like DockerHub or AWS ECR or a private registry we should use  image directive.
ports: "443:50001"  map the host to the container. Generally they are pefered to have the same numbers on the both side to avoid confussion. to distinguish the difference we will use different numbers . The nginx configuration must include the 50001, a browser coming with a https request( generally 443) will hit the host VM, and then the request will be forwarded to the container which is listening on 50001.
We can define multiple ports directives depending on the requirments. if there was a HTTP, we would have defined a second one which will map 80 to like  50011.
<u>depends_on: </u>
this will determine the order of container creations. Nginx will wait the creation of Wordpress.

<u>volumes: </u> - wp:/var/www/html
Indicates the wolume it is going to use or write. If there are volumes to use it will use them.
it is plural, as on container can have multiple volume mounts. I have discussed the volume issu in my article here: 
The first part (wp:) actually refers to the named volume defined in the volumes section of the docker-compose.yaml file. it tells that it is making a long-term persistence.  



<u>networks: 
-mynetwork
it is plural like the anaolgu that in the physical world a commputer can have different netorks like cabled etherne,  wi-fi, bluetooth.
