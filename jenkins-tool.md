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

**5. Add and Enabled plugins: Multibranch Scan Webhook Trigger**

*Trigger jenkins deployed when push code to github branch*

![Webhook Jenkins](/assets/jenkins-webhook-config.PNG "Webhook Jenkins")

![Webhook Github](/assets/github-webhook-config.PNG "Webhook Github")

*Payload URL*

```js
<URL_JENKINS>:8080/multibranch-webhook-trigger/invoke?token=<TRIGGER_TOKEN>
```

```js
Example:

URL_JENKINS = http://13.214.200.95
TRIGGER_TOKEN = codoki
```

**5. Add and Enabled plugins: Pipeline: AWS Steps**

*AWS configure in Jenkins file*

![AWS](/assets/AWS_CREDENTIAL.PNG "AWS")

```js
    withAWS([credentials: 'AWS credentials', region: '<REGION_CODE>']) {
        sh 'aws eks --region <REGION_CODE> update-kubeconfig --name <CLUSTER_NAME>'
        sh 'kubectl apply -f deployment.yml'
    }
```