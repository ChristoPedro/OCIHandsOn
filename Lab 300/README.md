# Storage

No OCI encontramos 3 tipos de storage

- [Object Storage](https://docs.cloud.oracle.com/pt-br/iaas/Content/Object/Concepts/objectstorageoverview.htm)
- [File Storage](https://docs.cloud.oracle.com/en-us/iaas/Content/File/Concepts/filestorageoverview.htm)
- [Block Volume](https://docs.cloud.oracle.com/pt-br/iaas/Content/Block/Concepts/overview.htm)

Nesse lab vamos criar um Block Valume e associá-lo a nossa VM Púlica

## Criando um Block Volume

### 1. No Action Menu vamos em Block Storage->Block Volume

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20300/images/actionmenu.png" >
</p>

### 2. Se certifique que estamos no Compartiment que criamos no Lab 000

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20100/images/changecompartment.png" >
</p>

### 3. Clicar em Create Block Volume

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20300/images/createblock.png" >
</p>

### 4. Preecher os campos

- Name: WorkshopBV
- Size: 1024
- Volume Performance: Balanced

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20300/images/createscreen.png" >
</p>

### 5. Clicar em Create Block Volume

Vamos esperar o ícone do BV ficar ver e available

## Conectar o Block Volume a Instancia Pública

### 1. Dentro dos detalhas do boot volume vamos em Atacched Instances

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20300/images/attached1.png" >
</p>

### 2. Clicar em Attach Instance

- Selecionar a instência Bastion
- E qualquer Device Name

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20300/images/attached2.png" >
</p>

Clicar em Attach

### 3. Copiar comandos

Com o block attachado vamos clicar no menu do lado direito da lista de instâncias e ir em iCSI Commands & Information

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20300/images/attached3.png" >
</p>

E copiar os comando para realizar o Attach lógico

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20300/images/attached4.png" >
</p>

### 4. Criado o Attach lógico

Colar os comandos no terminal do Bastion e executa-los

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20300/images/logical1.png" >
</p>

