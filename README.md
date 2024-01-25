NODE-APP
Create a new directory for your project and navigate into it:
mkdir my-nodejs-app
cd my-nodejs-app

Initialize a new Node.js project by running:
npm init -y

Install Express.js:
npm install express

Create a file named app.js and open it in a text editor. Add the following code:
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello, this is your Node.js app!');
});

app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});

Save the file and run your Node.js app:
node app.js

DOCKER
Dockerfile
# Use an official Node.js runtime as a base image
FROM node:14

# Set the working directory to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the current directory contents into the container at /app
COPY . .

# Expose port 3000 to the outside world
EXPOSE 3000

# Define the command to run your app using node
CMD ["node", "app.js"]

This Dockerfile does the following:

Uses the official Node.js 14 base image from Docker Hub.
Sets the working directory inside the container to /app.
Copies package.json and package-lock.json to the working directory and installs the app dependencies.
Copies the entire content of the current directory into the container at /app.
Exposes port 3000 for external access.
Sets the default command to run your app using node app.js.

Build the Docker image:
docker build -t my-nodejs-app .

Run the Docker container:
docker run -p 3000:3000 my-nodejs-app
