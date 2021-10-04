# Réseaux

[Retour à l'accueil](./../README.md)

<details>
<summary> Plan ✨</summary>

- [Réseaux](#réseaux)
  - [Introduction](#introduction)
    - [Trame](#trame)
    - [LAN](#lan)
    - [VLAN](#vlan)
    - [&IP](#ip)
    - [SSH](#ssh)
      - [Connection SSH avec certificat :](#connection-ssh-avec-certificat-)
- [Réseaux et Bash](#réseaux-et-bash)
  - [Fichier de configuration réseau](#fichier-de-configuration-réseau)
- [Éléments réseau](#éléments-réseau)
      - [Hub](#hub)
      - [Switch](#switch)
      - [Routeur](#routeur)
</details>

___
## Introduction

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

> **Trunk :** port transportant des trames entre différents switchs entre des VLANs parfois différents.

### &IP
4 octets (32 bits)
- & réseau : n premiers bits
- & machine : 32-n bits
  - Bits & machine à 0 : & réseau
  - Bits & machine à 1 : & broadcast

### SSH
Lors d'une connection par mot de passe, ce dernier peut être intercepté. Il est plus sécurisé de se connecter avec un certificat.

#### Connection SSH avec certificat :
1. `ssh-keygen` 
   - génère un couple de clés privée/publique stockées dans `~/.ssh/id_rsa` et `~/.ssh/id_rsa.pub`.
   - demande de créer une passphrase.
2. Copier `id_rsa.pub` sur le serveur SSH dans `~/.ssh/authorized_keys`.
3. Se connecter au serveur avec la passphrase.


# Réseaux et Bash

| commande                                  | explication                                                       |
| ----------------------------------------- | ----------------------------------------------------------------- |
| `ifconfig`                                | informations réseau de la machine                                 |
| `ifconfig eth0 &ip`                       | assigne l'ip à l'interface eth0                                   |
| `ifconfig eth0 inet6 add ipv6`            | assigne l'ipv6 à l'interface eth0                                 |
| `ping &ip`                                | requête à &ip. &ip doit répondre.                                 |
| `route`                                   | affiche les routes d'une machine ou d'un routeur                  |
| `route add -net &IPdest/24 gw &IProuteur` | ajoute une route ves &IPdest dont le prochain saut est &IProuteur |
| `route del -net &IPdest/24`               | supprime la route                                                 |
| `ps x`                                    | liste les processus d'une machine                                 |
| `/etc/init.d/ssh start`                   | démarre ssh                                                       |
| `ssh &IP`                                 | lance ssh vers &IP                                                |
| `scp user@machine:fichier u@m:f`          | copie un fichier entre deux machines                              |


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

#### Switch
Reproduit un paquet reçu vers sa destination.
> **FSTP :** trouve les cycles entre des switchs pour arrêter les bouclages. 

#### Routeur
Relie deux réseaux IP ou transfère des paquets à leur réseau de destination.