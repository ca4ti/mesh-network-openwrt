# Gate
![Gate](gate.png)

O gate está na extremidade de uma rede mesh mais próxima dos clientes desta rede, é o responsável por oferecer um AP aos STAs. Para isso ele deve possuir, no mínimo, duas interfaces de rede. Podendo fazer uma comunicação direta com o Portal ou através de uma ou mais Mesh Stations.

## Equipamento
Nosso router apesar de oferecer duas antenas e permitir SSID múltiplo, oferece apenas **uma interface física**. Um empecilho para nosso objetivo. Já que para evitar o *intrafluxo*, utilizamos canais diferentes para comunicação nos rádios. Porém o router dispõe de uma porta USB. Para poder então solucionar nossa problemática e utilizar o Gate de forma devida, adicionamos uma antena USB que servirá como nossa segunda interface.

Para a realização da proposta dispomos dos seguintes equipamentos:
* TL-WR842ND da TP-Link (Roteador)
* TL-WN721N da TP-Link (Antena USB)

### Configuração
#### OpenWrt
É necessário antes de tudo, substituir a firmware do equipamento, utilizaremos o ***OpenWrt Chaos Calmer 15.05*** como novo Sistema.

Para seguir com a alteração da firmware é essencial termos certeza que nosso dispositivo suporta o OpenWrt. A consulta pode ser feita na [Tabela de Hardware](http://wiki.openwrt.org/toh/start). Atente para a versão do equipamento. Nosso caso em particular é um [TL-WR842ND v2](http://wiki.openwrt.org/toh/hwdata/tp-link/tp-link_tl-wr842nd_2). Nesta página é possível localizar informações úteis para os próximos passos como o **Target** (ar71xx) que será útil na página de [downloads](http://downloads.openwrt.org/chaos_calmer/15.05/), onde iremos adquirir nossa versão do *Chaos Calmer*. Basta inserir o *Target* obtido anteriormente e prosseguir para o diretório `generic/` onde localizaremos nossa versão ideal do [OpenWrt](http://downloads.openwrt.org/chaos_calmer/15.05/ar71xx/generic/openwrt-15.05-ar71xx-generic-tl-wr842n-v2-squashfs-factory.bin) e faremos o Download. Ou atalhe com:
```bash
$ wget http://downloads.openwrt.org/chaos_calmer/15.05/ar71xx/generic/openwrt-15.05-ar71xx-generic-tl-wr842n-v2-squashfs-factory.bin
```

Para instalá-lo, acesse o painel de controle atual do seu roteador, possivelmente em [192.168.0.1](http://192.168.0.1/). Realize o login com suas credenciais já definidas previamente ou caso contrário, utilize `admin` para o usuário e senha que é o padrão por convenção. Posteriormente procure por Software Updates e realize upload da imagem do OpenWrt.

Com o OpenWrt Instalado, o endereço IP do roteador também será alterado. Acesse [192.168.1.1](http://192.168.1.1/) e crie uma senha para o root, ela será necessária para poder utilizar o SSH.

#### Antena USB
Partindo do ponto que estamos em uma sessão SSH ativa. Devemos atualizar a lista de dependências do sistema e instalar um utilitário para reconhecer os dispositivos conectados ao router. Como **root** execute:
```bash
\# opkg update
\# opkg install usbutils
```
Feito isso, execute `lsusb` para listar os dispositivos conectados. Nossa saída foi:
```
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
Em seguida vamos instalar o drive da antena USB. Para isso:
```bash
\# opkg install kmod-ath9k-htc
```
É possível checar o log do buffer através do comando `dmesg` e confirmar se a instalação ocorreu com sucesso.

Se você chegou até aqui, pode substituir os arquivos **network** e **wireless** localizados em `/etc/config/` pelos respectivos arquivos neste repositório.
