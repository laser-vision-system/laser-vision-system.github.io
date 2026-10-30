# Updating the Server and GUI
This guide will walk you though how to pull a new version of our server and GUI docker image.

## Accessing the terminal
access the servers terminal using either SSH or physical access, the method has no bearing on the following steps. 

### Stop the current container 
execute `docker container ls` to check for exsisting containers, if there are containers present please run `docker container kill CONTAINER_NAME` if you have used our default command you can just run the following: 
```
docker container kill server 
docker container kill gui 
```

### Check & remove exsisting images
run the following command and take note of the images present: 
`docker images` 

if the image you wish to upgarde too is not present then you can skip this next step, otherwise please run the following command: 
```
docker image rm YOUR_IMAGE_TAG
```

if you have followed our previous guides on how to install the server and gui then you can run this command instead: 
```
docker image rm ghcr.io/laser-vision-system/server:amd64-release-main 
docker image rm ghcr.io/laser-vision-system/gui:amd64-main 
```

### Pulling new images 
Now it is time to re-run our docker image, here is the command you need to run with its corosponding attributes: 

**NOTE** This command will re-run the release version of our main branch, if you want too or have been asked to run an alternative version of the edge please change the final line of this command to the image you wish to run. 

----

### For the Server: 
navigate to your terminal and run the following command to start the server, listed are the  corosponding attributes:  
```
docker run \
-p 8080:8080 \
--name server \ 
--detach \ 
--restart unless-stopped \
--mount type=bind,src=/home/USR/laser-vision-system,dst=/content \
ghcr.io/laser-vision-system/edge:amd64-release-main 
```
###### -p 8080:8080
this command exposes port 8080 on your host machine and inside the container, how this attribute works is the left most ports dictate what ports the container mouts too on your host where as the right is what the system thinks its being fed on the inside of the container. **WE STRONGLY ADVISE AGAINST CHANGING THIS** if you do need to change this you can alter the left side to whatever you wish but you must leave the right unchanged e.g. `----:8080`, `1234:8080`.

###### --name server
the name of your docker container, this can be changed freely and is the name that will be associated with its container id when you run the command `docker container ls`

###### --detach 
detaches your terminal from the container when running the container for the first time, the output of the docker run command will provide you with the edge ID and nothing more. if you execute `docker container ls` you can see the container running in the background 

###### --retsart unless-stopped
ensures that if your docker container stops running for any reason besisdes intentionally stopping it the container will start back up automaticly e.g. on device restart.

###### --mount.....
this command exposes a folder on your host machine to the inside of the docker container, the `src=...` portion of the command tells your container where to mount the folder on your host machine. the `dst=...` is where the files are coming from inside the container. for the command to work **You will need to change `USR` too the name of the lab servers primary account** otherwise the logs will not write. if done correctly you will see a server.log file apear inside the `laser-vision-system` folder in your home directory. 

###### ghcr.io/laser-vision-system/edge:amd64-release-main 
This specfies the image to use for our container, our tags follow a system as follows:

`ghcr.io/laser-vision-system/` - our github orgonization 
`/server` - our server program
`amd64` - CPU architecture, raspberry pi's run & macs on `arm64` where as most modern laptops & desktops use `amd64`
`-release-` - Specifies the build target, release has only what is required for production where as the `dev` tag will print debugging alerts in the console
`main` - the github branch that the docker image is built from, `main` is our stable branch and is intended for production use.

### Help! docker could not find the image when trying to run it. 
if you get an error because your system cannot find the docker image localy you might be having network issues, please refer to the troubleshooting steps in the `server pre-requistes` document. if you have preformed the above steps and can ping `ghcr.io` you can try pull the docker image manually. 

```
docker pull ghcr.io/laser-vision-system/server:amd64-release-main 
```

if this does not work please contact your IT department or the system maintainers. 
----

### For the GUI: 
navigate to your terminal and run the following command to start the gui, listed are the  corosponding attributes:  
```
docker run \
-p 5173:5173 \
--name gui \ 
--detach \ 
--restart unless-stopped \
ghcr.io/laser-vision-system/gui:amd64-main
```

###### -p 5173:5173 
this command exposes port 5173 on your host machine and inside the container, how this attribute works is the left most ports dictate what ports the container mouts too on your host where as the right is what the system thinks its being fed on the inside of the container. **WE STRONGLY ADVISE AGAINST CHANGING THIS** if you do need to change this you can alter the left side to whatever you wish but you must leave the right unchanged e.g. `----:5173`, `1234:5173`.

###### --name gui
the name of your docker container, this can be changed freely and is the name that will be associated with its container id when you run the command `docker container ls`

###### --detach 
detaches your terminal from the container when running the container for the first time, the output of the docker run command will provide you with the edge ID and nothing more. if you execute `docker container ls` you can see the container running in the background 

###### --retsart unless-stopped
ensures that if your docker container stops running for any reason besisdes intentionally stopping it the container will start back up automaticly e.g. on device restart.

###### ghcr.io/laser-vision-system/gui:amd64-main
This specfies the image to use for our container, our tags follow a system as follows:

`ghcr.io/laser-vision-system/` - our github orgonization 
`/gui` - our server program
`amd64` - CPU architecture, raspberry pi's run & macs on `arm64` where as most modern laptops & desktops use `amd64`
`main` - the github branch that the docker image is built from, `main` is our stable branch and is intended for production use.

### Help! docker could not find the image when trying to run it. 
if you get an error because your system cannot find the docker image localy you might be having network issues, please refer to the troubleshooting steps in the `server pre-requistes` document. if you have preformed the above steps and can ping `ghcr.io` you can try pull the docker image manually. 

```
docker pull ghcr.io/laser-vision-system/gui:amd64-main 
```

if this does not work please contact your IT department or the system maintainers. 

----
### Conclusion 
Your docker image should now be updated.