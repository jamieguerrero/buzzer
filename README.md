<p align="center">
  <img width="400px" src="https://github.com/bufferapp/buzzer/blob/master/public/buzzer-logo.svg?raw=true&sanitize=true" alt="Buzzer"/>
</p>

A little buzzer app for running your own quizzes or game shows! Uses websockets to sent messages.

## Running the app

You'll need [Node.js](https://nodejs.org) or [Docker](https://www.docker.com/) to run this
application. For Node:

```
npm install
node index.js
```

For Docker:

```
docker build -t buzzer .
docker run -p 8090:8090 buzzer
```

Open http://localhost:8090 in your browser to start!

## How to use

The players goto the homepage (`http://localhost:8090/`) and they can enter their name and team
number. Joining will give them a giant buzzer button!

The host heads over to `/host` and will be able to see everyone that buzzes in and clear the list
in between questions.

Join a team                | Buzz in                   | Host view                  |
:-------------------------:|:-------------------------:|:-------------------------:|
<img width="250px" src="https://github.com/bufferapp/buzzer/blob/master/screenshots/player-join-v3.png?raw=true" alt="Join a team"/> | <img width="250px" src="https://github.com/bufferapp/buzzer/blob/master/screenshots/player-buzzer-v3.png?raw=true" alt="Buzz in"/> | <img width="250px" src="https://github.com/bufferapp/buzzer/blob/master/screenshots/host-v3.png?raw=true" alt="Host view"/>

## License

## Deploying to GCloud

Starting this article from Building the Docker Image helped: https://towardsdatascience.com/how-to-deploy-docker-containers-to-the-cloud-b4d89b2c6c31

```docker build -t [image name] .```

- Here, the Docker image build command is docker build
- Next, we use the -t flag to specify our image name
- Finally, we tell Docker to include everything from the current directory with .

install gcloud sdk: https://cloud.google.com/sdk/docs/downloads-interactive

log into gcloud
```gcloud auth login```

gcloud might ask you to use your previous credentials... just say yeah, you can create a new project

configure docker to use our gcloud auth
```gcloud auth configure-docker```

set project you're using
```gcloud config set project [project-name]```

make sure cloud container registry is available in google cloud, then submit image to cloud build 
```gcloud builds submit --tag gcr.io/[PROJECT-ID]/gcp-api```

manually create a Cloud Run on google cloud console. take note that the port number is 8090, not 8080.

MIT
