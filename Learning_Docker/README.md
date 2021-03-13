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
		docker rm <imageName:imageTag/imageId>
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
