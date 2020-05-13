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

## Criar conexão com o banco criado

### 1. Primeiro precisamos adicionar o banco a uma NSG para habilidar a porta 1521

Acessar a sua VNC de pois ir em Network Security Group e clicar em Create Network Security Group

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/creatensg.png" >
</p>

E Preencher os Campos

- Name: databaseSG
- Compartment: O compartment criado no Lab 000

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/creatensg1.png" >
</p>

E Clicar em next

Agore precisamos escrever a regra de ingress para a NSG

- Direction: Ingress
- Source Type: CIDR
- Source CIDR: 0.0.0.0/0
- IP Protocol: TCP
- Destination Port Range: 1521

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/creatensg2.png" >
</p>

Deplois Clicar em Create

### 2. Vincular a NSG ao Banco de Dados

Voltando a página do Banco de Dados criados, vamos clicar em edit do lado de NSG

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/creatensg3.png" >
</p>

Selecionar a NSG Criada e Salvar

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/creatensg4.png" >
</p>

### 4. Antes de Conctar precisamos de algumas informações

- Primeiro o nome do seu database que vai ser seu SID

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/databasename.png" >
</p>

- Depois vamos até a lista de nodes e conseguir o IP Público

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/ippublico.png" >
</p>

### 3. Conectando ao Banco através do SQLDeveloper


Abrindo o SQLDeveloper crie uma nova conexão preencha o dados.

- Name: WorkshopDB
- Nome do Usuário: sys as sysdba
- Senha: A senha que utilizou na criação do database
- Hostname: Ip Publico do node
- SID: nome do database

Depois é só testar a conexão e se conectar

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20400/images/testeconnection.png" >
</p>
