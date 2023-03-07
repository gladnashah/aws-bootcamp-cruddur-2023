# Week 1 — App Containerization

This week I learned the advantages of containerazing applications. Not only is containerazing applications more portable, but it generally makes work easier for everyone, improving the efficiency of the whole application delivery process.

The fact that many images are stored on the [Docker Hub](https://hub.docker.com/) means that someone does not need to spend a lot of time building an already existing image, they can just download it, thereby saving a lot of time.

## Required Homework

### 1. Create a new GitHub repo
![gladnashah-aws-bootcamp-cruddur-2023](https://user-images.githubusercontent.com/17044063/222890124-2f8fe798-0acf-443c-8b37-3d5cdfd99f7c.png)

### 2. Launch the repo within a Gitpod workspace
![Welcome-aws-bootcamp-cruddur-2023-Gitpod-Code](https://user-images.githubusercontent.com/17044063/222890172-6e222a3f-7d5c-4196-afbd-8d15a8576b91.png)

### 3. Configure Gitpod.yml configuration, eg. VSCode Extensions
### 4. Clone the frontend and backend repo
### 5. Explore the codebases
### 6. Ensure we can get the apps running locally
This is the app's frontend

![Cruddur](https://user-images.githubusercontent.com/17044063/223426709-6ff37ff8-a793-441c-8305-433fb9249eea.png)

This is the app's backend

![https-4567-gladnashah-awsbootcampc-z9i49zzlfsd-ws-eu89-gitpod-io-api-activities-home](https://user-images.githubusercontent.com/17044063/223427062-d1856386-f54d-4c91-bfec-6b81610b31f3.png)



### 7. Write a Dockerfile for each app

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
### 8. Ensure we get the apps running via individual container
### 9. Create a docker-compose file
### 10. Ensure we can orchestrate multiple containers to run side by side
### 11. Mount directories so we can make changes while we code
