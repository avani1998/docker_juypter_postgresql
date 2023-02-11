#Installations
- [Install Docker Desktop](https://www.docker.com/get-started/) and follow instructions to setup Docker and Docker Hub. 

- [Install Anaconda](https://www.anaconda.com/)

# Docker
To check if docker is running, type in terminal
```bash 
docker ps
```
This command will show all the containers, the time of creation, port they are running on and the container names.

# Run Jupyter on Docker
To launch Jupyter Notebook on Docker, create a new container containing the Jupyter Notebook image. Jupyter already has an image on Docker. To launch Jupyter we need the correct CLI command which can be found on [Jupyter's Docker Stacks documentation](https://jupyter-docker-stacks.readthedocs.io/en/latest/)

```bash 
docker run -p 10000:8888 jupyter/scipy-notebook:85f615d5cafa 
```

``` -d ```  flag tells docker to run the container in detached mode (in the background)  
``` -p 1000:8000 ```  creates a mapping of port 1000 on your local environment to the port 8000 on the container  
``` jupyter/scipy-notebook:85f615d5cafa ```   is the name of the container  

This command does two things one after the other: 
  1. Pulls the jupyter/scipy-notebook image from the Docker Hub
  2. Creates a container with this image and runs runs it on port 8000 of the container. 

Visitng ``` http://<hostname>:10000/?token=<token> ``` in a browser will load Jupyter Notebook, where 
- hostname is the name of the computer running Docker
- token is the secret token printed in the console.
