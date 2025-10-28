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


Lecture 04. Managing Docker Volumes
Docker volumes. This is a nice tool in Docker to share content between the different containers, to make it 
available to different applications at the same time simultaneously.

1. You can also use Docker volumes to access this data directly from your local system, but this is not recommended 
because it is not designed to work in that way, but still totally doable if you want to do.

2. Data persistence (data is not lost when container removed). Docker volumes are the way to persist data that is generated 
or used by Docker containers. Normally when container is deleted, its content also deleted.
So you cannot actually store data in a container that is entirely lost. But at the same time, you can use volumes 
to back up your data to store something sensitive or important in them, and use them as backup or some kind of a 
persistent storage.

3. Sharing Data(multiple container can access same volume). 
on top of data persistence, sharing, and backup, you can also use it as an isolation mechanic in order to separate  
your data from the container layer and store it elsewhere, which is a useful feature if you want same file to be 
shared across multiple applications or application versions at the same time.

Now let's take a look on how this works. For instance, Both containers will have a thing called Mountpoint inside them.
This is basically a folder that points at a certain space somewhere in the system, and what they will do. they 
will both point at the same folder in your desktop system.
So your actual operating system like Mac OS or Windows or Linux or whatever, will have an actual folder with 
actual files inside them. And both containers will have a pointers toward that folder, which will allow them 
to access this folder, to manipulate its content if necessary, or just read it if you need read only.


Now let's try something simple. Let's go to Docker Hub and use something like a BusyBox container that is essentially
just a Linux command line with no strings attached. It doesn't have any additional applications or services. 
It's very basic Linux setup. use the command from website and run it. 
And once it's done, you can see the content by ls -a or ls -l command. 
you can exit it using exit command. 

after that we will create the volume using the docker volume create my-vol(this is name) command. 
use the docker volume ls command to check if volume is created. it will create in your system so you can find 
that in the  mnt folder > docker desktop disk > data > docker > volumes. 
This folder will contain the actual data that we will use to share between the hosts.

I want to emphasize this that the folder might wall itself isn't the place where the data is hold. It will be here.
So let's do a simple experiment and create a basic text document with something inside.
create a file inside that folder and then mount this volume and attach it to the BusyBox. 
on ubunto, you will find var/lib/docker/volumes.

to add that file, we will use the command and add -v my-vol:/app/data in the command so command will look like 
docker run -it --rm -v my-vol:/app/data busybox. 
so if you run ls -l again in this then you will see app folder at the top with details like date and it was 
not present already. because we didn't attach volume before. 
and if we go inside that folder we will see our file that we added. 

let's try same for sql. you if you have any other container running, you can check in docker desktop and goto 
exec in terminal and there you can enter command and navigate to the directory and see the file that we added 
and hence we can access that file through multiple conteiners. 