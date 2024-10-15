# Tutorial: Como Rodar e Acessar o Oracle DB no Kubernetes

Este tutorial detalha como rodar o Oracle Database em um ambiente Kubernetes, incluindo como se conectar ao banco de dados, criar tabelas e realizar consultas.

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
