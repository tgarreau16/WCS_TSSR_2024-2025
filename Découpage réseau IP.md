## - Découpage Symétrique 

4 Sous réseaux -> 172.16.1.0/24 

Masque sous réseau 32-6 = 26
50 équipements 2^6 - 2 = 62

| Option | Pôle informatique | Pôle développement | Pôle Administratif | Pôle Technicien |
| ------ | :-----------: | :-----------: | :--------: | :--------: |
| Adresse de réseau :   |  172.16.1.0/26 | 172.16.1.64/26 | 172.16.1.128/26 | 172.16.1.192/26
| Début de plage IP disponible : |  172.16.1.1/26 | 172.16.1.65/26 |  172.16.1.129/26 | 172.16.1.195/26
| Fin de plage IP disponible :  |  172.16.1.62/26 |  172.16.1.126/26 | 172.16.1.190/26 | 172.16.1.254/26
| Adresse de broadcast :  |  172.16.1.63/26 | 172.16.1.127/26 | 172.16.1.191/26 | 172.16.1.255/26

## - Découpage Asymétrique 

Pôle informatique (50 équipements : 2^6= 64) : 

Pôle Administratif (20 équipements : 2^5 = 32 )  : 

Pôle Technicien (15 équipements : 2^5 =32 )  :

Pôle développement (12 équipements : 2^4 = 16) : 

| Option | Pole Informatique | Pôle Administratif | Pôle Technicien | Pôle Developpement |
| ------ | :-----------: | :-----------: | :--------: | :--------: |
| Adresse de réseau :   |  172.16.1.0/26 | 172.16.1.64/26 | 172.16.1.94/26 | 172.16.1.127/26
| Début de plage IP disponible : |  172.16.1.1/26 | 172.16.1.65/26 |   172.16.1.95/26 | 172.16.1.128/26
| Fin de plage IP disponible :  |  172.16.1.62/26 |  172.16.1.92/26 | 172.16.1.125/26 | 172.16.1.142/26
| Adresse de broadcast :  |  172.16.1.63/26 | 172.16.1.93/26 | 172.16.1.126/26 | 172.16.1.143/26








