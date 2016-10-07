# Jenkins
Self-contained Jenkins for Docker

### Start Jenkins container
1. Go to the project directory.
2. Build docker image with Jenkins.
````sh
docker build -t myjenkins .
````
3. Run docker container with mounting jenkins_home volume on docker host local storage.
````sh
docker run -d --name jenkins-master -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home myjenkins
````
#### Useful Jenkins container commands
Remove jenkins_home volume on docker host local storage.
````sh
docker volume rm jenkins_home
````
Connect to running Jenkins container.
````sh
docker exec -i -t jenkins-master /bin/bash
````
