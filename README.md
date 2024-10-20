# Jogo de Adivinhação com Flask e React

Este projeto consiste em um jogo de adivinhação utilizando Flask para o backend e React para o frontend, orquestrados com Docker e NGINX como proxy reverso.

## Requisitos

### Containers Backend e Frontend
- **Backend**: O container executa a aplicação Flask do jogo de adivinhação.
- **NGINX**: Serve como proxy reverso, balanceando a carga entre instâncias do backend e servindo o frontend.

### Banco de Dados Postgres
- O container do Postgres armazena os dados do jogo em um volume persistente.

### Resiliência e Manutenção
- **Reinício de Containers**: Containers falhos são reiniciados automaticamente.
- **Balanceamento de Carga**: NGINX é configurado para balancear carga entre múltiplas instâncias do backend.
- **Volumes Separados**: O banco de dados é armazenado em um volume persistente.
- **Facilidade de Atualização**: Atualizações são feitas trocando a versão do container.

## Estrutura do Repositório
- **docker-compose.yml**: Orquestra os serviços.
- **Dockerfile do Backend**: Configura o container Flask.
- **Dockerfile do Frontend**: Configura o container React via NGINX.
- **Configuração do NGINX**: Define o proxy reverso e o balanceamento de carga.

## Instruções de Uso

### Instalação
1. Clone o repositório.
2. Navegue até o diretório do projeto.
3. Execute `docker-compose up --build`.

### Acessando a Aplicação
- O frontend estará disponível em `http://localhost:8080`.

### Atualizações
Para atualizar qualquer componente:
1. Altere a versão do container no `docker-compose.yml`.
2. Execute `docker-compose up --build` novamente.
