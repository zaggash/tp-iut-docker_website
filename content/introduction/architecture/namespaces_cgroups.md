---
title: "Namespaces/Cgroups/CoW"
date: 2020-06-09T03:02:54+02:00
draft: false
weight: 3
---

Docker est extremement lié au Kernel.  
Le fonctionnement des conteneurs reposent sur les namespaces, les cgroups et le CopyOnWrite.  
Mais egalement d'autres aspects liés à la sécuritée comme les CAPabilities, seccomp,...  

Ceux qui nous interressent aujourd'hui sont les trois premiers : namespaces, cgroups et le CopyOnWrite.

{{% notice note %}}
Ces aspects seront abordés au cours des exercices du TP.
{{% /notice %}}

Brièvement, les namespaces permettent l'isolation des processus à differant niveaux (PID, User, Network, Mount)  
Les Cgroups permettent l'isolation, la limitation de l'utilisation des ressources (Processeur, Memoire, Utilisation Disque)