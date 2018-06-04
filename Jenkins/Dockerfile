FROM jenkins/jenkins:lts

USER root

# Install distributed maven
RUN apt-get update -qq && \
    apt-get install -y maven && \
    chown -R jenkins:jenkins $JENKINS_HOME/

USER jenkins
