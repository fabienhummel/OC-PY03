# HomeSkolar — dossier de conception

Ce dépôt rassemble la documentation produit et technique de **HomeSkolar**, une application web de mise en relation et de suivi entre élèves et tuteurs.

## Périmètre du produit

HomeSkolar permet à deux acteurs — l’élève et le tuteur — de créer librement leur compte, d’être associés automatiquement, de communiquer, de consulter leurs rendez-vous et de gérer leurs tâches de suivi.

Le produit est conçu comme une application web responsive fondée sur Django 5.2 LTS, les gabarits Django, Bootstrap 5.3 et PostgreSQL.

## Documentation

| Section | Contenu |
|---|---|
| [Contexte et périmètre](docs/01-contexte/README.md) | Objectifs, acteurs, décisions et exclusions |
| [Spécifications fonctionnelles](docs/02-specifications-fonctionnelles/README.md) | Règles métier et comportements attendus |
| [Veille technologique](docs/03-veille-technologique/README.md) | Choix et suivi des technologies |
| [Spécifications techniques](docs/04-specifications-techniques/README.md) | Architecture, données, sécurité et qualité |
| [Backlog produit](docs/05-backlog-produit/README.md) | User Stories, critères d’acceptation, priorités, estimations, dépendances et Kanban |
| [Modélisation UML](docs/06-modelisation-uml/README.md) | Cas d’utilisation et diagramme de classes validé |

## Livrables client

Le [cahier des charges HomeSkolar](livrables/cahier-des-charges/README.md) est fourni aux formats PDF et ODT. Les sources PlantUML sont conservées avec leurs exports SVG afin que les diagrammes restent maintenables.

Le [Kanban public](docs/05-backlog-produit/kanban.md) permet de suivre la réalisation des User Stories et leurs dépendances.

## État du dossier

- périmètre fonctionnel consolidé ;
- choix techniques validés ;
- acteurs limités à l’élève et au tuteur ;
- diagramme de classes validé ;
- backlog initial et dépendances prêts pour la planification ;
- Kanban initial publié ;
- recherche exclue de la première version.
