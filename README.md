
## Docker

# Dockerfile explanation 

# FROM is used to pull image from docker hub
FROM node:18-alpine3.15

# The WORKDIR command is used to define the working directory of a Docker container at any given time. The command is specified in the Dockerfile.
# Any RUN, CMD, ADD, COPY, or ENTRYPOINT command will be executed in the specified working directory.
WORKDIR /app

# ENV PORT=3000
#setting environment variables
#we can pass environment variables here in Dockerfile or directly pass from docker-compose.yml file

COPY ./app /app/
# Copies local(Host)folder to container  

RUN npm install
# runs linux commands

CMD ["npm", "start"]

----------------------------------------------------------------------

version: "3.8"
# version of docker-compose (needs to set according to docker engine version)

services:
# we can create multiple services, basically services are nothing but images that run in same network
# services can be named anything like this - backend, frontend, database etc etc
  backend:
    build: ./backend
    ports:
      - 3000:3000
    environment:
      - PORT=3000

  database:
    image: mongo:4.0-xenial
    ports:
      - 27017:27017
    volumes:
      - devops:/data/db

volumes:
  devops:
# setting volumes for data persistance


### For running this application you just need to fire the command "docker-compose up" where the docker-compose.yml file exist and docker will take care of everything and start the application. Then you can access the ports and see the output. for database you may need to see for clients that supports database query. for example mongo we have mongo compass for Mac M1.