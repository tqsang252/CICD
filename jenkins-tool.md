# Jenkins Tool

**1. Manage Jenkins > Plugin Manager**

**2. Add and Enabled plugins: NodeJS Plugin**

*use run npm command in Jenkinsfile*

**3. Add and Enabled plugins: Docker Pipeline**

*use run docker command in Jenkinsfile*

*Accept Docker deamon for Jenkins* 

---Stop docker container

---Start docker and mount docker from host to jenkins container (Replace <DOCKER_VOLUME_NAME>)

---Check Docker volume : docker volume ls

```js
docker run -p 8080:8080 -p 50000:50000 -d \
-v  <DOCKER_VOLUME_NAME>:/var/jenkins_home \
-v /var/run/docker.sock:/var/run/docker.sock \
-v $(which docker):/usr/bin/docker jenkins/jenkins

sudo su -

docker exec  -u 0 -it id bash

chmod 777 /var/run/docker.sock
```

**4. Manage Jenkins > Global Tool Configuration**

![Nodejs](/assets/Nodejs-jenkins.PNG "Nodejs")

![Docker](/assets/docker-jenkins.PNG "Docker")

**5. Use**

![Nodejs](/assets/use-in-jenkinsfile.PNG "Nodejs")

```js
    tools {
        "org.jenkinsci.plugins.docker.commons.tools.DockerTool" "docker"
        nodejs "Node14"
    }
```
