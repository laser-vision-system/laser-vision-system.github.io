# Installing The Server/GUI Pre-requesites 
To deploy our system to your server you will need to have docker installed and access to the wider internet to pull our images, **currently the lab server meets these requirements, this guide is here incase the server has to be setup from scratch again**

**Note.** This part of the guide will assume you have a hardware machine that meets the minumum secifications for docker and our system, we will also assume that you have terminal or greater access to your system. 

## Installing docker 
Navigate to the corosponding link to install docker for your system

['Ubuntu'](https://docs.docker.com/engine/install/ubuntu/)
['Raspberry-pi-32-bit'](https://docs.docker.com/engine/install/raspberry-pi-os/)
['Raspberry-pi-64-bit-or-Debian'](https://docs.docker.com/engine/install/debian/)
['Windows'](https://docs.docker.com/desktop/setup/install/windows-install/)
['Mac'](https://docs.docker.com/desktop/setup/install/mac-install/)

## Network prep
Make sure your device has access to the internet, if you wish to confirm try to ping `ghcr.io`. If this ping goes through you will be able to pull our docker images. If you are unable to ping this address we have found that while you are on the labs internal network you may need to do the following: 
- disable IPv6
- configure a manual DNS server of `8.8.8.8` and `8.8.4.4`

---

Please read the server pre-requistes document prior to following this guide, we will now walk you through the steps to configure the `server` and `gui` systems onto you server. 

----

## Server
The server is a rellay point between all the `edge` compute devices in the lab and `gui`, it also holds your persistance data such as previously saved device configurations and logs. 

### Starting the server docker container
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

## GUI
The GUI is what you will interact with on a day to day basis, it acts effectivly as a direct mirror of the server. 

### Starting the gui docker container
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

## Next steps
Once both docker containers are up and running you should be able to access the GUI by navigating to the servers address and adding `:5173` at the end of the address. for the lab enviroment that should be `192.168.20.13:5173`. 

If you need to update the docker containers on the server please refer too the 