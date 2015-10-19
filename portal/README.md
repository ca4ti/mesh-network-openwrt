# Portal
![Portal](portal.png)

Em *mesh networks*, um portal é o router responsável pela conexão com o backbone. Ligando a rede à Internet. Geralmente é o único nó que possui conexão com fio. Portanto, diferentemente dos outros tipos de agentes numa topologia mesh, é necessário, no mínimo, apenas uma interface física wireless para funcionar, visto que a comunicação externa pode ser feita através de um RJ-45 e a interna, via 802.11s com outro nó agente.

## Equipamento
Continuamos utilizando o mesmo roteador, porém, descartamos o uso de uma antena USB auxiliar, devido a limitação da quantidade de equipamento disponível para testes. O que não atrapalhará o cenário explorado.

Para a realização da proposta dispomos do seguinte equipamento:
* TL-WR842ND da TP-Link (Roteador)

### Configuração
#### OpenWrt
É necessário antes de tudo, substituir a firmware do equipamento, utilizaremos o ***OpenWrt Chaos Calmer 15.05*** como novo Sistema.

Para seguir com a alteração da firmware é essencial termos certeza que nosso dispositivo suporta o OpenWrt. A consulta pode ser feita na [Tabela de Hardware](http://wiki.openwrt.org/toh/start). Atente para a versão do equipamento. Nosso caso em particular é um [TL-WR842ND v2](http://wiki.openwrt.org/toh/hwdata/tp-link/tp-link_tl-wr842nd_2). Nesta página é possível localizar informações úteis para os próximos passos como o **Target** (ar71xx) que será útil na página de [downloads](http://downloads.openwrt.org/chaos_calmer/15.05/), onde iremos adquirir nossa versão do *Chaos Calmer*. Basta inserir o *Target* obtido anteriormente e prosseguir para o diretório `generic/` onde localizaremos nossa versão ideal do [OpenWrt](http://downloads.openwrt.org/chaos_calmer/15.05/ar71xx/generic/openwrt-15.05-ar71xx-generic-tl-wr842n-v2-squashfs-factory.bin) e faremos o Download. Ou atalhe com:
```bash
$ wget http://downloads.openwrt.org/chaos_calmer/15.05/ar71xx/generic/openwrt-15.05-ar71xx-generic-tl-wr842n-v2-squashfs-factory.bin
```

Para instalá-lo, acesse o painel de controle atual do seu roteador, possivelmente em [192.168.0.1](http://192.168.0.1/). Realize o login com suas credenciais já definidas previamente ou caso contrário, utilize `admin` para o usuário e senha que é o padrão por convenção. Posteriormente procure por Software Updates e realize upload da imagem do OpenWrt.

Com o OpenWrt Instalado, o endereço IP do roteador também será alterado. Acesse [192.168.1.1](http://192.168.1.1/) e crie uma senha para o root, ela será necessária para poder utilizar o SSH.

#### Configurações Adicionais
Se você chegou até aqui, pode substituir os arquivos **network** e **wireless** localizados em `/etc/config/` pelos respectivos arquivos neste repositório.
