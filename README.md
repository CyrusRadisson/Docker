# Docker

this file tells us about docker commands and installation process.
Instalation
{
  1:sudo apt update
  2:sudo apt-get install ca-certificates curl
  3:sudo install -m 0755 -d /etc/apt/keyrings
  4:sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
  5:sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:-> you can do it by directing to cd /etc/apt/sources.list.d
  6: sudo nano docker.list
  7: deb [arch=amd64] https://download.docker.com/linux/ubuntu jammy stable
  8:sudo apt update
  9:sudo apt install docker-ce
  10:docker --version
}
  11: you can pull something from docker hub: sudo docker pull ubuntu-> by default it will download the latest version
  12: sudo docker image ls-> it shows your images
  13: sudo docker run ubuntu /bin/ls -l /-> it shows all of your container
  14:sudo docker container rm <NO of container>
  15:sudo docker run hello-world -> it runs the container
  16:sudo docker container ls -a | awk '{print $1}' |xargs -n 1 sudo docker container rm -> it will remove all running and stopped container
 # How to pull ubuntu and use it
 {
 1: sudo mkdir dockerdemo/demo
 2: cd dockerdemo/demo
 3:sudo nano dockerfile
   {FROM ubuntu:jammy
    RUN apt-get update && apt-get -y(it means yes to every question) install build-essential && apt-get clean
    RUN useradd -d /home/cyrus -s /bin/bash cyrus
    USER cyrus(Before this line everything excute as root line)
    WORKDIR /home/cyrus
    CMD ["/bin/bash"]
    }
  4:sudo docker build -t(means tag the image name we would like to have) my-ubuntu .
  5: sudo docker run -it(interactive terminal) --rm(when the container start it will remove automaticly data like error) my-ububntu ( NOW YOU CAN USE THE CONTAINER INSIDE. YOU CAN CREATE A TABLE BY CREATE my_table and so on. 
  ps ax -> show you the process id number.
  
  you can exit by running exit)
  6: sudo docker image ls
  
  }
# HOW TO PULL PHP CONTAINER AND USE IT.
{
  1: sudo mkdir demo2
  2: cd demo2
  3: sudo cp ../demo/dockerfile .
  4: sudo nano dockerfile {
    change apt-get essential to apt-get php
    ENV DEBIAN_FRONTEND noninteractive
    CMD ["/usr/bin/php", "-S", "0.0.0.0:8000"] OR
    ENTRYPOINT ["usr/bin/php"]
    CMD ["-S", "0.0.0.0:8000"]
    WORKDIR /app
    EXPOSE 8000}
  5: sudo docker build -t my-php .
  6:mkdir pages
  7: sudo docker run -v $(pwd)/pages:/app --rm -p 8000:8000 my-php
  }
  #

  sudo docker -v $(pwd):/app -it --rm my-ubuntu

# about docker compose , docker network, docker reverse proxy, docker 
  sudo nano docker-compose.yaml
    {
      services:
  php_http:
    image: my-php
    build: .
    volumes:
      - type: bind
        source: ./pages
        target: /app
    ports:
      - 8000:8000
    }
    sudo docker compose up or sudo docker compose -d
    sudo docker container logs CONTAINER  -> it shows you the container in the compose that are running and shows you if there is any errors. 
    
  
    

   




















 
  
  
