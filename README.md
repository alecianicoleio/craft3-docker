
# Craft 3 in Docker
A reusable and flexible base for starting Craft 3 projects using Docker

## Prerequisites
Make sure [Docker Desktop](https://docs.docker.com/docker-for-mac/install/) is installed on your development machine.

## Setup
1. Clone this repo.
2. `cd` into your new project directory.
3. run `docker-compose build` to build your image, and install composer and dependencies. This will take a few minutes to complete.  NOTE: In our docker-compose.yml we told nginx to listen for incoming traffic on port 80 by binding it to our localhost's port 80. (If you see an error stating that a 'port is already allocated' it is likely because you already have something running which is listening for incoming traffic - MAMP, Apache, nginx or something similar. You'll need to find that and close it before continuing -OR- change the port binding for nginx in docker-compose.yml to something like - 8080:80 to listen on 8080 instead.)
4. Now run `docker-compose up -d ` to create a container and run in the background.
5. Open [http://localhost/admin](http://localhost/admin). You should see a fresh craft installation page!

## Development
While in development we want to be able to watch for file changes and recompile when a change is detected.
To watch for changes, run `docker-compose up buildchain`.

## Craft 3 Image Assets
Set up an image source like below:
1. Define a new asset source by going to http://localhost/admin > Settings > Volumes
2. Click the '+ New Volume' button.
3. Set the Name to `Local`.
4. Set the handle to `local`.
5. Toggle public urls to on,.
6. Set the Base URL to `@web/images`.
7. Set the Volume Type to ‘Local Folder’.
8. Set the File System Path to `/var/www/html/web/images`.
Craft should now be able to process image uploads to this directory!

## Additional Resources
* This project was set up by following [this guide](https://mattgrayisok.com/a-craft-cms-development-workflow-with-docker-part-1-local-development) by [mattgrayisok](https://mattgrayisok.com/).
* Find the official Docker Documentation [here](https://docs.docker.com/).
* Find the official Craft 3 Documentation [here](https://docs.craftcms.com/v3/).
* Interested in setting up custom local urls for your Docker projects? Check out [this article](https://medium.com/@francoisromain/set-a-local-web-development-environment-with-custom-urls-and-https-3fbe91d2eaf0) on setting up a reverse-proxy to route urls to specific Docker containers.
