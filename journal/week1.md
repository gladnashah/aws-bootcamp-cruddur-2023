# Week 1 — App Containerization

This week I learned the advantages of containerazing applications. Not only is containerazing applications more portable, but it generally makes work easier for everyone, improving the efficiency of the whole application delivery process.

The fact that many images are stored on the [Docker Hub](https://hub.docker.com/) means that someone does not need to spend a lot of time building an already existing image, they can just download it, thereby saving a lot of time.

## Required Homework

### 1. Create a new GitHub repo
![gladnashah-aws-bootcamp-cruddur-2023](https://user-images.githubusercontent.com/17044063/222890124-2f8fe798-0acf-443c-8b37-3d5cdfd99f7c.png)

### 2. Launch the repo within a Gitpod workspace
![Welcome-aws-bootcamp-cruddur-2023-Gitpod-Code](https://user-images.githubusercontent.com/17044063/222890172-6e222a3f-7d5c-4196-afbd-8d15a8576b91.png)

### 3. Configure Gitpod.yml configuration, eg. VSCode Extensions
I was able to configure the Gitpod .yml extensions. The extensions I configured are:
#### a) Open API
#### b) Postgres Database

![image](https://user-images.githubusercontent.com/17044063/225551778-03c15f37-bcbe-48a0-8aa1-1795b56f119f.png)


### 4. Explore the codebases

I was able to explore the Github Codebases as shown below
![image](https://user-images.githubusercontent.com/17044063/225560350-fb99ff36-0cfb-45f4-95b6-cb05df2dd083.png)


### 5. Ensure we can get the apps running locally
This is the app's frontend

![Cruddur](https://user-images.githubusercontent.com/17044063/223426709-6ff37ff8-a793-441c-8305-433fb9249eea.png)

This is the app's backend

![https-4567-gladnashah-awsbootcampc-z9i49zzlfsd-ws-eu89-gitpod-io-api-activities-home](https://user-images.githubusercontent.com/17044063/223427062-d1856386-f54d-4c91-bfec-6b81610b31f3.png)



### 6. Write a Dockerfile for each app

I was able to write a docker file each app.

**On the backend, I used the code below:**
``` ruby
FROM python:3.10-slim-buster

WORKDIR /backend-flask

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

ENV FLASK_ENV=development

EXPOSE ${PORT}
#python3 -m flask run --host=0.0.0.0 --port=4567
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
```

**On the frontend, the code below was used**

``` ruby
FROM node:16.18

ENV PORT=3000

COPY . /frontend-react-js
WORKDIR /frontend-react-js
RUN npm install
EXPOSE ${PORT}
CMD ["npm", "start"]
```
### 7. Ensure we get the apps running via individual container
The apps were running in an individual container as shown below

![docker-compose-yaml-aws-bootcamp-cruddur-2023-Gitpod-Code (1)](https://user-images.githubusercontent.com/17044063/225561180-d4435e67-dd9e-4921-b898-927179ac48fd.png)


### 8. Create a docker-compose file
I was able to create a docker compose file using the code below

<details><summary>Click here to see the code </summary>
  
``` ruby
version: "3.8"
services:
  backend-flask:
    environment:
      FRONTEND_URL: "https://3000-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
      BACKEND_URL: "https://4567-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
    build: ./backend-flask
    ports:
      - "4567:4567"
    volumes:
      - ./backend-flask:/backend-flask
  frontend-react-js:
    environment:
      REACT_APP_BACKEND_URL: "https://4567-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
    build: ./frontend-react-js
    ports:
      - "3000:3000"
    volumes:
      - ./frontend-react-js:/frontend-react-js
  dynamodb-local:
    # https://stackoverflow.com/questions/67533058/persist-local-dynamodb-data-in-volumes-lack-permission-unable-to-open-databa
    # We needed to add user:root to get this working.
    user: root
    command: "-jar DynamoDBLocal.jar -sharedDb -dbPath ./data"
    image: "amazon/dynamodb-local:latest"
    container_name: dynamodb-local
    ports:
      - "8000:8000"
    volumes:
      - "./docker/dynamodb:/home/dynamodblocal/data"
    working_dir: /home/dynamodblocal
  db:
    image: postgres:13-alpine
    restart: always
    environment:
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=password
    ports:
      - '5432:5432'
    volumes: 
      - db:/var/lib/postgresql/data

# the name flag is a hack to change the default prepend folder
# name when outputting the image names
networks: 
  internal-network:
    driver: bridge
    name: cruddur
    
volumes:
  db:
    driver: local
  ```
</details>

### 9. Ensure we can orchestrate multiple containers to run side by side
I was able to orchestrate multiple containers to run side by side as shown in the image below
![image](https://user-images.githubusercontent.com/17044063/225557227-fb60721d-97c5-4acc-bdea-8f5470843f64.png)

### 10. Mount directories so we can make changes while we code
In the docker compose file, volumes were used for the backend, frontend and database in order to mount directories so that we could make changes easily while coding
![image](https://user-images.githubusercontent.com/17044063/225559380-ebe0124e-31d1-4fcb-9f55-122462452dcc.png)


