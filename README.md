# Configuração Terraform AWS RDS MySQL

## Visão Geral

Este script Terraform, `main.tf`, tem como objetivo implantar uma instância do Amazon RDS (Relational Database Service) na AWS. O script utiliza o Terraform para definir a infraestrutura como código, facilitando o provisionamento e gerenciamento dos recursos AWS necessários.

## Descrição

O propósito principal deste script é criar uma instância AWS RDS executando MySQL. Ele também configura um grupo de segurança para controlar o tráfego de entrada e saída para a instância RDS.

### Recursos AWS Criados:

- **Provider:** Configura o provedor AWS com a região especificada (sa-east-1).

- **Grupo de Segurança (`aws_security_group`):** Define um grupo de segurança chamado "rds_sg" permitindo tráfego de entrada na porta 3306 (MySQL) de qualquer endereço IP (`0.0.0.0/0`). O tráfego de saída é permitido para qualquer destino.

- **Instância do Banco de Dados RDS (`aws_db_instance`):** Cria uma instância RDS com as seguintes especificações:
  - Engine: MySQL
  - Identificador: todo-list-rdsinstance
  - Armazenamento Alocado: 20 GB
  - Versão do Engine: 8.0.34
  - Classe da Instância: db.t2.micro
  - Nome de Usuário: root
  - Senha: password
  - Grupo de Parâmetros: default.mysql8.0
  - Grupo de Segurança Associado: rds_sg
  - Pular Snapshot Final: true
  - Publicamente Acessível: true

## Requisitos

Antes de executar este script, certifique-se de ter os seguintes pré-requisitos:

- **Credenciais AWS:** Configure as credenciais da AWS com as permissões necessárias. Isso pode ser feito definindo variáveis de ambiente ou usando perfis AWS CLI.

- **Terraform Instalado:** Instale o Terraform em sua máquina. Você pode baixá-lo em [terraform.io](https://www.terraform.io/downloads.html).

## Execução

Siga estas etapas para implantar a instância RDS usando o Terraform:

1. **Inicializar o Terraform:**
    ```bash
    terraform init
    ```

2. **Revisar o Plano:**
    ```bash
    terraform plan
    ```

3. **Aplicar Alterações:**
    ```bash
    terraform apply
    ```

4. **Destruir Recursos (Opcional):**
    ```bash
    terraform destroy
    ```