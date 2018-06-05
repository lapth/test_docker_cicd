Setup web server with Wildfly

1. Start server
  => docker run -d --rm -v /home/docker/wildfly_deployments:/opt/jboss/wildfly/standalone/deployments -p 8080:8080 -p 9990:9990 jboss/wildfly /opt/jboss/wildfly/bin/standalone.sh -bmanagement 0.0.0.0
2. Deploy war file to /home/docker/wildfly_deployments
