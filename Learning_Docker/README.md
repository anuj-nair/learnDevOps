# Basic Docker

## Using docker

* `run` Command
	Run a docker image
	```
	docker run <imageName:imageTag/imageId> 
	```
	* Additional options
		* `-ti` for Terminal Interface
		* `-d` for Detaching and running the image in background
		* `-v` for mounting a file or folder
		* `--rm` for removing the container after use
	* To Run GUI in Docker containers
		```
		docker run --rm -ti --net=host --env="DISPLAY" --volume="$HOME/.Xauthority:/root/.Xauthority:rw" <imageName:imageTag/imageId>
		```
* `ps` Command
	Shows running containers 
	```
	docker ps
	```
	* Additional options
		* `-l` for showing last run container
		* `-a` for showing all run containers

* `attach` Command 
		```
		docker attach <containerId/containerName>
		```
* To Detach from a running container
	```
	<Ctrl+p> <Ctrl+q> 
	```

* `exec` Command
	Start another process on existing container
	```
	docker exec -ti <containerId/containerName> <command>
	```
	* Helps in debugging
		

* `logs` Command
	Keep the output of container
	```
	docker logs <containerId/containerName>
	```
	* Keep the logs small or they might pile up
* `inspect` Command
	* It helps you find information about the container
		```
		docker inspect <containerId/containerName>
		```
		or
		```
		docker inspect --format '{{.State.Pid}}' <containerId/containerName>
		```
* `kill`,`rm` and `rmi` Command
	* Kill a container
		```
		docker kill <containerId/containerName>
		```
	* Remove a container
		```
		docker rm <containerId/containerName>
		``` 
	* Remove a image
		```
		docker rmi <imageName:imageTag/imageId>
		``` 
* `save` and `load` Command
	* Save an image locally
		```
		docker save -o <filename>.tar.gz <imageId/imageName>
		```
	* Load a saved image
		```
		docker load -i <filename>.tar.gz
		```
## Manage Resources
* Memory Limits
	```
	docker run --memory maximum-allowed-memory <containerId/containerName> <command>
	``` 
* CPU Limits
	```
	docker run --cpu-shares <relative_to_other_containers>
	docker run --cpu-quota <to_limit_it_in_general>
	``` 
## Build Docker Image

### Build a Dockerfile
```
docker build -t <imageName> <Folder_of_Dockerfile>
```
### Format
* FROM Statement
	```
	FROM image
	```
* MAINTAINER Statement
	```
	MAINTAINER Firstname Lastname <email@example.com>
	```
* RUN Statement
	```
	RUN unzip install.zip /opt/install/
	RUN echo hello docker
	```
* ADD Statement
	```
	ADD run.sh /run.sh # copies files to folder
	ADD project.tar.gz /install/ # unzips the file to folder
	ADD https://project.example.com/download/1.0/project.rpm /project/ # download from website to folder
	```
* ENV Statement
	* Set Environmental Variable 
	```
	ENV DB_HOST=db.production.example.com 
	ENV DB_PORT=5432
	```
* ENTRYPOINT and CMD Statement
	* ENTRYPOINT specifies the start of the command to run
	* CMD specifies the whole command to run
	* Shell form
		```
		nano notes.txt
		``` 	
	* Exec form
		```
		["/bin/nano","notes.txt"]
		``` 
* EXPOSE Statement
	```
	EXPOSE 8080
	``` 
* VOLUME Statement
	* Shared or ephemeral volumes
	```
	VOLUME ["/host/path","/container/path/"]
	VOLUME ["/shared-data"]
	```
* WORKDIR Statement
	* Set the directory container starts in
	```
	WORKDIR /install/
	``` 

* USER Statement
	* Set which user the container will run as
	```
	USER arthur
	USER 1000
	```


