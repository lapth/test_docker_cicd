1. Pull Jenkins images
docker pull jenkins/jenkins:lts

2. Run Jenkins
docker run -d --rm -u jenkins:docker --privileged -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v /usr/local/bin/docker:/usr/local/bin/docker -p 8080:8080 jenkins/jenkins:lts

Issues:
- /var/run/docker.sock: connect: permission denied
  => sudo groupadd docker
  => sudo usermod -aG docker $USER
  => sudo reboot

- Docker: not found in Jenkins pipeline, permission denied, ..
  => sudo chmod +rx /usr/bin/* -R
  => sudo chmod +rx /run/* -R
  
- Build java project with maven in Jenkins => use Jenkinsfile and Jenkins pipeline
