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
#runs linux commands

CMD ["npm", "start"]