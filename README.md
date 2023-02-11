# Installations
- [Install Docker Desktop](https://www.docker.com/get-started/) and follow instructions to setup Docker and Docker Hub. 

- [Install Anaconda](https://www.anaconda.com/)

# Docker
To check if docker is running, type in terminal
```bash 
docker ps
```
This command will show all the containers, the time of creation, port they are running on and the container names.

### Image 1

# Run Jupyter on Docker
To launch Jupyter Notebook on Docker, create a new container containing the Jupyter Notebook image. Jupyter already has an image on Docker. To launch Jupyter we need the correct CLI command which can be found on [Jupyter's Docker Stacks documentation](https://jupyter-docker-stacks.readthedocs.io/en/latest/)

```bash 
docker run -p 10000:8888 jupyter/scipy-notebook:85f615d5cafa 
```

`-d`  flag tells docker to run the container in detached mode (in the background)  
`-p 1000:8000`  creates a mapping of port 1000 on your local environment to the port 8000 on the container  
`jupyter/scipy-notebook:85f615d5cafa`   is the name of the container  

This command does two things one after the other: 
  1. Pulls the jupyter/scipy-notebook image from the Docker Hub
  2. Creates a container with this image and runs runs it on port 8000 of the container. 

Visitng `http://<hostname>:10000/?token=<token>` in a browser will load Jupyter Notebook, where 
- hostname is the name of the computer running Docker
- token is the secret token printed in the console.

Or, using the links provided at the end of the terminal output of the docker run commad can be used to launch Jupyter Notebook. 
### Image 2

Now, executing  `docker ps`  we see that a new entry has been made in the table. 

# Check Docker's working directory
While your container is running

# Copy .csv file into Docker
While your container is running, open another terminal and your csv file into the container. Here I am using [Goodreads-book](https://www.kaggle.com/datasets/jealousleopard/goodreadsbooks) csv from Kaggle. My downloaded csv is located in my Downloads folder.


# PGAdmin
Now, you have to install PGAdmin, a web-based GUI tool used to manage PostgreSQL databases and services. You can install PGAdmin to check whether your Docker Containers are working fine and execute SQL queries on databases present in PostgreSQL.

To install PGAdmin do the follwoing:
1. Search Docker Hub for PGAdmin and pull the Image
```bash
docker pull dpage/pgadmin4
``` 
2. Run the container using 
```bash
docker run --name my-pgadmin -p 82:80 \
  -e 'PGADMIN_DEFAULT_EMAIL=user@domain.local' \ 
  -e 'PGADMIN_DEFAULT_PASSWORD=postgresmaster' \
  -d dpage/pgadmin4
```
  Replace PGADMIN_DEFAULT_EMAI and PGADMIN_DEFAULT_PASSWORD with your email address and a password of your choosing. These detials will be used to log    into the PGAdmin webpage.  
  
  3. Once the container is up and running, visit Docker Desktop and clcik on the port link against the "my-pgadimn" container. Enter the credentials you used to create the container.

# Display the databases in PostgresQL
1. While your PostgresQl container is runnign, log into the docker container using -------
2. Log into the terminal based front end of Postgres using 
  ```bash
  psql -U postgres
  ```
3. Type `\l` or `\list` to print all databeses in PostgresQL
