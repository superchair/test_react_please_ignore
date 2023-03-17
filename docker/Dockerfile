# STAGE 1 - build react project
FROM node:16-alpine AS build

# set working directory for building the project
WORKDIR /test_react_please_ignore

# copy project files to working directory
COPY . .

# gather dependencies
RUN npm install

# run the test suite
RUN CI=true npm test

# build the react project
RUN npm run build


# STAGE 2 - build deployable image
FROM nginx:1.21 AS production

# Expose HTTP port
EXPOSE 80

# Copy built files from build environment
COPY --from=build /test_react_please_ignore/build /usr/share/nginx/html