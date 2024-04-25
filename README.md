# Docker

this file tells us about docker commands and installation process.
Instalation
{
  1:sudo apt update
  2:sudo apt install apt-transport-https ca-certificates curl software-properties-common
  3:curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  4: sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu jammy stable"-> here jammy is my ubuntu version it might be different from yours. you can find out yours by  . /etc/os-release && echo "$VERSION_CODENAME"
  5:sudo apt update
  6:sudo apt install docker-ce
  7:docker --version
}
  8: you can pull something from docker hub: sudo docker pull ubuntu-> by default it will download the latest version
  9: sudo docker image ls-> it shows your images
  10: sudo docker run ubuntu /bin/ls -l /-> it shows all of your container
  11:sudo docker container rm <NO of container>
  12:sudo docker run hello-world -> it runs the container
  13:sudo docker container ls -a | awk '{print $1}' |xargs -n 1 sudo docker container rm -> it will remove all running and stopped container
  
 
