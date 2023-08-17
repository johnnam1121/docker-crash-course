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