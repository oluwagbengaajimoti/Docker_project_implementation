## Docker Compose


Docker Compose is a tool used for defining and running multi-container Docker applications. It allows you to define a multi-container Docker application using a YAML file (docker-compose.yml) where you can specify the services, networks, and volumes required for your application to run.

With Docker Compose, you can define the configuration for multiple services, their dependencies, networking, and volumes all in one place. This simplifies the process of managing and deploying complex applications that consist of multiple interconnected containers.

### Some key features of Docker Compose include:

Declarative Configuration: Docker Compose uses a simple YAML file format to define the services, networks, and volumes required for your application. This allows you to declare the desired state of your application's infrastructure.

Service Orchestration: Docker Compose manages the lifecycle of the containers defined in the docker-compose.yml file, handling tasks such as container creation, starting, stopping, and removal.

Networking: Docker Compose creates a default network for your application, allowing the containers defined in the docker-compose.yml file to communicate with each other using service names as hostnames.

Volumes: Docker Compose can manage volumes, which allow data to persist beyond the lifecycle of a container. This is useful for storing application data or configuration that needs to be shared between containers.

Environment Variables and Overrides: Docker Compose allows you to specify environment variables for your services, as well as override any configuration settings defined in the docker-compose.yml file.

Below is an example of docker docker file structure for the MongoDB and Mongo-Express isolate network connection.


```
# Mongo-docker-compose.yaml
version: '3'
services:
    mongodb: #container name
        image: mongo
        ports: 
            - 27017:27017
        environment:
            - MONGO_INITDB_ROOT_USERNAME=admin
            - MONGO_INITDB_ROOT_PASSWORD=password
    mongo-express:
        image: mongo-express
        ports:
            - 8081:8081
        environment:
            - ME_CONFIG_MONGODB_ADMINUSERNAME=admin
            - ME_CONFIG_MONGODB_ADMINPASSWORD=password
            - ME_CONFIG_MONGODB_SERVER=mongo
```
To run docker compose file on an interactive terminal, ensure you are within the directory where your  docker-compose file is located, or specify the file location. we use the command line below:

```
docker-compose -f Mongo-docker-compose.yaml up
```
To stop all the containers created by docker-compose, we use the command below instead of stoping one after the other.

```
docker-compose -f Mongo-docker-compose.yaml down
```
To stop all the