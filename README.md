# micro-services


## Docker file basic content to get started using Dockerfile

- Create a file in the project without any extension with name Dockerfile

- Paste below content ...

```sh

> #Start with a base image containing Java runtime

> FROM openjdk:8-jdk-slim as build

> #Information around who maintains the image

> MAINTAINER bharatkadam.com

> #Add the application's jar to the container

> COPY target/accounts-0.0.1-SNAPSHOT.jar accounts-0.0.1-SNAPSHOT.jar

> #execute the application

> ENTRYPOINT ["java","-jar","/accounts-0.0.1-SNAPSHOT.jar"]

```


## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```






