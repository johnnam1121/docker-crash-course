Docker - Net Ninja Notes

Lesson 1
What is Docker?

Makes it easier to run applications buy putting things in containers
Scenario.. I made a node 17 application. I want to share with others. They would need Node 17 + all other app dependencies just to run it. This is where Docker comes in..

It puts the app in a container which includes Node 17, dependencies, and the source code. that way anyone can run it since the container contains everything you need to run it. Pretty neat. Therefore the ONLY thing the other person will need is Docker just to be able to run the container.

Dockers containers vs virtual machines
VMs are generally slower since it has its own fully running OS. Containers share the hosts OS. They both can solve the same problem theoretically but Docker will be faster.

INSTALLATION
Holy crap that was complicated. Follow the guide here:

https://www.youtube.com/watch?v=8Ev1aXl7TGY&list=PL4cUxeGkcC9hxjeEtdHFNYMtCpjNBm3h7&index=3&ab_channel=TheNetNinja

tldr Docker desktop should be running in the background for it to work properly

Lesson 3
Images and Containers

Images are like blueprints for containers and contains the following (these things are NOT currently running)
- Runtime Env
- App code
- Dependencies
- extra configs like env variables
- commands

Once you create an image you CANNOT change it. You must create a new one instead.

Containers are runnable instances of those images. They run as an isolated process.

Lesson 4 Images
You use layers in the image. the order of the layers does matter

First is generally the parent image which includes the OS and sometimes the runtime env

After that you put stuff like source code or dependencies.

Docker HUB is like the npm thing but for docker. We can download images and stuff from here. We can download the parent images here

docker pull node - this command can be typed anywhere. It will download the parent image for node into docker

Lesson 5
Dockerfile guide
Each line is a seperate instruction

# Parent Image
FROM node:17-alpine

# This makes it so all the next instruction suse this working directory
WORKDIR /app

# copy stuff from root folder which includes the package.json for dependencies
COPY . .

# installs the dependencies
RUN npm install

# port must be specified
EXPOSE 4000

# runs the container by doing this syntax is the same as node app.js
CMD ["node", "app.js"]

Lesson 6
dockerignore guide
basically the same thing as gitignore

Lesson 7
starting and stopping containers

Lesson 8
Layer chaching
Basically the steps docker takes in order to create the image
ex: step 1, node parent image
2, go to workdir
3, copy dir
4, run npm install

When you try to build an image, it stores the layer in the cache. so when you change one small thing, the cached version will be called and the build will run a lot faster
Even if you run some layers in different orders, the cached versions will run first really quickly making it efficient.

Lesson 9
Managing Images and Containers
Basically how to check images/containers and how to remove them

Lesson 10
Volumes
Basically making another container as like a sandbox so you can get immediate changes

Lesson 11
Docker Compose
helps you define and share multi-container applications