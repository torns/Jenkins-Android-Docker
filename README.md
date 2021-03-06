# Jenkins-Android-Docker
[![](https://images.microbadger.com/badges/image/windsekirun/jenkins-android-docker.svg)](https://microbadger.com/images/windsekirun/jenkins-android-docker "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/windsekirun/jenkins-android-docker.svg)](https://microbadger.com/images/windsekirun/jenkins-android-docker "Get your own version badge on microbadger.com") 

🐳 Docker image for Jenkins with Android, [View on DockerHub](https://hub.docker.com/r/windsekirun/jenkins-android-docker)

Fork base code at [futurice/android-jenjins-docker](https://github.com/futurice/android-jenkins-docker), Revised to the latest development environment.

## Pre-installed SDK Version
 * Android API 28 - build tools 28.0.3
 * Android API 27 - build tools 27.0.3
 * Android API 26 - build tools 26.0.3
 * Android API 25 - build tools 25.0.3 (1.0.2)
 * Android API 23 - build tools 23.0.3 (1.0.2)
 * Android API 22 - build tools 22.0.1 (1.0.2)
 * extra-android-m2repository
 
## Pre-installed Jenkins Plugin
  * git
  * gradle
  * android-emulator
  * ws-cleanup
  * slack
  * embeddable-build-status
  * blueocean (since 1.0.4)
  * github-coverage-reporter (since 1.0.4)
  * jacoco (since 1.0.4)
  * github-pr-coverage-status (since 1.0.4)
  
## Build image
```docker build -t jenkins-android-docker .```

Instead, you can use `buildImage.sh`

## Use image
```docker run -d -p 8080:8080 -p 50000:50000 -v /data/jenkins-android-docker:/var/jenkins_home windsekirun/jenkins-android-docker:<latest-version>```

 - Latest version need to replace real version. You can find tag in [Release Page](https://github.com/WindSekirun/Jenkins-Android-Docker/releases)

 - Before run image, you should provide permission to access /data/jenkins-android-docker with ```sudo chown -R 1000:1000 /data/jenkins-android-docker``` statement.

### docker-compose (v 2.4)
```
  jenkins:
    image: windsekirun/jenkins-android-docker:<latest-version>
    container_name: jenkins
    volumes:
      - "/data/jenkins-android-docker:/var/jenkins_home"
    restart: always
```

### With nginx
If you want use nginx for reverse-proxy, you can add this statement in conf file.
```proxy_pass http://jenkins:8080;```

## Modification
 From Line 33 ~ 41, you can modify version info using `sdkmanager`. Feel free to change these value.
 
## ~License~
 ~Do we really need license?~
