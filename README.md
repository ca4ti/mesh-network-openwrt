# Mesh Network
Rede mesh ou rede de malha, é uma alternativa de protocolo ao padrão 802.11 para diretrizes de tráfego de dados e voz além das redes a cabo ou infraestrutura wireless.

Uma rede de infraestrutura é composta de Access Point e clientes, os quais necessariamente devem utilizar aquele AP para trafegarem em uma rede. Uma rede mesh é composta de vários nós/roteadores, que passam a se comportar como uma única e grande rede, possibilitando que o cliente se conecte em qualquer um destes nós. Os nós têm a função de repetidores e cada nó está conectado a um ou mais dos outros nós. Desta maneira é possível transmitir mensagens de um nó a outro por diferentes caminhos.

## Topologia
![Topologia Mesh](mesh.png)

Na essência, existem quatro tipos de agentes numa rede mesh. São eles:
* `Portal` são os routers que se comunicam com a internet diretamente.
* `Station` fazem a malha, estando ao centro da nuvem de routers. Comunicam-se com os Portal e Gate.
* `Gate` são responsáveis pelos Access Points.
* `STA` Dispositivos finais que se conectam ao AP via Wi-Fi ou cabo.

Routers com 3 ou mais antenas podem realizar funções de Station e Gate ao mesmo tempo. A grande vantagem é cobrir uma área maior com APs.

## Repositório
Este repositório está organizado com base na topologia das *mesh networks*. Ele é mantido pelo grupo de Redes Mesh do LAR-A, Laboratório de Redes de Aracati.

### Cenário
Tendo em vista nosso número limitado de equipamentos, montaremos um cenário composto de Portal, Station e Gate. Sendo uma unidade para cada tipo de agente. Assim como ilustra a figura:
![Cenário](cenario.png)

Configuraremos tal cenário com as especificações abaixo listadas:
* **Portal**
  * DHCP: On
  * Canal: 1
  * IP: 192.168.20.1
* **Station**
  * DHCP: Off
  * Canal: 1 e 6
  * IP: 192.168.30.1
* **Gate**
  * DHCP: Off
  * Canal: 6 e 11
  * IP: 192.168.40.1

### Equipamento
Para a execução dos testes utilizamos seguintes equipamentos:
* Harware:
  * TL-WR842ND da TP-Link (Roteador)
  * TL-WN721N da TP-Link (Antena USB)
* Software:
  * OpenWrt Chaos Calmer 15.05


#### Navegação
1. [Página Inicial](https://github.com/ivomarsan/mesh-network-openwrt)
2. [Gate](https://github.com/ivomarsan/mesh-network-openwrt/tree/master/gate)
3. [Station](https://github.com/ivomarsan/mesh-network-openwrt/tree/master/station)
4. [Portal](https://github.com/ivomarsan/mesh-network-openwrt/tree/master/portal)
