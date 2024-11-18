Configuration d'un service DHCP 


VM serveur Ubuntu 
VM client Debian 

Ensuite il faut installer le paquet suivant :

"bash
apt-get install isc-dhcp-server"

- Une fois installé, il faut éditer le fichier suivant :

```bash
nano /etc/default/isc-dhcp-server
```

- Dans ce fichier, à la ligne ci-dessous, il faut indiquer quelle interface réseau nous allons utiliser :

```bash
INTERFACESv4=""
```

- Dans mon cas, l'interface réseau est la suivante (vous pouvez la trouver avec un ip a dans le terminal de votre machine) :

```bash
INTERFACESv4="enp0s8"
```

- Dans le prochain fichier à éditer, nous allons indiquer les configurations IP à fournir :

```bash
nano /etc/dhcp/dhcpd.conf
```
