# <a href="https://www.docker.com/">Docker</a>  
## Install Docke and Docker compose
  
<p align="left">
  <a href="https://github.com/vdarkobar/Home_Lab">Home</a>
</p>  
  
*swich shell (bash) if command not working*  
  
```
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```
```
sudo add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/debian \
  $(lsb_release -cs) \
  stable"
```
```
sudo apt update && sudo apt install -y docker-ce docker-ce-cli containerd.io
sudo docker -v
sudo docker ps -a
```
  
#### Create necessary Docker networks:  
```
sudo docker network create traefik
```
<!--- Commented out
*option: custom Docker networks (specify the gateway and subnet to use).*
```
sudo docker network create --gateway 192.168.90.1 --subnet 192.168.90.0/24 traefik  
```
*option: set static ip to your service(s).*
```
# ...
    networks:
      traefik:
        ipv4_address: 192.168.90.254
```
--->
#### Securing Docker:  

<p align="center">
  <b>Do no add user to docker group (sudo usermod -aG docker $USER && logout).</b><br>
  <b>Do not mess with the ownership of Docker Socket (/var/run/docker.sock in Linux)</b><br>
  <b>Change DOCKER_OPTS to Respect IP Table Firewall. Edit /etc/default/docker and add the following line:</b><br>
</p>

```
DOCKER_OPTS="--iptables=false"  
```
  
### Docker Compose:  
  
[Check the current Docker Compose release here](https://github.com/docker/compose/releases), update '/1.27.4/' in the command:
```
sudo curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose  
sudo chmod +x /usr/local/bin/docker-compose
sudo docker-compose --version
```