# Creating Docker Image from Node + Express Application

### Create Node Express Application: https://github.com/sarth99016/C0883191_ClassAssignment_3

### Create Dockerfile in the project and copy the following code in the file

```
# syntax=docker/dockerfile:1
FROM node:18-alpine
LABEL maintainer "muralimeruga@gmail.com"
LABEL build_date "2024-02-06"
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["node", "app.js"]
```

### Create Docker Image using following command

```
docker build --tag c0882902-node-assignment3 .
docker images
```

### Run the created Image using below commands

```
docker run --detach --publish 3000:3000 c0882902-node-assignment3:latest
docker run --detach --publish 3001:3000 c0882902-node-assignment3:latest
docker ps
```

### Stop container using below commands

```
docker stop vigilant_pare
docker stop sad_lederberg
docker ps
docker ps -a
```

### Remove existing continers using below commands

```
docker rm 2b85acbe2eca
docker rm 98f12c58ce44
docker ps -a
```

### Run the continers using environment variables

```
docker run --detach --publish 3000:80 -e PORT=80 c0882902-node-assignment3:latest
docker run --detach --publish 3000:80 -e PORT=80 -e NAME=C1 c0882902-node-assignment3:latest
docker run --detach --publish 3001:8080 -e PORT=8080 -e NAME=C1 c0882902-node-assignment3:latest
```

### Run the continers using environment variables using file

```
docker run --detach --publish 3000:3000 --env-file my-env.txt c0882902-node-assignment3:latest
```

### Tag your recently created image to publish on DockerHub registry

docker image tag c0882902-node-assignment3:latest muralimeruga/c0882902-node-assignment3:1.0.0
docker images
docker login
docker push muralimeruga/c0882902-node-assignment3:1.0.0

### Pull and run the recently pushed image on local docker environment
docker pull muralimeruga/c0882902-node-assignment3:1.0.0
docker run -d -p 3000:3000 muralimeruga/c0882902-node-assignment3:1.0.0
