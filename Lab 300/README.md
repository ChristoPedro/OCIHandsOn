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

