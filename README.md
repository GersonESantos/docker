#  Introdução ao Docker para iniciantes  Docker Tutorial
---
title: "Introdução ao Docker para iniciantes | Docker Tutorial #docker"
curso: Virtualização e Containers com Docker
video_url: https://www.youtube.com/watch?v=01MR38eDXz8
author: Manual do Dev
data_estudo: 2026-01-28
linguagem:
  - SQL
  - JavaScript
tecnologias:
  - Docker
  - Docker Hub
  - MySQL
  - Node.js
  - React
assuntos:
  - Virtualização
  - Containers vs Imagens
  - Mapeamento de Portas (Port Binding)
  - Criação de Dockerfiles
  - Variáveis de Ambiente
status: 🔴 Inicio
tags:
  - docker
  - devops
  - backend
  - desenvolvimento
---

#  Introdução ao Docker para iniciantes

![Capa do Vídeo](https://img.youtube.com/vi/01MR38eDXz8/maxresdefault.jpg)

**Video:** [Link original do vídeo](https://www.youtube.com/watch?v=01MR38eDXz8)

## Conteúdo da Aula

O vídeo do canal **Manual do Dev** apresenta uma introdução prática ao **Docker**, destacando como ele resolve o problema de incompatibilidade entre ambientes de desenvolvimento. O autor explica que a plataforma permite **empacotar aplicações em contêineres**, garantindo que o software funcione em qualquer máquina apenas com o Docker instalado. São detalhados conceitos fundamentais como a diferença entre **imagens e contêineres**, além da importância do **direcionamento de portas** para a comunicação externa. Na parte prática, o tutorial demonstra desde a execução de um banco de dados **MySQL** até a criação de um **Dockerfile** personalizado para uma aplicação React. O objetivo final é preparar o espectador para projetos **full stack**, utilizando imagens prontas ou configurando ambientes do zero.

![[Pasted image 20260314072310.png]]

### 1. Conceitos Fundamentais e o Problema da "Minha Máquina"
- **O Problema [00:01:06]:** Explicação sobre como divergências de versões de software (Node.js, MySQL) entre máquinas de desenvolvedores causam erros de execução.
- **O que é Docker [00:00:42]:** Plataforma open-source que facilita a criação e administração de ambientes isolados.
- **Containers e Imagens [00:03:42]:** Analogia entre uma imagem ISO de um sistema operacional e uma imagem Docker, onde o container é a instância em execução.

### 2. Mapeamento de Portas e Conectividade
- **Ambiente Isolado [00:05:13]:** O container roda em isolamento total, por isso é necessário o "Port Binding".
- **Bind de Portas [00:06:06]:** Como vincular uma porta da máquina local (host) a uma porta interna do container para permitir o acesso externo.

### 3. Prática com MySQL no Docker
- **Docker Hub [00:09:56]:** Apresentação do repositório oficial de imagens.
- **Comando `docker run` [00:11:37]:** Executando um container MySQL definindo nome, variáveis de ambiente (senha do root) e a versão específica da imagem.
- **Comando `docker ps` [00:13:52]:** Como listar containers ativos e verificar status.
- **Persistência e Erros [00:16:42]:** Demonstração de erro de conexão quando o mapeamento de portas não é realizado corretamente.

### 4. Criando Imagens Personalizadas (Dockerfile)
- **Criação do Dockerfile [00:22:04]:** Passo a passo para criar uma imagem para uma aplicação React:
    - `FROM`: Definindo a imagem base (Node Alpine) [00:22:14].
    - `WORKDIR`: Definindo o diretório de trabalho interno [00:22:39].
    - `COPY`: Copiando arquivos de dependências e código fonte [00:24:52].
    - `RUN`: Executando o `npm install` durante o build [00:25:30].
    - `EXPOSE`: Declarando a porta que o container deve liberar [00:26:24].
    - `CMD`: Definindo o comando de inicialização da aplicação [00:26:35].
- **Build da Imagem [00:27:24]:** Uso do comando `docker build -t meu-app .` para gerar a imagem personalizada.

## Performance/Conclusão
O vídeo demonstra com sucesso como o Docker resolve o problema de inconsistência de ambientes. Ao final, é apresentada uma aplicação React rodando inteiramente dentro de um container, provando que não é necessário ter o Node.js ou o MySQL instalados diretamente na máquina física para desenvolver, bastando apenas o motor do Docker ativo.