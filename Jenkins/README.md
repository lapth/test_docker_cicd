1. Pull Jenkins images
docker pull jenkins/jenkins:lts

2. Run Jenkins
docker run -d --rm -u jenkins:root --privileged -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v /usr/local/bin/docker:/usr/local/bin/docker -p 8080:8080 jenkins/jenkins:lts

Issues:
- Docker: not found in Jenkins pipeline
- Build java project with maven in Jenkins => use Jenkinsfile and Jenkins pipeline
