# Network

Nesse lab vamos criar uma VCN, no compartment que acabamos de criar, que servira para a conexão dos outros elementos que seráo criados nos préoximos laboratórios.

Será criado uma VCN contendo uma subnet publica e uma privada, depois vamos passar por todos os elementos que podem compor uma rede virtual.

Para mais informações sobre redes temos [aqui](https://docs.cloud.oracle.com/en-us/iaas/Content/Network/Concepts/overview.htm) a documentação.

## Criação de uma VCN (Virtual Cloud Network)

### 1. No action menu acessar Networking->Virtual Cloud Networking

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20100/images/acessvnc.png" >
</p>

### 2. Mudar o compartment para workshopOCI

No campo esquerto da tela temos um drop list com os compartments, selecione o compartment workshopOCI que criamos no lab anterior.

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20100/images/changecompartment.png" >
</p>

### 3. Clicar em Start VNC Wizard

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20100/images/vncwizard.png" >
</p>

### 4. Selecionar VNC With Internet Connectivity

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20100/images/internetconect.png" >
</p>

### 5. Preencher as informações:

- VCN Name: workshopVNC
- Compartment: workshopOCI
- VCN CIDR Block: 10.0.0.0/16
- Plublic Subnet CIDR Block: 10.0.0.0/24
- Private Subnet CIDR Block: 10.0.0.1/24

VCN CIDR Block representa o tamanho da sua rede, no OCI é possivel criar redes desde /30 até /16 e sempre recomendado seguir o padrão de IP's privados 10.0.0.0/8, 172.16/12, e 192.168/16

<p align="center">
  <img src="https://github.com/ChristoPedro/OCIHandsOn/blob/master/Lab%20100/images/basicinfo.png" >
</p>
