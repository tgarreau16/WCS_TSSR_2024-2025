Configuration d'un service DHCP, pour simplifier, agissez en tant que compte système ( ROOT )

VM serveur Ubuntu       
VM client Debian 

**Configuration de l'adresse IPv4**

Pour définir l'adresse IPv4 fixe du serveur, editer le fichier ``/etc/network/interfaces``                          
```#The primary network interface
allow-hotplug enp0s3
iface enp0s3 inet static
        address 172.20.0.2
        gateway 172.20.0.1
```
Redémarrer la carte réseau et actualiser son adresse fixe en utilisant la commande 
```systemctl restart networking.service```

Ensuite il faut installer le paquet suivant :

```
apt-get install isc-dhcp-server
```

Une fois installé, éditer le fichier suivant :

```
nano /etc/default/isc-dhcp-server
```
Dans ce même fichier, il faut indiquer quelle interface réseau à utiliser :

```ìp a```

```
INTERFACESv4="enp0s3"
```
Editer le fichier avec la commande ```nano /etc/dhcp/dhcpd.conf``` pour indiquer les configurations IP à fournir.

```
# Notre configuration pour le réseau 172.20.0.0
subnet 172.20.0.0 netmask 255.255.255.0 {
range 172.20.0.100 172.20.0.200;
#option domain-name-servers 8.8.8.8;
#option domain-name "reseau.lan";
#option routers 172.18.0.1;
#option broadcast-address 172.18.255.255;
default-lease-time 600;
max-lease-time 7200;
}
```

Après avoir modifié le fichier, redemarrer le service DHCP 

```
service isc-dhcp-server restart
```

```
ifup enp0s3
ifdown enp0s3
```

