# Estudo-AWS-CloudFormation
# Estudo sobre uma Stack AWS CloudFormation

Este repositório foi criado como parte do **desafio de laboratório** de CloudFormation.  
O objetivo é implementar uma stack mínima em AWS, documentar o processo e compartilhar insights de aprendizado.

# O que é o AWS CloudFormation?

O **AWS CloudFormation** é um serviço que permite **descrever e provisionar recursos da AWS usando código** (YAML ou JSON).  
Com ele, conseguimos automatizar a criação de ambientes completos em nuvem, sem precisar clicar manualmente no console.

---

## Objetivos do Desafio

- Aplicar conceitos de **Infraestrutura como Código (IaC)** com AWS CloudFormation.  
- Documentar o processo técnico de forma clara e estruturada.  
- Utilizar o **GitHub** como ferramenta de estudo e compartilhamento.  
- Criar um material de apoio que sirva como referência para futuros projetos.  

---

## Arquitetura da Stack

Essa stack é um **modelo clássico de aplicação web/API em nuvem**, que inclui:

- **Escalabilidade** → Auto Scaling Group + Load Balancer  
- **Segurança** → VPC isolada, Subnet e Security Groups  
- **Banco de Dados** → Amazon RDS (MySQL)  
- **Armazenamento** → Amazon S3  
- **Serverless** → AWS Lambda  
- **Mensageria** → Amazon SNS  
- **Monitoramento** → Amazon CloudWatch  

---

## Diagrama da Stack

```mermaid
flowchart TB
    subgraph VPC[VPC]
        IGW[Internet Gateway]
        NAT[NAT Gateway]
        ALB[Application Load Balancer]
        ASG[Auto Scaling Group]
        EC2[EC2 Instances]
        RDS[(RDS Database)]
        S3[(S3 Bucket)]
        Lambda[Lambda Functions]
        SNS[SNS Topic]
        SG[Security Groups]
    end

    ALB --> ASG
    ASG --> EC2
    EC2 --> RDS
    EC2 --> S3
    Lambda --> S3
    Lambda --> SNS
    SNS --> Lambda
    EC2 -->|Logs| CW[CloudWatch]
    Lambda -->|Logs| CW
    ALB -->|Logs| CW
```
## Template CloudFormation

O arquivo `template.yaml` contém a definição da infraestrutura descrita neste repositório.  
Ele provisiona recursos como VPC, Subnet, Internet Gateway, NAT Gateway e configurações básicas para uma arquitetura escalável.

> Este template é usado como base para estudo e não está pronto para produção.

