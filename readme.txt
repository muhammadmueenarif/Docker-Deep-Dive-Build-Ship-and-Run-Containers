docker ps to check running docker containers 
docker images to see the docker images we have 
docker pull to pull the image with its name. 
docker run mysql(imagename) to run the image. 

Docker itself is an open source platform. it enables developers to build, package and deliver their products
in containers. containers are lightweight and standalone units that deliver application with all its dependencies 
and ensure that it will have a consistent behavior across different environments.

Docker is an ideal way to deliver your application, no matter where you want to run it the setup, the configuration, 
the environment, everything will be handled by Docker.
Whenever you deploy your application to any kind of new platform. It would be fair to say that this reminds of 
regular VMs.
Docker manages to make its containers lighter than the regular virtual machine, because it does not actually 
require a full operational system to work. it builds on top of an existing operational system and utilizes 
its services and capacity to run its containers, basically providing only the bare minimum for each container
to function.

This means that Docker will be way faster and cheaper to run than regular VM. the speed and resource cost 
efficiency of Docker made it quite popular in the industry. 
as well as its capacity to well integrate itself into CI, CD workflows and processes, capacity to deliver 
stable and predictable behavior of applications in both test and production environments, as well as the 
sprawling community that supports the platform. Multiple images and contributes to its further development.



Lec 02. How to Install Docker?

Lec 03. Pulling and Running Docker Images
what are Docker image, how to work with them and where to find them? 
goto Docker Hub. This is a website where you can find the existing Docker images that are publicly available 
of various applications, services, and their different versions.
For the purpose of this lesson, we will be working with the MySQL image, which contains obviously MySQL service 
that is backed up and ready to go. You can search in the search bar and find various images.

on that page, we can see different things like general overview, recent tags, supported tags, links to quick 
references, tags etc., tags are basically the way that Docker handles its versioning, different options of 
this image and so on.
We can also see additional information like how to run the image, different commands set up properties.
Environmental parameters.
we will use this and run the image and make it accessible for everyone.

copy the command in the right side section and run it in terminal. 

use the docker ps command to check if any container is already running or not. make sure no container is running 
already and after that use the command. 
docker will pull the latest version with the command and download and you will be able to use that in your pc.
use docker images command to see the images you have with their details like size and when created etc., 
then use the command docker run mysql to run the image. 
We will need to provide some additional information. Most of the docker images will require setup passwords etc., 
We can use docker run -e MYSQL_ROOT_PASSWORD=12345678 mysql. 

In the docker desktop you will see your containers and everything about container like logs etc., 
in the exec section of container, you can run bash script or shell commands for linux that runs inside the 
Docker image. we can delete the container and exit from the service etc., 
We can stop the container by clicking on stop icon or goto the terminal where we run the container and stop 
from there by using ctrl+c. it will take sometime to stop but if you press ctrl+c Multiple times then it will
stop forcefully. Means that services running stop but the container itself is running. 
If you want to start docker image again, then just click on start and it will start again. 
All the settings that we have set up with the first run like environment variables like root password, will 
be kept intact, so we don't need to set them every time we run the image Again.
Docker will remember the setup for this image and will just reuse the same environmental parameters everytime 
we want to start it.

If we will change docker password, database password for example, then it will be a different image because 
the environment has changed and the vigilant Kepler will be no longer used.