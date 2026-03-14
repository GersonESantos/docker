Execute estes comandos para preparar o terreno e instalar o motor que rodará os bancos.

Bash

```
# 1. Atualizar e instalar dependências básicas
sudo apt update && sudo apt install -y ca-certificates curl gnupg

# 2. Configurar Chave GPG do Docker
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# 3. Adicionar Repositório Docker (Base Noble/24.04)
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu noble stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 4. Instalar o Docker
sudo apt update && sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 5. Permissão de Usuário (Evita usar sudo no docker)
sudo usermod -aG docker $USER

# ⚠️ PARE AQUI: Reinicie o computador agora para validar a permissão.
```
docker build -t meu-app .

NO VS CODE, VOCÊ EXECUTA ASSIM:

1.ABRA O TERMINAL: CTRL + ' (CRASE)
2.ENTRE NA PASTA DO PROJETO:

cd /home/Repo2026/docker/Manual do Dev/app
  
3.COLE UM COMANDO POR VEZ E PRESSIONE ENTER.
  ORDEM RECOMENDADA:


docker images | grep meu-app
docker rm -f react-app
docker run --name react-app -p 3000:3000 meu-app
docker ps | grep react-app
docker port react-app
docker logs -f react-app
curl -I http://localhost:3000
