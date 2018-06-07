**Settup SSH-key authentication to copy file from Jenkins server to Staging/Pro server**
```
Work flow: code => github => Jenkins/Jenkins server => build => test => deploy => deploy => staging/pro
```
- Jenkins server: sv1
- Wildfly server: sv2

**Step 1: In sv1**
```
ssh-keygen -t rsa
```
=> leave all setting as default/empty. The output should be in /root/.ssh/ including **id_rsa** and **id_rsa.pub** files

**Step 2: sv1 copy to sv2**

Copy and append the id_rsa.pub content from sv1 into the /home/docker/.ssh/authorized_keys in sv2. If the authorized_keys is not yet existed, let create it.

*In this case we will ssh to docker user*

**Test: from sv1**
```
ssh docker@sv2 ls
```

**Setup web server with Wildfly**

1. Prepare this folder: /home/docker/wildfly_deployments
To ensure, we will not face with the access permission denied issue, run
```
chmod 777 -R /home/docker/wildfly_deployments
```
2. Start server
 
   docker run -d --rm -v /home/docker/wildfly_deployments:/opt/jboss/wildfly/standalone/deployments -p 8080:8080 -p 8787:8787 -p 9990:9990 jboss/wildfly /opt/jboss/wildfly/bin/standalone.sh -bmanagement 0.0.0.0 --debug
  
   Here we mount the wildfly_deployments to /opt/jboss/wildfly/standalone/deployments in container then when we copy the bin file into this folder, wildfly can detect and deploy it as well.
  
3. Deploy war file to /home/docker/wildfly_deployments. This will be done by Pipeline stage in Jenkins
