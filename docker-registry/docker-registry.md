# Registro Docker

Un Registry es un lugar donde almacenar imágenes de contenedores que luego utilizará(n) el/los engines para crear nuestros amados contenedores. 

Docker Hub es un registro de Docker alojado administrado por Docker. Docker Hub tiene más de 100.000 imágenes de contenedores de proveedores de software, proyectos de código abierto y la comunidad. Docker Hub contiene software y aplicaciones de repositorios oficiales, como NGINX, Logstash, Apache HTTP, Grafana, MySQL, Ubuntu y Oracle Linux.

Al iniciar un contenedor, Docker extraerá de manera automática y predeterminada la imagen correspondiente del Docker Hub público si no está disponible a nivel local. Además, también puede crear sus propias imágenes y enviarlas a Docker Hub en un repositorio público o privado.

https://hub.docker.com/_/registry/

https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-docker-registry-on-ubuntu-18-04-es

roxsross12/app-demo

docker build -t app-demo .

tag -
docker tag app-demo:latest roxsross12/app-demo:latest  

docker login

docker push roxsross12/app-demo:latest

docker build -t app-demo:v1.0.0 .
