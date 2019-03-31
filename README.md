# Simple Ubuntu Docker Compose Application

## Goal

Demonstrate the use of a startup script, docker compose and a systemd unit to create an application that runs as a service on an Ubuntu server, such as EC2 or LightSail.

The application used is a [Spring Boot Hello World](https://github.com/kbaynes/docker-springboot-helloworld) runnable JAR, which has no depedencies.

## Lightsail

Note, it is very important that the setup.sh file not have CR/LF line endings.

To use this setup script on Amazon LightSail:
- Select the Ubuntu OS Only instance
- Enter the following in the Launch Script input field
- Click the Start Instance button

```
curl -o ./setup.sh https://raw.githubusercontent.com/kbaynes/ubuntu-compose-simple/master/setup.sh
chmod +x ./setup.sh
./setup.sh
```

## Attribution

This project is based on [Mark Coleman's video tutorial](https://www.youtube.com/watch?v=z525kfneC6E&list=PL5wNnJ-VwlrE1BiUh4qzqFwz81bQrXuXK).

