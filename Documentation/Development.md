# Setup of the Development Environment

## Overview

This project is run with a node.js web server and is fully Dockerized. This documentation will go over the replication of the development
environment using Docker. We were provided with a template that already had the Postgres database and API Dockerized, but we had to Dockerize the frontend ourselves.

This documentation expects that you are setting up the dev environment on a Windows computer.
If any problems occur during this process you can email riley.jamison@bsu.edu for assistance.

## Prerequisites

### Cloning the Repository

You will need to access and clone the repository containing the source code. Our repository can be
found here:
https://bitbucket.org/accutechcapstone/bsu.cheetah.sign/src/main

Once you're on the repository you can click 'Clone'. This will give you a
link you can use to clone into the repository.
![cloning](./images/Cloning.png)
After copying the link, open your terminal or IDE and cd into your directory
of choice. Once in your directory, paste the link to clone the repository. If
you run into any access errors you can get assistance by reaching out to
riley.jamison@bsu.edu.

Once you have cloned into the repository, you will see
two projects - Cheetah.Sign.Api (The Back-end)
and cheetahsign-webclient (The Front-end).

### Installation Prerequisites

In order to run the program, you will need the following programs already installed:

- Install [Docker Desktop](https://www.docker.com/products/docker-desktop/). This application lets you build and run your containerized applications.

- IDE of your choice with the ability to docker compose (When writing this documentation, we opted to use Visual Studio Code
  with the Docker compose Extension)

- Front-end:

  - Node.js 20
  - Vue 3
  - Vite 5

- Back-end:
  - .NET 8 SDK
  - [Docker Desktop](https://www.docker.com/products/docker-desktop/)

## Replicating via Docker

### Building The Docker Containers

Open your preferred IDE with the ability to docker compose and your Docker Desktop application. We are using VSCode so you will want to install the [Docker Extension](https://code.visualstudio.com/docs/containers/overview) to run it in the way presented. Now you should right click on the docker-compose.yml file and select "compose up". This can take some time to build your containers.

![dockerCompose](./images/dockerCompose.png)

You will know if the build was successful because your container names will appear in your terminal and
Docker Compose will spin up 4 images:

- sign-pgdata
- sign-pgadmin
- sign-api
- bsucheetahsign-cheetahsign-webclient-1

This is how it will appear on Docker Desktop:
![dockerContainer](./images/DockerContainer.png)

### Editing the Frontend

Everything relating to the front end will be found in the 'cheetahsign-webclient' directory. By default, the app will run
the App.vue file.

App.vue is a file that inherits HelloWorld.vue, which inherits DailyForecast.vue. You can modify these Vue files to
begin work, or you may make a new Vue file.

When making a new Vue file, ensure that you edit 'main.ts' to open your newly made
Vue file instead of the old one. You can do this by editing the directory from './App.vue' to the directory of your newly
made vue file.

### Editing the Backend

Everything relating to the back end will be found in the Cheetah.Sign.Api directory. Primarily, you will be editing the
files within the Endpoints directory, where the HTTP POST and GET requests will be sent.

Use this directory to edit the current endpoints or create new files with new endpoints. With the creation of new endpoints,
ensure that you add the new endpoints to the 'Program.cs'.

If you want to edit the database, refer to the Contexts folder with the file [AppDbContext](https://sbelialov.medium.com/quick-and-easy-dbcontext-setup-in-net-70e2211be8f4). This file is used to define
your database tables and data.

## Accessing the Application & How to Test

Once you have Docker Desktop running the containers for the API, Postgres, and the web client,
you can access the application. Navigate to the URL http://localhost:8080/

This URL is given to you in the terminal of your
Docker container on Docker Desktop after running 'Compose Up'. To test if the application is running
correctly, attempt to upload a document. After uploading click the 'refresh files' buttons. If the
list under 'Uploaded Documents' populates with your file, your enviroment is setup correctly.

## Project & Folder Structure

### Frontend (cheetahsign-webclient)

- Components
  <br>
  This contains all of our Vue components. Components are reusable pieces of code that encapsulates a specific part of the UI. As of now these contain the different parts of our page. We have one for our weather forecast and document uploading form.

- Service-Base
  <br>
  Within our SDK folder, our service base folder contains our service base file and our axios setup file. These are both an integral part of our application. Axios is a popular JavaScript library used for making HTTP requests. Our service base file adds to that and is like a template. In our case, it is designed to help us reuse HTTP methods across other classes, avoiding duplication of code.

- Upload
  <br>
  Our upload folder contains our data models (interfaces) and our Upload document client. Our Upload document client extends our service base and is used to setup our HTTP requests. For example, when doing a post request we make an asynchronous method that takes an argument and a return type (a string in our case). We define our endpoint and our argument is used as the post body. This is then sent to the backend.

![asyncMethod](./images/asyncMethod.png)

### Backend (Cheetah.Sign.Api)

- Endpoints
  <br>
  Our Endpoints folder contains the file that receives the requests from the frontend and returns a response. This file also contains our Data Transfer Objects (DTO), these are used to transfer data between different parts of an application.

- Migrations
  <br>
  The Migrations folder contains our migrations that come from our Microsoft Entity Framework setup. Migrations represent changes to your database schema over time and provide a way to apply or revert those changes. Think of them like a version control for your database structure.

- Contexts
  <br>
  This is another piece of our Microsoft Entity Framework setup. This folder contains our AppDbContext, which is a class that serves as a bridge between your application and the database. It is responsible for managing your database tables and data.

### Important Files

- Program.cs & appsettings.json
  <br>
  These files are where we configure our connections to our database, enviroment variables, our HTTP request pipeline,
  automatic database setup, etc.
