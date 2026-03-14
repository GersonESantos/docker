
# entrar em gerson@Xeon:/home/Repo2026/docker/Maria Lazara/laboratorio-devops/projeto-devops-fase-1$

# Criar o arquivo  Dockerfile

FROM nginx:alpine
COPY website /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

# bildar a imagem

docker build -t meu-site:v1.0 .

# para ver a imagem

docker images

# Empacotar a aplacaçao 

docker run -d -p 8080:80 meu-site:v1.0 --name meu-site??????

# Para acessear 

http://localhost:8080/
 
# para parar 

docker stop 

# para ver os contêiner rodando

docker ps

# para ver todos contêiner

docker ps -a

# para excluir 

docker rm

# ate aqui testou local 

agora parar e excluir 

docker ps -a

para ver que zerou 

CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

agora fazer a infra extrutura vamos provisionar todos recursos na AWS 

criar um ECR elastic conteiner registry que e um repositorio de imagens da AWS e provisionar um servidor na nuvem que se chama EC2