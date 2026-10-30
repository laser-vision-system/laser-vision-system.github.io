# Updating the edge 
This guide will walk you though how to pull a new version of our edge docker image.

## SSH
connect to the edge device you wish to update via SSH, not you will need to know the devices IP address this can be found be looking at the hosts/clients tab of `192.168.20.1`.

When prompted enter the username: `lab_admin` and the password is: `TallGoggles5$2` 

### Stop the current container 
execute `docker container ls` to check for exsisting containers, if there are containers present please run `docker container kill CONTAINER_NAME` if you have used our default command you can just run the following: 
```
docker container kill edge
```

### Check & remove exsisting images
run the following command and take note of the images present: 
`docker images` 

if the image you wish to upgarde too is not present then you can skip this next step, otherwise please run the following command: 
```
docker image rm YOUR_IMAGE_TAG
```

if you have followed our previous guides on how to install the edge then you can run this command instead: 
```
docker image rm ghcr.io/laser-vision-system/edge:arm64-release-main 
```

### Pulling new images 
Now it is time to re-run our docker image, here is the command you need to run with its corosponding attributes: 

**NOTE** This command will re-run the release version of our main branch, if you want too or have been asked to run an alternative version of the edge please change the final line of this command to the image you wish to run. 

```
docker run \
--net=host \
--privileged \
--name edge \
--restart unless-stopped \
--mount type=bind,src=/dev,dst=/dev \
--detach \
-e SERVER_URL=192.168.20.13:8080 \
-e VERBOSITY=3 \
ghcr.io/laser-vision-system/edge:arm64-release-main 
```
###### --net=host
gives the docker container access to your devices network interface, this is required for auto connecting to the server.

###### --priviledged 
this runs the container in priveledged mode, without this tag our container will fail to access your devices cameras.

###### --name edge
the name of your docker container, this can be changed freely and is the name that will be associated with its container id when you run the command `docker container ls`

###### --retsart unless-stopped
ensures that if your docker container stops running for any reason besisdes intentionally stopping it the container will start back up automaticly e.g. on device restart.

###### --mount type=bind,src=/dev,dst=/dev 
camera devices on linux are mounted to the dev folder in a machines root path, this command can be forgone on other platforms but is nessacary for our container to 

###### --detach 
detaches your terminal from the container when running the container for the first time, the output of the docker run command will provide you with the edge ID and nothing more. if you execute `docker container ls` you can see the container running in the background 

###### -e .......
the two commands listed that start with the prefix `-e` are our enviorment varriables and are tailored to our system, `SERVER_URL` specifies the server address for our system. if not defined on first container run it will default to autoconnect which scans the local network for the server, make sure to include the port when specifying the address which is by default `8080`. the seccond varriable is our error logging verbosity `VERBOSITY` this specifies what level of errors are sent to the server, it ranges from 1 -> 4 with the lower numbers only logging major errors where as 4 will log every occurance on our edge system. 

###### ghcr.io/laser-vision-system/edge:arm64-release-main  
This specfies the image to use for our container, our tags follow a system as follows:

`ghcr.io/laser-vision-system/` - our github orgonization 
`/edge` - our edge program
`arm64` - CPU architecture, raspberry pi's run & macs on `arm64` where as most modern laptops & desktops use `amd64`
`-release-` - Specifies the build target, release has only what is required for production where as the `dev` tag will print debugging alerts in the console
`main` - the github branch that the docker image is built from, `main` is our stable branch and is intended for production use.

### Help! docker could not find the image when trying to run it. 
if you get an error because your system cannot find the docker image localy you might be having network issues, please refer to the troubleshooting steps from early under `Network prep`. if you have preformed the above steps and can ping `ghcr.io` you can try pull the docker image manually. 

```
docker pull ghcr.io/laser-vision-system/edge:arm64-release-main 
```

if this does not work please contact your IT department or the system maintainers. 

### Conclusion 
Your docker image should now be updated.