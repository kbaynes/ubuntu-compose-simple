# Simple Ubuntu Docker Compose Application

## Goal

Demonstrate the use of a startup script, docker compose and a systemd unit to create an application that runs as a service on an Ubuntu server, such as AWS LightSail.

The application used is a [Spring Boot Hello World](https://github.com/kbaynes/docker-springboot-helloworld) runnable JAR, which has no depedencies, and which is linked in via the [kbaynes/springboot-helloworld:latest](https://hub.docker.com/r/kbaynes/springboot-helloworld) Docker image.

## Lightsail

Note to Windows users: CR/LF line endings as this will cause setup.sh to fail in Ubuntu. Convert to LF if you edit setup.sh.

To use this setup script on Amazon LightSail:
- Select an Ubuntu OS Only instance
- Enter the following in the Launch Script input field
- Click the Start Instance button

```
curl -o ./setup.sh https://raw.githubusercontent.com/kbaynes/ubuntu-compose-simple/master/setup.sh
chmod +x ./setup.sh
./setup.sh
```

Confirm that the instance is running by connecting to the IP of the instance in a browser. You should see the 'Hello World!' screen. It seems to require a couple of minutes to completely load, even after the instance says it's ready in the LightSail interface.

Next, stop the instance via the LightSail interface, and reload in the browser to confirm that it cannot connect. Then start the instance via the LightSail web interface and reload in the browser to confirm that the instance has restarted and the application automatically reloaded.

### Tests
April 2019 : confirmed working with LightSail Ubuntu 16 (1 GB RAM, 1 vCPU, 40 GB SSD)
April 2019 : confirmed working with LightSail Ubuntu 18 (1 GB RAM, 1 vCPU, 40 GB SSD)
<!-- 
## EC2

NOTE: on first try, this is not working, need to debug. For now, commenting out this section.

To use this setup script on Amazon EC2:
- Click Launch Instance and select an Ubuntu instance (tested with 64-bit x86)
- Select a type (tested with t2.micro: Variable ECUs, 1 vCPUs, 2.5 GHz, Intel Xeon Family, 1 GiB memory, EBS only)
- Click Next: Configure Instance Details, expand the Advanced section at the bottom
- Enter the following Launch Script into the User Data input field
- Click Review and Launch, then Launch



```
curl -o ./setup.sh https://raw.githubusercontent.com/kbaynes/ubuntu-compose-simple/master/setup.sh
chmod +x ./setup.sh
./setup.sh
``` -->

## Attribution

This project is based on [Mark Coleman's video tutorial](https://www.youtube.com/watch?v=z525kfneC6E&list=PL5wNnJ-VwlrE1BiUh4qzqFwz81bQrXuXK).

