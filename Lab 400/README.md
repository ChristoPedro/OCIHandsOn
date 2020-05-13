# Database

No OCI temos 3 tipos de deployment de banco de dados.

- [Autonomous](https://docs.cloud.oracle.com/en-us/iaas/Content/Database/Concepts/adboverview.htm)
- [VM/Bare Metal](https://docs.cloud.oracle.com/en-us/iaas/Content/Database/Concepts/overview.htm)
- [Exadata Cloud Service](https://docs.cloud.oracle.com/en-us/iaas/Content/Database/Concepts/exaoverview.htm)

Nesse laboratório vamos criar um Banco de Dados as a Service e nos conectar a ele

## Criação do banco de dados

### 1. No action menu vamos em Bare Metal, VM and Exadata

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/actionmenu.png" >
</p>

### 2. Clique en Create DB System

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/createdb1.png" >
</p>

### 3. Vamos preencher os campos com as informações:

- Compartment: workshopOCI
- Name your DB system: DBWorkshop
- Select a shape type: Virtual Machine
- Oracle Database software edition: Standard Edition
- Carregue sua chave SSH Pública
- Selecione a VNC e subnet Pública criadas no Lab 100
- Hostname prefix: workshopOCI

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/createdb2.png" >
</p>

Clicar em next e preencher:

Password: Sua senha

E então clicar em 

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/createdb3.png" >
</p>

### 4. Esperar o Banco de Dados ser Provisionado

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/provisioning.png" >
</p>
