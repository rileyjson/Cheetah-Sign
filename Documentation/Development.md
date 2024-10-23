# Setting up the Development Environment

## Overview
This project is run with a node.js web server and in a docker container. This documentation will go over the creation of the
environment in two sections - setting up the web server and setting up the api. Both need to be ran at the same
time for a proper dev environment.

This documentation expects that you are setting up the dev environment on a Windows computer. 

## Prerequisites

You will need access to the repository containing the source code. It contains two projects - Cheetah.Sign.Api (The Back-end)
and cheetahsign-webclient (The Front-end). 

In order to run the program, you will need the following programs already installed:

- IDE of your choice with the ability to docker compose (When writing this documentation, we opted to use Visual Studio Code 
with the Docker compose Extension)

- Front-end:
  - Node.js
  - Vue

- Back-end:
  - .NET 8 SDK
  - Docker Desktop

## Front End Setup

### First Time Setup

Open up windows powershell and navigate to the directory where the source code is stored. Navigate into the
"cheetahsign-webclient" directory.

Run 'npm install'. 

This will install the Vite + Vue client that runs the front end.

### Running the Application

Open up windows powershell and navigate to the directory where the source code is stored. Navigate into the
"cheetahsign-webclient" directory.

Run 'npm run dev'. This will run the Vite + Vue website.

The powershell will display commands. Most importantly, you will use 
- R + enter - Restarts the website.
- O + enter - Opens the website on your default web browser.
- Q + Enter - Quits the service.

### Editing the Application

Everything relating to the front end will be found in the 'cheetahsign-webclient' directory. By default, the app will run
the App.vue file. 

App.vue is a file that inherits HelloWorld.vue, which inherits DailyForecast.vue. You can modify these Vue files to
begin work, or you may make a new Vue file. 

When making a new Vue file, ensure that you edit 'main.ts' to open your newly made
Vue file instead of the old one. You can do this by editing the directory from './App.vue' to the directory of your newly
made vue file.


## Back End Setup

### Running the Application

Open your preferred IDE with the ability to compose. You should run the "docker-compose" startup option.
(You can also right click on the docker-compose.yml file and select "compose up".)

Docker composing will spin up 3 images: 
- cheetah.sign.api
- pgdata
- pgadmin

This will run the api. Currently, the API only runs the weather forecast found on the default website. If the API is not working,
the website will fail to find a forecast.

### Editing the Application

Everything relating to the back end will be found in the Cheetah.Sign.Api directory. Primarily, you will be editing the 
files within the Endpoints directory, where the HTTP POST and GET requests will be sent.

Use this directory to edit the current endpoints or create new files with new endpoints. With the creation of new endpoints,
ensure that you add the new endpoints to the 'Program.cs'.



