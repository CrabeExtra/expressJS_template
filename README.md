In this file I will outline the process that went into creating this project as a list of steps provided by Marcos Henrique da Silva in more detail.

in terminal:
    npm init
    npm i express debug winston express-winston cors
    npm i --save-dev @types/cors @types/express @types/debug source-map-support tslint typescript
creating files:
    /app.ts
    ./common/common.routes.config.ts
    ./users/users.routes.config.ts

Abstract classes are used for when we need a similar functionality for many things (such as API endpoints), but each one requires a slightly different func logic.

scripts are added to package.json for npm start and npm run debug -> in addition the tsconfig.json is created, this ensures that tsc (compiling typescript creates a new version of the entire directory structure rather than creating a copy js file next to each ts file in the same directory)

Make requests using postman (post localhost:3000/users or get localhost:3000/users/12345 etc.)

Next we refer to middleware, models and services. The dto folder and the ./users/dto/create.user.dto.ts file are created. refer to the definition of a DTO.

then ./users/dto/patch.user.dto.ts is created along with ./users/dao/users.dao.ts

lines into terminal:
    npm i shortid
    npm i --save-dev @types/shortid

All crud operations relating to the dto files are handled in functions in the users.dao.ts file.

Next the inerfaces folder is created in common with crud.interface.ts 

then the services folder is created in users with users.service.ts

In many IDEs the services file can be automatically generated using the CRUD class import.

Next in terminal:
    npm i argon2 
for hashing passwords

Then created:
    ./users/controllers
    ./users/controllers/users.controller.ts
    ./users/middleware
    ./users/middleware/users.middleware.ts

At this point, all is functioning, but an in-memory database is being used, next is to integrate an external (persistent) database such as MongoDB 

docker is installed to the OS and docker.compose.yml is created.

next in terminal (windows):

    docker-compose up -d 

or in ubuntu:
    sudo docker-compose up -d

This errors if docker itself isn't running (and running as administrator)

to shut down the docker:
    docker-compose down 

next:
    npm i mongoose

keep in mind, using MONGO, _id is inherent so replace id with _id

the CRUD system in users.dao.ts is reconstructed