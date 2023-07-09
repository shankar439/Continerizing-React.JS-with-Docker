<h1 align="center"> Containerizing React App using Docker </h1>
<h2 align="center"> Containerizing/Dockerize React application to deploy it in Kubernetes or in other environment in container form. </h2>

![imagegit](https://github.com/shankar439/Images/assets/70714976/b27af22b-c4a8-443d-af66-00978c2930a8)

## Why we need to Containerize application and what are the advantages of it ?. 
  - `Any one can adopt to Containerization as the development and deployment need to be faster these days, this will be the right choose.`
  - ### Pros
    - `Portability` - Containers encapsulate applications and their dependencies making them run consistently in any environment that supports containerization.
    - `Isolation` - Containers provide a level of isolation between applications and their host environment makes them considering them as a separate vm.
    - `Scalability` - Containers allow applications to scale easily. By leveraging container orchestration platforms like Kubernetes, you can dynamically manage and scale containers based on demand.
    - `Faster Deployment and Rollback` - Since the containerized application includes all its dependencies, deployment becomes a matter of spinning up new containers. If an issue arises, rolling back to a previous version is straightforward by redeploying the earlier container image.
  - ### Cons
    - Debugging and Troubleshooting, Resource optimization and Learning curve make containers little challenging. 

### prerequisite
  - Any Operating System with Docker pre installed.
  - A sample React application.
  - NodeJs with any version that optimal to the react application.

<br>
<br>



<h1 align="center">Lets Begin </h1>

- `This will be a quick tutorial.`

- Open the react application in your favorite IDE i will open it in VS code.

<h2 align="center">Create a Docker file </h2>

- In the Project structure create a file with name `Dockerfile`, make sure the name of the file should be exactly like this.
- Inside the `Dockerfile` insert the below statements.

```
FROM node:20.3.1-alpine
RUN mkdir -p /usr/src/
WORKDIR /usr/src/
COPY . /usr/src/
RUN npm install
EXPOSE 3000
CMD npm run start
```

## Explanation

- `Line 1` - As every Docker image need to be created from a base docker image, here i am using node as a base image to run my React application.
- `Line 2` - Lets create directory `/usr/src/` .
- `Line 3` - Make the directory as current working directory.
- `Line 4` - Copy all file and folders to docker working directory.
- `Line 5` - Install the needed dependencies mentioned in package.js.
- `Line 6` - Here we exposing the image at port 3000.
- `Line 7` - This command that will be executed when the container starts.


<br>
<br>


<h2 align="center">Let's Create a Docker Image </h2>

- Run the docker desktop before executing Docker commands.
- In the terminal enter the below cmd to build the Docker image.

```
docker build -t reactapp:1 .
```

- Check if the image is created, using the below cmd
```
docker images
```

- If the image exist run the docker image to in detached mode at port 80, as we are exposing the imaged at port 80.
```
docker run -d -p 3000:3000 reactapp:1
```

- Once we run the docker image it is considered as container.
- To see the running containers use the below cmd .
```
docker ps
```

- If our React application is running lets check it in chrome using the localhost:3000.

<br>
<br>



<h2 align="center">Conclusion</h2>

- We have seen what is containerization and its advantages.
- Build an artifact of our react application using npm
- We created a Dockerfile and created a Docker image
- And we have run the Docker container and accessed it in chrome.



<br>

# END