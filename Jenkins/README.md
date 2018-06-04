1. Pull Jenkins images
  => docker pull lapth/jenkins:v1

2. Run Jenkins
  => docker run -d --rm -v jenkins_home:/var/jenkins_home -p 8080:8080 lapth/jenkins:v1

Issues:
- Build project with maven
  => tutorial from jenkins team
    => using jenkins pipeline
      => problem: need docker in docker, can not access host docker, ... <= do not use this solution
  => work around to resolve this issue: 
    => make new Dockerfile to pull original Jenkins
    => install distributed maven
      => work as expected
  
- /var/run/docker.sock: connect: permission denied
  => sudo groupadd docker
  => sudo usermod -aG docker $USER
  => sudo reboot
