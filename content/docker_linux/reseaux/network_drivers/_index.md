---
title: "Les Pilotes Réseau"
date: 2020-06-12T23:23:40+02:00
weight: 1
draft: false
---

Docker inclut plusieurs drivers Réseau que l'on peux choisir avec l'option `--net <driver>`
- bridge (par default)
- none
- host
- container

### Le *bridge*

Par default le conteneur obtient un interface virtuel eth0 en plus de son interface de bouclage (127.0.0.1)  
Cette interface est fournit par une paire de *veth*.  

Elle est connecté au Bridge Docker appelé docker0 par default.  
Les adresses sont alloué dans un reseau privé interne 172.17.0.0/16 par défault.  

Le traffic sortant passe par une régle iptables MASQUERADE, puis le traffic entrant et naté par DNAT.  
Les régles sont automatiquement gérée par Docker.

### Le *null* driver

Par grand chose à dire sur celui-là, Si ce n'est que le conteneur ne peux pas envoyer ni recevoir de traffic.  
Il obtient uniquement son adresse local *lo*

### Le *host* driver

Le conteneur executé avec ce driver voit et accède au interfaces de l'hôte.  
Le traffic n'est donc pas naté et ne passe pas par une veth.  

Ce driver permet donc d'avoir les performances natives de la carte réseau.
Très pratique dans des applications sensiblent à la latence (Voip, streaming, ...)

### Le driver *container*

Celui-ci est un peu spécial car il permet de réutiliser la stack réseau d'un autre conteneur.  
Les deux conteneurs partagent la même interface, IP, routes, ...  
Ils peuvent communiquer au travers de 127.0.0.1.  
