1. Pull Jenkins images
docker pull jenkins/jenkins:lts
2. Run Jenkins
docker run -d --rm -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -p 8080:8080 jenkins/jenkins:lts
