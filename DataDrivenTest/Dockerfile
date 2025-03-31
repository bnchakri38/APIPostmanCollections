# Use the official Node.js 20 image as the base image
FROM node:22

# Set the working directory in the container
WORKDIR /app

# Install Newman globally
RUN npm install -g newman newman-reporter-html newman-reporter-htmlextra

# Ensure the results directory exists
RUN mkdir -p /app/results

# Copy your Postman collection, environment, and data files to the working directory
COPY DataDrivenAPIsCollection.json /app/
COPY GoRestAPIEnvironment.json /app/
COPY myuser.csv /app/

# Set the command to run Newman with Data-Driven testing
CMD ["newman", "run", "/app/DataDrivenAPIsCollection.json", "-e", "/app/GoRestAPIEnvironment.json", "-d", "/app/myuser.csv", "-r", "cli,json,html,htmlextra", "--reporter-htmlextra-export", "/app/results/gorest.html"]