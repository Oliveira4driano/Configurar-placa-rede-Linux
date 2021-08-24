# Configurar-placa-rede-Linux

requisitos: utlizar o editor nano oi vim

no terminal
#verificar sua placa de rede
ifconfig ou ip addr
e verifique se em qual porta esta reconhecendo: eth0 ou eth1


-- entrar no diretorio
cd /etc/network
-- listar os arquivos
ls
-- abrir o arquivo interfaces
nano interfaces
-- dentro do arquivo adicione os comando
#the loopback network interface
auto enp11s0f0
iface enp11s0f0 inet loopback

auto eth1
allow-hotplug eth1
iface eth1 inet dhcp

sudo /etc/init.d/networking restart


