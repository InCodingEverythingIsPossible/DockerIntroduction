# Frontend project

Inside that projects there is Dockerfile (Dockerfile.dev) for dev environment  
There is also production Dockerfile in which we have 2 phases  (multistep build)  
Also docker compose file(yml) appear to avoid long command during running container  
We will also use NGINX (web server) which will take incoming traffic and respond with the files  
There is also Travis yml file which we use for CI/CD development with unit testing and deploying app on AWS

### 3 commands regarding Node js
🚀Node js must be installed on ubuntu instance🚀   
🚀Execute flag must be set on that file node_modules/.bin/react-scripts🚀  

`npm run start` start up a development server, for development use only   
`npm run test` run tests associated with the project  
`npm run build` builds a production version of the application

### Build container from mentioned docker file
`docker build -f Dockerfile.dev .`  

### Run and map ports on container
`docker run -p 3000:3000 {container_id}`

### Run and map ports with bookmarking volumes
`docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app f2bc8218d7`

### After creation of yaml we don't docker run anymore
`docker-compose up`

### After creation of production Dockerfile (multistep build file)
`docker build .` -> we don't need to specify docker file anymore  
`docker run -p 8080:80 53803hdsak` -> 8080 it's our port, 80 nginx default port


