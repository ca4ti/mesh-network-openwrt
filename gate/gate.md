# Gate
O gate faz parte do nível 1 da topologia mesh e é o responsável por oferecer um AP aos STAs. Para isso ele deve possuir, no mínimo, duas interfaces de rede. Ele pode fazer uma comunicação direta com o Portal ou pode passar por um ou mais Stations.

## Equipamentos
Nosso router apesar de oferecer duas antenas e permitir SSID múltiplo, oferece apenas **uma interface física**. Um empecilho para nosso objetivo. Porém o router dispõe de uma porta USB. Para poder então utilizar o Gate da forma devida utilizamos uma antena USB que servirá como nossa segunda interface. Para tal, devemos configurá-la.
* TL-WR842ND da TP-Link + OpenWrt Chaos Calmer 15.05
* INSERIR DETALHES DA ANTENA USB!

### Configuração
Estando em uma sessão SSH com nosso router, devemos primeiro atualizar a lista de dependências do sistema. Como **root** execute:
```bash
opkg update
opkg install usbutils
```
Feito isso, execute `lsusb` para listar os dispositivos conectados. Nossa saída foi:
```
Bus 001 Device 009: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
