# Configurar-placa-rede-Linux

requisitos: utlizar o editor nano ou vim
Passo 1. Abra um terminal;
Passo 2. Primeiro, é necessário saber qual interface de rede vamos configurar. Para este exemplo, assumirei que configuraremos a interface de rede com fio. Então, veirfique o nome da interface com o seguinte comando;

ip addr show

Passo 4. Na listagem você terá o nome das interfaces de rede. Aquele que corresponde à rede com fio é chamado enp0s3. Algo semelhante deve estar no seu caso. No exemplo acima, ela tem um endereço IP 192.168.250.15. No entanto, quero que o endereço seja 192.168.250.99. Agora que sabemos o nome da interface, precisamos editar o arquivo /etc/network/interfaces;

sudo nano /etc/network/interfaces

e verifique se em qual porta esta reconhecendo: eth0 ou eth1 ou enp11s0f0<br>

-- dentro do arquivo adicione os comando<br>
#the loopback network interface<br>

auto enp11s0f0
allow-hotplug enp11s0f0
iface enp11s0f0 inet dhcp

sudo /etc/init.d/networking restart

# Como definir um endereço IP estático no Debian 10 Buster e derivados

Passo 5. Na linha

iface enp11s0f0 inet static<br>

, o arquivo diz que irá configurar a interface com DHCP, ou seja, para um endereço IP dinâmico. Então, ela tem que ser alterado para configurá-lo de maneira estática. Para isso, mude para esta linha:
iface enp0s3 inet static<br>

Passo 6. Depois dessa linha, os seguintes parâmetros de conexão devem ser adicionados. Lembre-se de que esses parâmetros são um exemplo. Você precisa digitar os correspondentes para sua rede;

address 192.168.250.99<br>
netmask 255.255.255.0<br>
network 192.168.1.1<br>
broadcast 192.168.255.255<br>
gateway 192.168.1.1<br>



Passo 7. Em seguida, reinicie o serviço de rede;<br>

sudo systemctl restart networking

Passo 8. Em seguida, verifique as alterações;<br>

ip addr show


