---
created: 1970-01-01T08:00
updated: 2024-05-15T19:17
---
	## Concept
- `Docker0` : một bridge interface được tạo ra (mặc định) khi cài đặt docker trên máy host. Hoạt động như một switch ảo có nhiệm vụ thực hiện kết nối cung cấp giao tiếp giữa các container, với nhau, container với host.
	- Mỗi container khi được tạo ra Docker sẽ gán địa chỉ IP trong subnet của `Docker0` và kết nối với bridge này.
- `Docker Server(Docket Daemon)`: thực hiện hết tất cả logic liên quan đến crud containers, images.  
- `Docker Client(CLI)`: 

## Image:
- Build image from Docker-file:
```bash
docker build -t <image-name> <path-contain-docker-file>
```
	--no-cache to clear all the cache of the previous build
- List docker images:
```bash
docker images
```
- Remove docker image:
```bash
docker rmi -f <image-namme-or-id>
```
## Container:
- Run container from an image
```bash
docker run -dp <host-port>:<container-port> --name <container-name> <image-name-or-id>
docker run -dp <host-port>:<container-port> -v /path/on/host:/path/in/container <image-name-or-id>
docker run -dp <host-port>:<container-port> -e NODE_ENV=production myapp
```
	-d make container run in background
	-v to mount volumes
	-e to specify env
- Stop running container:
```bash
docker stop <container-name-or-id>
```
- Remove container:
```bash
docker rm <container-name-or-id>
```
- Container running: 
```bash
docker ps -a
```
	-a to including those that are stopped
- Execute a command in an active container:
```bash
docker exec <container-name-or-id>
```
	env to list all env variables
	 -it to get into a running container, along with shell like bash (or sh for alpine image)
	
- Show all logs in the in the container:
```bash
docker logs <container-name-or-id>
```
	-t logs with timestamps
- Control the state of the container:
```bash
docker start <container-name-or-id>
docker stop <container-name-or-id>
docker restart <container-name-or-id>
```

## Other:
- Vim be good
```bash
docker run -it --rm brandoncc/vim-be-good:stable
```
- Check total storage that docker using:
```bash
docker system df
```
- delete all data relate to container, network, image, build cache:
```bash
docker system prune -a
docker builder prune //only build cache part 
```
