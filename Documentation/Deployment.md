# Deployment & Maintenance of Cheetah Sign

## Overview

Our project runs on a node.js web server and has been fully [Dockerized](https://medium.com/@swalperen3008/what-is-dockerize-and-dockerize-your-project-a-step-by-step-guide-899c48a34df6). It contains four Docker images running in a single container. The images include:

- pg-admin: A web-based PostgreSQL database management tool that provides a UI to interact with your PostgreSQL database.
- pgdata: The PostgreSQL database image that stores the application's database setup.
- Cheetah Sign API: The backend for the application, which interacts with PostgreSQL and handles requests from end users.
- cheetahsign.webclient: The frontend for the application

For more information, refer to [Development.md](Development.md).

## Setting Up the Application

As mentioned before, the application is Dockerized. This means the application is in a single container that contains all the code, the server, dependencies, configurations, etc. to run the application. To setup the system you must have [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed on your machine and follow these steps:

1. Follow the instructions to [clone the repository](Development.md#Prerequisites) containing the source code and docker files.

2. Once cloned, open your command line and cd to
   the projects directory. Run the command 'docker-compose up'. This should run the file contained in the root of the project called
   'docker-compose.yml'.

3. Docker compose should spin up the [3 images](Development.md#back-end-setup) on Docker Desktop:

   - cheetah.sign.api
   - pgdata
   - pgadmin

## Deploying the Application

### API Deployment:

- Ensure appsettings.json is up-to-date
- Configure some info like image name/tags etc
- os linux
- arch x64
- run dotnet publish /t:PublishContainer
- Containerize an app with dotnet publish - .NET | Microsoft Learn
- push to Registry (for our case, AWS ECR)
- Configure other server necessities
- Configure/run postgres database server
- Configure port forwarding to route traffic to the correct docker port
- Configure secret environment variables injected via AWS parameter store
- i.e. Database connection string
  (later relevant)
- ensure target server has SSL Certificates for HTTPS traffic
- deploy new task service (for our case, using AWS ECS/EC2)

### Web Deployment:

- run "npm run build" or "vite build"
- Building for Production | Vite
- Configure proxy/rewrites on a static host vendor:
- Render Example
- Env Variables and Modes | Vite
- Deploy to a static host
- Deploying a Static Site | Vite

## Maintenance

## Troubleshooting

Some of the main issues that could come up are usually related to Docker Compose. There are a few commands you can use in the terminal to troubleshoot those issues.

- docker login -u
  
When you first try to run the application with Docker, you will probably get an authentication error. This means your IDE and Docker Desktop are not connected. You must login to Docker Desktop from your IDE to fix this problem. 'docker login -u' will let you enter your Docker username and password. 

- docker ps

This will display all the containers that are running

- docker-compose logs

This will display logs for all images defined in docker-compose.yml.
The errors that you may have run into are typically found in these logs, or can be found displayed in Docker when you select
the service that the error is happening in.
