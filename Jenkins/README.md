1. Pull Jenkins images
docker pull jenkins/jenkins:lts
2. Run Jenkins
docker run -d -v jenkins_home:/var/jenkins_home -p 8080:8080 jenkins/jenkins:lts
