---
title: "Copy-On-Write"
date: 2020-06-11T23:10:12+02:00
weight: 3
draft: false
---

### Le copy-on-write

Le copy-on-write ( CoW ) permet de partager les layers des images entre les conteneurs.  
Dès que le conteneur à besoin d'ecrire dans un fichier existant dans une image, celui-ci est copié dans le layer en écriture du conteneur puis modifié.  
On retrouve ce principe dans les snapshots BTRFS, le provisioning VMwawre,...  

Grâce à cela, le demarrage des conteneurs est rapide, pas besoin de copier l'image.  

Le système de fichier CoW  recommandé et supporté par docker est ***Overlay2***  
L'avantage  est qu'il est disponible sur tous les kernel linux recent.

Containers that write a lot of data will consume more space than containers that do not. This is because most write operations consume new space in the container’s thin writable top layer. If your container needs to write a lot of data, you should consider using a data volume.

Les conteneurs qui ecrivent beaucoup de données vont par contre consommer plus d'espace et seront plus lent, d'autant plus si le fichier à copier est gros.
Dans ce cas la, l'utilisation d'un volume est recommandé.

{{% notice note %}}
Les volumes seront abordés un peu plus tard dans les chapitres.
{{% /notice %}}


### Démo

- Lancer 5 conteneurs avec l'image utilisé précédement `zaggash/random`
- Chercher les IDs des conteneurs fraîchement démarré.  
  

* Lancer un shell dans un conteneur puis ajouter un fichier dans */root*
* Inspecter le conteneur avec `docker inspect` puis chercher dans le json:
```json
[...]
"GraphDriver": {
    "Data": {
[...]
        "MergedDir": "[...]",
...
```
-  Verifier le contenu de ce dossier.
-  Executer la commande `mount` sur la VM, qu'en concluez vous ?