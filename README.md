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
  
 
