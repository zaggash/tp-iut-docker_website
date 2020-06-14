---
title: "Avant Docker"
menuTitle: ""
date: 2020-06-08T23:09:18+02:00
weight: 4
draft: false
---

Les applications étaient principalement toutes installées sur des Machines Virtuelles.  
Certaine fois plusieurs applications partage la même VM avec ses propres librairies, dependances, fichiers de configurations...

Les installations se sont ensuite automatisées avec Ansible, Chef, Puppet,... mais il est très facile de mofifier un fichier directement sur la machine sans changer le template.  
Ce qui rend les environement certaine fois non fiable.  

Les Ops et Dev n'ont pas forcement une manière simple partager les applications.  
Les environements varient ce qui crée des lenteurs et des frictions entre Dev et Ops.

![DevVsOps](/images/meme_dev_vs_ops.jpg?featherlight=false&width=40pc)