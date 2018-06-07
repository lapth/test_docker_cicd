**Setup web server with Wildfly** => sv2

1. Prepare this folder: /home/docker/wildfly_deployments

   To ensure, we will not face with the access permission denied issue, run
```
chmod 777 -R /home/docker/wildfly_deployments
```

2. Start server
 
   docker run -d --rm -v /home/docker/wildfly_deployments:/opt/jboss/wildfly/standalone/deployments -p 8080:8080 -p 8787:8787 -p 9990:9990 jboss/wildfly /opt/jboss/wildfly/bin/standalone.sh -b 0.0.0.0 --debug
  
   Here we mount the wildfly_deployments to /opt/jboss/wildfly/standalone/deployments in container then when we copy the bin file into this folder, wildfly can detect and deploy it as well.
  
3. Deploy war file to /home/docker/wildfly_deployments. This will be done by Pipeline stage in Jenkins
