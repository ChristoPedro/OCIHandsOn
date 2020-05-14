# Compute

Nesse lab vamos criar duas instancias de compute, uma em uma subnet publica e outra em uma subnet privada. Vamos utilizar a instancia na rede pública como bastion para acessar a instancia na rede privada. Abaixo temos o desenho da arquiteutra.

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/tunel.png" >
</p>

Para mais informações sobre compute intances acesse a documentação [aqui](https://docs.cloud.oracle.com/en-us/iaas/Content/Compute/Concepts/computeoverview.htm)

## Criando um par de Chave SSH

Se não tiver o putty instalado pode utilizar o par de chaves que estão [aqui](https://raw.githubusercontent.com/ChristoPedro/OCIHandsOn/master/Chaves.zip).

Ou seguir [esse](https://docs.rightscale.com/faq/How_Do_I_Generate_My_Own_SSH_Key_Pair.html) tutorial que ensina a gerar para Windows e Linux/Unix.

## Criando uma instancia de Compute no OCI (Subnet Pública)

### 1. No action menu acessar Compute->Instances

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/actionmenu.png" >
</p>

### 2. Certifique-se que está no compartment workshop OCI

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20100/images/changecompartment.png" >
</p>

### 3. Clicar em Create Instance

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/createInstance.png" >
</p>

### 4. Preencher as informações

- Name: Bastion
- Image or operating System: Oracle Linux 7.8
- VCN Compartment: workshopOCI
- Select VCN: workshopVNC
- Subnet Compartment: workshopOCI
- Subnet: Public Subnet-workshopVNC

Adicione a chave SSH Pública e clique em create.

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/instancecreatept1.png" >
</p>

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/instancecreatept2.png" >
</p>

### 5. Quando o ícone estiver verde a máquina pode ser acessada

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/instancePronta.png" >
</p>

## Criando uma instancia de Compute no OCI (Subnet Privada)

Vamos Seguir os mesmos passos da criação da instância anterior, mas dessa vez selecionaremos uma subnet privada.

### Preencher as informações

- Name: Pivate
- Image or operating System: Oracle Linux 7.8
- VCN Compartment: workshopOCI
- Select VCN: workshopVNC
- Subnet Compartment: workshopOCI
- Subnet: Private Subnet-workshopVNC

Adicione a chave SSH Pública e clique em create.

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/privateInstance.png" >
</p>

## Acessando as Instancias

A conexão pode ser feita através de ssh no windows através do putty ou gitbash (em alguns já tem o SSH habilidado no prompt) e no MAC e Linux através do terminal.

Vamos primeiro nos conectar a instancia que está em uma subnet pública e através dela nos conectar a que está na subnetprivada.

### 1. Voltando a página das intancias de compute vamos clicar pegar o IP público da instância Bastion.

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/instances.png" >
</p>

### 2. Fazer SSH utilizando o IP Publico e a chave privada

Vamos abrir o Putty e colar o IP no campo Host Name

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/puttypt1.png" >
</p>

Depois, no menu a esquerda vamos em SSH->Auth e vamos selecionar a chave privada

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/puttypt2.png" >
</p>

Depois voltar para Session

Salvar a Conexão com o nome Bastion assim como nas imagem e clicar em open

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/savebastion.png" >
</p>

Vamos logar como opc

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/puttypt3.png" >
</p>

Se tudo ocorrer corretamente já terá acesso ao Bastion

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/bastion.png" >
</p>

## Acessando a Instância Private

Essa é a arquitetura construida, podemos ver que a instância privada não tem acesso direto a Internet, então para poder acessá-la vamos fazer um tunel através do Bastion.

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/tunel1.jpg" >
</p>

Abaixo temos o exemplo de tunelamento através do putty, mas também pode ser feito através de SSH ou do MobaXterm.

### 1. Tunelamento através do Putty

Vamos fechar a instancia aberta do putty e abrir novamente, se a conexão já estiver salva, é só selecionar na lista e adicionar a chave privada novamente.

Mas antes de se conectar no Menu do canto esquerdo vamos em Connection->SSH->Tunnels

Vamos preencher os campos com:

- Source Port: 5000 - Essa será a porta local onde o trafego será direcionado
- Destination:{ip privado}:22 - ip privado e a porta de destino do tunnel

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/tunnel1.png" >
</p>

Depois clicar em Add

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/tunnel2.png" >
</p>

Com o tunnel adicionado basta apenas clicar em Open e inicar a conexão com a VM Bastion

### 2. Conectar à Instância privada através do tunnel

Agora vamos abrir outra javela no putty, sem fechar a anterior e configurar a conexão, mas dessa vez vamos preecher a seguinte forma

- Hostname: localhost
- Port 5000

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/conectionprivada.png" >
</p>

Adicione a chave privada como anteriormente e clique em open

Se tudo estiver correto será capaz de conectar

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20200/images/conexaoprivada.png" >
</p>