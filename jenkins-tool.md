# Jenkins Tool

**1. Manage Jenkins > Plugin Manager**

**2. Add and Enabled plugins: NodeJS Plugin**

*use run npm command in Jenkinsfile*

**3. Add and Enabled plugins: Docker Pipeline**

*use run docker command in Jenkinsfile*

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
