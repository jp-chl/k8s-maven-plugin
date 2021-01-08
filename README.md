# Deploying Spring Boot Application on Kubernetes using Kubernetes Maven Plugin

> _Based on [https://medium.com/faun/deploying-spring-boot-application-on-kubernetes-using-kubernetes-maven-plugin-46caf22b03a5](https://medium.com/faun/deploying-spring-boot-application-on-kubernetes-using-kubernetes-maven-plugin-46caf22b03a5)_

---
## Generate project

Generate a project either on [Spring Initializr](https://start.spring.io/), or with the following command:

```bash
curl https://start.spring.io/starter.tgz ^
  -d dependencies=web,actuator ^
  -d packageName=com.acme.spring.jkubeapp ^
  -d groupId=com.acme.spring ^
  -d artifactId=jkube-app ^
  -d bootVersion=2.3.7.RELEASE ^
  -d baseDir=jkube-app ^
  | tar -xzvf -
```

---

## Start project

```bash
./mvnw spring-boot:run
```

Open actuator:
```bash
open http://localhost:8080/actuator
```

---

## Build artifacts

### Docker

Instead of building your own Dockerfile, use Spring Boot Maven Plugin.
Add in pom.xml ```spring-boot.build-image.imageName``` within ```<properties>``` tag where its value begins with your docker hub id, like:
```xml
<spring-boot.build-image.imageName>{PLACE_YOUR_DOCKER_HUB_ID_HER}/${project.artifactId
```

Build a docker image:
```bash
./mvnw spring-boot:build-image
```

Check image built:
```bash
docker images|grep jkube
```






