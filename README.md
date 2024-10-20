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

- **docker-compose.yml**: 
  - Este arquivo orquestra todos os serviços do projeto. Foi criado para definir cada container (backend, frontend e banco de dados), especificando as redes, volumes e as dependências entre os serviços, permitindo a execução conjunta. 
  - Também inclui configurações de **healthcheck** para monitorar a saúde dos containers. O health check garante que o Docker verifique se os serviços estão operacionais, reiniciando automaticamente qualquer container que não esteja respondendo corretamente.

- **Dockerfile do Backend**: 
  - Este arquivo foi construído para configurar o container do backend, instalando as dependências da aplicação Flask. O código-fonte foi copiado para o container e o ambiente foi configurado para executar o servidor Flask.

- **Dockerfile do Frontend**: 
  - O Dockerfile do frontend foi elaborado para configurar o container que serve a aplicação React. Ele instala as dependências do React, compila a aplicação e configura o NGINX para entregar os arquivos estáticos gerados.

- **Configuração do NGINX**: 
  - O arquivo de configuração do NGINX foi definido para atuar como um proxy reverso, direcionando requisições para as instâncias do backend e servindo a aplicação frontend. Ele melhora a escalabilidade e resiliência do sistema, permitindo o acesso sob um único domínio.


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
