# Common settup

**Settup SSH-key authentication to copy file from Jenkins server to Staging/Pro server**
```
Work flow: code => github => Jenkins/Jenkins server => build => test => deploy => staging/pro
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

**Test: from sv1** should do manually to add truted sv2
```
ssh docker@sv2 ls
```

   
