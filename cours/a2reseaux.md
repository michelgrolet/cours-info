# Réseaux

[Retour à l'accueil](./../README.md)

<details>
<summary> Plan ✨</summary>

- [Réseaux](#réseaux)
  - [Concepts réseau](#concepts-réseau)
    - [Trame](#trame)
    - [LAN](#lan)
    - [VLAN](#vlan)
    - [&IP](#ip)
    - [SSH](#ssh)
      - [Connection SSH avec certificat :](#connection-ssh-avec-certificat-)
      - [Tunnel SSH](#tunnel-ssh)
    - [DHCP](#dhcp)
    - [Serveur HTTP](#serveur-http)
- [Commandes réseau bash](#commandes-réseau-bash)
  - [Fichier de configuration réseau](#fichier-de-configuration-réseau)
- [Éléments réseau](#éléments-réseau)
      - [Hub](#hub)
      - [Switch](#switch)
      - [Routeur](#routeur)
- [Scripts bash](#scripts-bash)
</details>

___
## Concepts réseau

### Trame
data  | ... | ... | Transport                           | IP                  | interface
--    |--   |--   |--                                   |--                   |--
...   |...  |...  |Tcp ou UDP et **#port** (src et dest)|**&IP** (src et dest)|**&mac** (src et dest)

### LAN
Machines sur le même réseau IP. Partagent le même masque (adresse réseau).

### VLAN
LAN logique (construit comme un LAN physique). Permet de "couper un switch en switchs plus petits".  
Sur le terminal VDE d'un switch :
- `vlan/create 1` : crée le VLAN 1
- `port/setvlan 4 1` : attribue le port 4 au VLAN 1
- `vlan/print` : affiche les affectations des ports.

> **Trunk :** port transportant des trames entre différents switchs et différents VLANs.

### &IP
4 octets (32 bits)
- & réseau : n premiers bits
- & machine : 32-n bits
  - Bits & machine à 0 : & réseau
  - Bits & machine à 1 : & broadcast

### SSH
Lors d'une connection par mot de passe, ce dernier peut être intercepté. Il est plus sécurisé de se connecter avec un certificat.

| commande                       | explication                             |
| ------------------------------ | --------------------------------------- |
| `/etc/init.d/ssh start`        | démarre ssh                             |
| `ssh -X &IP`                   | lance ssh vers &IP (X : mode graphique) |
| `scp user@&ip:fichier u@&ip:f` | copie un fichier entre deux machines    |
| `exit` ou `CTRL+D`             | quitte la session ssh                   |

#### Connection SSH avec certificat :
1. `ssh-keygen` 
   - génère un couple de clés privée/publique stockées dans `~/.ssh/id_rsa` et `~/.ssh/id_rsa.pub`.
   - demande de créer une passphrase.
2. Copier `id_rsa.pub` sur le serveur SSH dans `~/.ssh/authorized_keys`.
3. Se connecter au serveur avec la passphrase.

#### Tunnel SSH
`ssh -L 7777:&IP[destination] &IP[intermédiaire]` Crée un tunnel pour le port `7777` de `&IP[destination]` passant par `&IP[intermédiaire]`.

### DHCP
Logiciel sur un réseau qui distribue des &IP du réseau aux nouveaux arrivants.
- &IP réseau/masque
- &IPs disponibles
- = &IP + #eth

### Serveur HTTP
| commande                       | explication                            |
| ------------------------------ | -------------------------------------- |
| `/etc/init.d/apache2 start`    | démarre le serveur apache              |
| `lynx localhost`               | lance localhost sur le navigateur lynx |
| `scp user@&ip:fichier u@&ip:f` | copie un fichier entre deux machines   |
| `exit` ou `CTRL+D`             | quitte la session ssh                  |


# Commandes réseau bash

| commande                                        | explication                                                       |
| ----------------------------------------------- | ----------------------------------------------------------------- |
| `ifconfig`                                      | informations réseau de la machine                                 |
| `ifconfig eth0 &ip`                             | assigne l'ip à l'interface eth0                                   |
| `ifconfig eth0 inet6 add ipv6`                  | assigne l'ipv6 à l'interface eth0                                 |
| `ping &ip`                                      | requête à &ip. &ip doit répondre.                                 |
| `route`                                         | affiche les routes d'une machine ou d'un routeur                  |
| `route add -net &IPReseaudest/24 gw &IProuteur` | ajoute une route ves &IPdest dont le prochain saut est &IProuteur |
| `route del -net &IPdest/24`                     | supprime la route                                                 |
| `ps x`                                          | liste les processus d'une machine                                 |
| `xterm &`                                       | ouvre un autre terminal                                           |



## Fichier de configuration réseau
```bash
auto eth0              #eth0 activée
iface eth0 inet [static||dhcp] #adresses attribuées manuellement||en dhcp
address 192.168.0.1    #spécifier l'&ip sur eth0
netmask 255.255.255.0  #spécifier le masque

allow-hotplug eth0     #lancer au démarrage
```

# Éléments réseau
#### Hub
Reproduit un paquet reçu sur tous les autres ports. Équivaut à un switch non programmable.
,l
#### Switch
Reproduit un paquet reçu vers sa destination.
> **FSTP :** trouve les cycles entre des switchs pour arrêter les bouclages. 

#### Routeur
Relie deux réseaux IP ou transfère des paquets à leur réseau de destination.

# Scripts bash
```bash
# Affiche le nombre de processus en cours d'exécution.
#!/bin/bash
echo $(ps -aux | wc -l) 
```