<div align="center"><H2>Configuration d'un service DHCP</H2></div>

## Pré-requis techniques

VM serveur Ubuntu       
VM client Debian 
pour simplifier, agissez en tant qu'utilisateur système

## Configuration de l'adresse IPv4

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

![DHCP_conf client 2024-11-18 110409](https://github.com/user-attachments/assets/c99e7b61-192a-44b2-95dd-5a8887b1c5d2)


Après avoir modifié le fichier, redemarrer le service DHCP 

```
service isc-dhcp-server restart
```

## Test du Protocole DHCP Sur la VM Debian client

Editer le fichier ```nano /etc/network/interfaces```

En y rajoutant ces lignes.
```
# The primary network interface
allow-hotplug enp0s3
iface enp0s3 inet dhcp
```

```
ifup enp0s3
ifdown enp0s3
```
Verification de l'adressage IP dans la plage du serveur DHCP, sur le client ( Linux Debian ) 

![DHCP_ipRange client 2024-11-18 110409](https://github.com/user-attachments/assets/240ba314-c5ed-414f-833f-11f7974a6a68)

## Mise en place d'une attribution statique avec l'adresse MAC pour obtenir l'adresse IP 172.20.0.10

Sur la VM server Ubuntu : 

editer ```nano /etc/dhcp/dhcpd.conf``` y ajouter les lignes suivantes :

```
host LIN_debian {
hardware ethernet 08:00:27:39:27:17;
fixed-address 172.20.0.10;
}
```




