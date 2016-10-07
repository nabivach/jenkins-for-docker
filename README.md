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
Connect to running Jenkins container.
````sh
docker exec -i -t jenkins-master /bin/bash
````
Remove jenkins_home volume on docker host local storage.
````sh
docker volume rm jenkins_home
````

### Android SDK usage
>For correct use the android sdk tools for multithreading builds android projects, you must declare `ANDROID_HOME` in the project workspace directory.

For setup Android SDK to your current workspace
````sh
env.ANDROID_HOME="${pwd()}/android-sdk" (/android-sdk is automatically created in the workspace)
sh "android-sdk-producer android-sdk_r24.4.1-linux.tgz"
````
For updating Android SDK packages inside your workspace
````sh
sh "android-update-sdk --components=platform-tools,tools,build-tools-24.0.2 --accept-licenses=android-sdk-license-.+"
````
Example [Jenkinsfile](examples/android/Jenkinsfile) for Android projects
