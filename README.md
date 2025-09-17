# AWS CloudFormation

O **AWS CloudFormation** é um serviço que auxilia na **automação da criação e gerenciamento de recursos na AWS**.  
Ele utiliza **templates declarativos** (em **JSON** ou **YAML**) para provisionar recursos de forma **rápida, segura e padronizada**.

---

## 📌 Principais Características

- **Automação:** cria e gerencia recursos automaticamente a partir de templates.  
- **Templates Reutilizáveis:** podem ser utilizados diversas vezes sem custo adicional.  
- **Custo sob demanda:** você paga apenas pelos recursos realmente provisionados.  
- **Versionamento:** templates podem ser versionados para rastrear mudanças na infraestrutura.  

---

## 🚀 Exemplo de Template JSON (EC2)

Abaixo está um exemplo de template **CloudFormation** em **JSON**, que cria uma instância **EC2** simples:

```json
{
  "AWSTemplateFormatVersion": "2010-09-09",
  "Description": "Exemplo de CloudFormation criando uma instância EC2",
  "Resources": {
    "MyEC2Instance": {
      "Type": "AWS::EC2::Instance",
      "Properties": {
        "InstanceType": "t2.micro",
        "ImageId": "ami-0c55b159cbfafe1f0",
        "KeyName": "minha-chave-ec2",
        "SecurityGroups": [
          {
            "Ref": "InstanceSecurityGroup"
          }
        ]
      }
    },
    "InstanceSecurityGroup": {
      "Type": "AWS::EC2::SecurityGroup",
      "Properties": {
        "GroupDescription": "Permitir acesso SSH e HTTP",
        "SecurityGroupIngress": [
          {
            "IpProtocol": "tcp",
            "FromPort": "22",
            "ToPort": "22",
            "CidrIp": "0.0.0.0/0"
          },
          {
            "IpProtocol": "tcp",
            "FromPort": "80",
            "ToPort": "80",
            "CidrIp": "0.0.0.0/0"
          }
        ]
      }
    }
  }
}
