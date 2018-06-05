Using Jenkins Ocean Blue:
  => docker run -u root --rm -d -p 8080:8080 -p 50000:50000 -v jenkins-home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock jenkinsci/blueocean


===> Failed solution
Steps with Jenkins

0. Prepare one RedHat EC2
  => See this to install Docker: https://forums.aws.amazon.com/thread.jspa?messageID=574126
  => sudo yum install yum-utils
  => sudo yum-config-manager --enable rhui-REGION-rhel-server-extras
  => sudo yum install docker
  
1. Pull Jenkins images
  => docker pull lapth/jenkins:v1

2. Run Jenkins
  => docker run -d --rm -v jenkins_home:/var/jenkins_home -p 8080:8080 lapth/jenkins:v1

3. Login Jenkins
4. Create new empyt jobs
  => Pull project from Git: https://github.com/lapth/test-docker-app.git
  => Build with Maven as normally

Known Issues:
- Build project with maven
  => tutorial from jenkins team
    => using jenkins pipeline
      => problem: need docker in docker, can not access host docker, ... <= do not use this solution
  => work around to resolve this issue: 
    => make new Dockerfile to pull original Jenkins
    => install distributed maven
      => work as expected
    => built image at: lapth/jenkins:v1
    
- /var/run/docker.sock: connect: permission denied
  => sudo groupadd docker
  => sudo usermod -aG docker $USER
  => sudo reboot

