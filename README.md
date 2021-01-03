# Udacity Microservices Project

A simple cloud application which allows users to register and log into a web client, view and post photos to the feed.

The project consists of the following subprojects:
1. Frontend Application
2. User microservice
3. Feed microservice
4. Reverse proxy

## Run locally
You can run the whole application using Docker Compose. The Docker Compose files are in `deploy/local`.

To run it you need to: 
1) Set the environmental variables `POSTGRES_USERNAME`, `POSTGRES_PASSWORD`, `POSTGRES_DB`, `POSTGRES_HOST`, 
   `AWS_REGION`, `AWS_PROFILE`, `AWS_BUCKET` and `JWT_SECRET`.
2) Go to `deploy/local`
3) `docker-compose -f docker-compose-build.yaml build --parallel`
4) `docker-compose up`
5) Open http://localhost:8100 in your browser.

## Run apps individually locally
If you need to make any changes, you may want to run the apps individually locally.

To run a backend microservice:
1) Go to the backend microservice folder
2) `npm install`
3) `npm run dev`

To run the frontend:
1) Go to `udagram-frontend`
2) `npm install`
3) `ionic build`
4) `ionic serve`

## Run in Kubernetes

Inside the `deploy/local` file you will find the kubernetes files needed to run the application. You will need to first 
add the secrets in kubernetes. You can do that by executing: `kubectl create secret generic secrets --from-literal=postgresUsername=myPostgresUsername 
--from-literal=postgresPassword=myPostgresPassword`. Then you can apply the rest of the files to your cluster.

## Note for running the apps either locally or kubernetes
You will need to change the `apiHost` in `environment.prod.ts` in `udagram-frontend` to point to the backend reverse proxy url.

## Travis CI
The project is configured to automatically run in Travis CI to build the docker images and push them in DockerHub. 
