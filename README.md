# Tutorial: Como Rodar e Acessar o Oracle DB no Kubernetes

Este tutorial detalha como rodar o Oracle Database em um ambiente Kubernetes, desde a configuração inicial até a criação de tabelas e consultas SQL.

## 1. Requisitos de Instalação

- Para rodar esta aplicação, certifique-se de que os seguintes softwares estejam instalados no seu sistema:

- **Docker**: Para rodar containers localmente.
  - Instalação: https://docs.docker.com/get-docker/
- **Minikube**: Para rodar um cluster Kubernetes localmente.
  - Instalação: https://minikube.sigs.k8s.io/docs/start/
- **Kubectl**: Ferramenta de linha de comando para interagir com o Kubernetes.
  - Instalação: https://kubernetes.io/docs/tasks/tools/install-kubectl/
- **SQL*Plus** (opcional): Cliente SQL para interagir com o Oracle Database via terminal.
  - Instalação: https://www.oracle.com/br/database/technologies/sqlplus-cloud.html

- Certifique-se de que o Docker esteja rodando e o Minikube esteja inicializado.

### 1.1 Inicializando o Minikube

- Se o Minikube não estiver rodando, inicialize-o com o comando:
  ```bash
  minikube start

### 2. Aplicar os Arquivos e Configurações do Kubernetes
### 2.1 Aplicando o Deployment e o Service
- Use isso para aplicar os arquivos yaml:
  ```bash
  kubectl apply -f deployment.yaml
  kubectl apply -f service.yaml
  #verifique se foi criado de forma certa:
  kubectl get deployments
  kubectl get services

### 3. Verificar o Pod do Oracle DB
- Execute
  ```bash
  kubectl get pods
  #Isso vai exibir o nome
  #do pod, sera algo parecido
  #com oracle-db-<idAleatorio>. Voce vai usa-lo para acessar
  #o pod

### 4. Acessando o Pod e o SQL*Plus
- substitua o <name-pod> pelo resultado do "kubectl get pods"
  ```bash
  kubectl exec -it <nome-do-pod> -- bash
- agora, voce entrou dentro do pod, e pode acessar o SQL*Plus:
  ```bash
  sqlplus sys/aulaalex as sysdba

### 5. Criando Tabelas e Fazendo Consultas
- agora voce esta conectado, entao pode criar tabelas, fazer consultas e muito mais
### 5.1 Criando Tabela
- Exemplo:
    CREATE TABLE MAT_CATEGORIAS (
        cat_cod     NUMBER(4) NOT NULL,
        cat_cod_pai NUMBER(4),
        cat_nome    VARCHAR2(30) NOT NULL
    );
### 5.2 Inserindo Dados
- Exemplo:
    INSERT INTO MAT_CATEGORIAS (CAT_COD,CAT_COD_PAI,CAT_NOME) VALUES (1,NULL,'Alimentos');
### 5.3 Consultando Dados
- Exemplo:
  SELECT * FROM MAT_CATEGORIAS;

### 6. Acessando o Oracle DB Externamente
- Para acessar o bd de fora do pod, voce pode expor a porta do servico. Primeiro, obtenha o IP do Minikube:
  ```bash
  minikube ip
- Agora, verifique as portas expostas pelo servico Oracle DB com o comando:
  ```bash
  kubectl get services
- Com o ip e a porta, voce pode acessar o banco de dados a partir de um cliente externo. Por ex, usando o seguinte endereço para conectar-se ao Oracle DB:
  ```bash
  <minikube-ip>:30000

### 7. Encerrando o cluster
- Quando terminar de usar o Oracle DB, voce pode parar o Minikube com o comando:
  ```bash
  minikube stop
