0. SSH with key
  => ssh -i /ec2.pem ec2-user@ec2-198-51-100-1.compute-1.amazonaws.com

1. Pull Jenkins images
  => docker pull jenkins/jenkins:lts

2. Build customize jenkins to install needed thing
  => mkdir cus_jenkins
  => cd cus_jenkis
  => vi Dockerfile   <= refer Dockerfile
  => docker build -t cus_jenkis .
  
2. Run Jenkins
  => docker run -d --rm -v jenkins_home:/var/jenkins_home -p 8080:8080 jenkins/jenkins:lts

Issues:
- Build project with maven
  => tutorial from jenkins team
    => using jenkins pipeline
      => problem: need docker in docker, can not access host docker, ... <= do not use this solution
  => work around to resolve this issue: install distributed maven inside this container
  
- /var/run/docker.sock: connect: permission denied
  => sudo groupadd docker
  => sudo usermod -aG docker $USER
  => sudo reboot
