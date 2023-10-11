# 1 
install docker `brew install --cask docker`
for ubuntu `sudo apt install docker-ce -y`

# 2
Dockerfile created

# 3
docker build and tag `docker build -t static_nginx:1.0.0 .`
docker tag `docker tag static_nginx makurin/beta_nginx:v1`
docker push `docker push makurin/beta_nginx:v1`

# 4
Remove local image `docker rmi makurin/beta_nginx:v1`

# 5
Go to the remote server
docker run `docker run -d -p 80:80 --name snginx makurin/beta_nginx:v1`
For check html `curl localhost:8080` or open in browser