# Tutorial: Como Rodar e Acessar o Oracle DB no Kubernetes

Este projeto, contém uma aplicação de banco de dados Oracle que opera em um ambiente Kubernetes utilizando Minikube. A aplicação permite a criação de tabelas e a realização de consultas SQL, oferecendo uma solução prática para gerenciar dados em um ambiente isolado e escalável. O acesso ao banco de dados é facilitado através do SQL*Plus, e a configuração de serviços permite o acesso externo, tornando-a ideal para desenvolvimento e testes.

## 1. Passos Iniciais
- Certifique-se de que o cluster Kubernetes esteja rodando (por exemplo, usando Minikube).
- Verifique se os arquivos `deployment.yaml` e `service.yaml` já foram aplicados para configurar o Oracle DB no Kubernetes.

## 2. Verificar o Pod do Oracle DB
- Para verificar se o pod do Oracle DB está rodando, execute o comando:
  ```bash
  kubectl get pods

## Acessando o pod do Oracle DB
```bash
 sqlplus sys/aulaalex as sysdba
 kubectl exec -it <nome-do-pod> -- bash
 kubectl exec -it oracle-db-54b9ccfbd9-2nz4t -- bash

## Após acessar o pod, você pode iniciar o SQL*Plus com o seguinte comando:
 ```bash
  sqlplus sys/aulaalex as sysdba


## Para verificar quais tabelas existem no esquema atual, execute:
SELECT table_name FROM user_tables;

## Criar uma Tabela de Exemplo
CREATE TABLE mat_categorias (
    cat_cod     NUMBER(4) NOT NULL,
    cat_cod_pai NUMBER(4),
    cat_nome    VARCHAR2(30) NOT NULL
);

## Sair/ encerrar
EXIT;

## Acesse o Oracle APEX no navegador
http://<minikube-ip>:<porta-exposta>/ords
# para saber o ip do minikube:
minikube ip
