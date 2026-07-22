# Modélisation UML

Les diagrammes représentent uniquement les deux acteurs métier retenus : **élève** et **tuteur**.

## Diagrammes de cas d’utilisation

- [Vue globale](export/cas-utilisation-global.svg)
- [Gestion du compte](export/cas-utilisation-compte.svg)
- [Communication](export/cas-utilisation-communication.svg)
- [Rencontres](export/cas-utilisation-rencontres.svg)
- [Tâches](export/cas-utilisation-taches.svg)

## Diagramme de classes

- [Diagramme de classes global validé](export/diagramme-classes-homeskolar-valide.svg)

Le modèle simplifié comporte huit classes, sans regroupement par package : `Utilisateur`, `Eleve`, `Tuteur`, `Conversation`, `Message`, `RendezVous`, `EvenementPersonnel` et `Tache`.

- `Eleve` et `Tuteur` héritent d'`Utilisateur` ;
- une seule composition est retenue entre `Conversation` et `Message` ;
- les autres liens sont des associations simples sans flèche, avec leurs cardinalités ;
- la relation élève–tuteur est directe : un élève peut temporairement ne pas avoir de tuteur, puis possède au plus un tuteur ;
- les indicateurs de messages non lus et de tâches attribuées sont calculés depuis les objets concernés et ne nécessitent pas de classe `Notification` persistante.

Cette version prend en compte les décisions tracées dans OCPY3-95 à OCPY3-98 à la suite du retour de mentorat du 20 juillet 2026.

## Sources

Les fichiers PlantUML modifiables se trouvent dans le dossier [`source`](source/). Les exports SVG du dossier [`export`](export/) peuvent être consultés directement dans GitHub ou intégrés à la documentation.

Toute évolution d’une règle métier doit être répercutée dans la source PlantUML, l’export correspondant, les spécifications et le backlog.
