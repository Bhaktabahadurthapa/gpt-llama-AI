### Installing Docker

### Update and Upgrade ubuntu machine
```
sudo apt update
sudo apt upgrade
```
### install a few prerequisite packages which let apt use packages over HTTPS
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

### Add the GPG key for the official Docker repository to your system
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

```
### Add the Docker repository to APT sources
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

```

### Update your existing list of packages again for the addition to be recognized
```
sudo apt update
```
### Make sure you are about to install from the Docker repo instead of the default Ubuntu repo
```
apt-cache policy docker-ce

``` 
### Finally, install Docker
```
sudo apt install docker-ce
```
### Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running
```
sudo systemctl status docker
```             

### If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group:
```
sudo usermod -aG docker ubuntu

```
### If not, run this bundle command (for CPU)
```
docker run -d -p 3000:8080 -v ollama:/root/.ollama -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama

```
