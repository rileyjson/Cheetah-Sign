# Setup of the Development Environment

## Overview

This project is run with a node.js web server and is fully Dockerized. This documentation will go over the replication of the development
environment using Docker. We were provided with a template that already had the Postgres database and API Dockerized, but we had to Dockerize the frontend ourselves.

This documentation goes through setting up your development enviroment on Windows, but it should be the same for MacOS.
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
two project folders - Cheetah.Sign.Api (backend) and cheetahsign-webclient (frontend).

### Installation Prerequisites

In order to run the program, you will need the following programs installed:

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

Open your preferred IDE with the ability to docker compose and your Docker Desktop application. We are using VSCode, so you will want to install the [Docker Extension](https://code.visualstudio.com/docs/containers/overview) to run it in the way presented. Now you should right click on the docker-compose.yml file and select "compose up". This can take some time to build your containers.

**Note: If this fails with an authentication error, you might have to login to your Docker account in the Visual Studio Code terminal to connect them.**

The command is:
docker login -u \<username\>

You will then be asked for your Docker password. (you will not see your password as you type it in)

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

Everything relating to the frontend for administrators will be found in the 'cheetahsign-webclient' directory. For now, the page where users will sign documents lies in this directory as well. App.vue is the template page that all of our components inherit from. This also contains our vue router to allow for navigation between different parts of the application.

Vue follows a component-based architecture. So, everything we make on the frontend is based around our components. For example, each of our different sections in our webpage is a separate component. Also, the modals we use on 3 of the sections are all one component! We don't have to make 3 separate modals in each of these Vue files. We make one modal and each component inherits the modal component into their own Vue file. This is how you use Vue to work with the UI.

Another piece of the frontend puzzle are the API calls that are made to talk to our backend. The way this is done falls into our 'sdk' folder in the webclient directory. Each of the classes located in these 'client' files contain a variety of asynchronous methods that we can call in our Vue components. If they're HTTP GET requests, they just contain the endpoint to talk to the backend. If they're an HTTP post request, they also will contain a body to be sent. Like if you were sending a file to the backend, so it could then be saved to the database.

### Editing the Backend

Everything relating to the backend will be found in the Cheetah.Sign.Api directory. Primarily, you will be editing the files within the Endpoints directory, where the HTTP POST and GET requests will be sent.

Use this directory to edit the current endpoints or create new files with new endpoints. With the creation of new endpoints,
ensure that you add the new endpoints to the 'Program.cs'.

If you want to edit the database, refer to the Contexts folder with the file [AppDbContext](https://sbelialov.medium.com/quick-and-easy-dbcontext-setup-in-net-70e2211be8f4). This file is used to define
your database tables and data. Also, you can define and edit tables within the 'sign-pgadmin' port on Docker (you can find the login info in the docker compose file). Your tables should automatically be created when you run the application. This are based off our latest database migrations found in the 'migrations' folder.

## Accessing the Application & How to Test

Once you have Docker Desktop running the containers for the API, Postgres, and the web client,
you can access the application. Navigate to the URL http://localhost:8080/

This URL is given to you in the terminal of your
Docker container on Docker Desktop after running 'Compose Up'. To test if the application is running
correctly, attempt to upload a document. If the
list under 'Uploaded Documents' populates with your file, your environment is set up correctly.

## Project & Folder Structure

### Frontend (cheetahsign-webclient & cheetahsign-clientside)

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
  This is another piece of our Microsoft Entity Framework setup. This folder contains our AppDbContext, which is a class that serves as a bridge between your application and the database. It is responsible for managing your database tables and data. This also contains the database fixture that is used in testing.

### Important Files

- Program.cs & appsettings.json
  <br>
  These files are where we configure our connections to our database, enviroment variables, our HTTP request pipeline,
  automatic database setup, etc.
