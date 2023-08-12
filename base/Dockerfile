# # Use the official Neo4j image as the base image
# FROM neo4j:4.4

# # Set the environment variables
# ENV NEO4J_AUTH=neo4j/12345678
# ENV NEO4J_dbms_memory_pagecache_size=512M

# # Copy the APOC plugin JAR file into the plugins directory
# COPY apoc-4.4.0.20-all.jar /plugins/

# # Copy the custom Neo4j configuration file into the container
# COPY neo4j.conf /var/lib/neo4j/conf/

# # Copy the index.js file into the container (assuming it's in the same directory as the Dockerfile)
# # COPY index.js /app/

# # Expose the Neo4j ports
# EXPOSE 7474 7687

FROM node:14

WORKDIR /app

# Everytime we use FROM COPY RUN CMD, it creates another image which is based off the previous layer.
# THe image can be cached and only needs to be created again if something changes
# So we are creating a layer that is based off the content file before we run npm insatll
# Means unless we change package.json, the next time we build DOcker will use the cache layer where npm install has already been run
COPY package*.json /app

RUN npm install

#COPY index.js /app/ 

EXPOSE 4000

CMD ["npx", "nodemon", "index.js"]


# Location for docker volume in Windows 11 : \\wsl$\docker-desktop-data\data\docker\volumes
# Docker volume maps the working directory in our contanier to the Docker volume in our machine
