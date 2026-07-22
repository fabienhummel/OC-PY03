# Journal des versions

## 3.1.0 — 2026-07-22

- suppression des classes `Accompagnement` et `Notification`, ainsi que de `TypeNotification`, dans le modèle métier ;
- relation directe entre `Eleve` et `Tuteur`, avec absence temporaire de tuteur autorisée ;
- suppression des regroupements par package dans le diagramme de classes ;
- conservation de deux héritages, d’une composition `Conversation`–`Message` et d’associations simples sans flèche ;
- synchronisation de la source PlantUML, de l’export SVG, des spécifications techniques et du cahier des charges final ;
- méthode de veille explicitée et versions cibles fixées : Python 3.14, Django 5.2 LTS, Bootstrap 5.3.x et PostgreSQL 17 ;
- modèle final réduit à sept classes avec l’objet unique `ElementSuivi` ;
- critères d’acceptation des 17 User Stories reformulés en Étant donné–Quand–Alors ;
- présentation et livrables finaux régénérés et contrôlés ;
- traçabilité : OCPY3-95 à OCPY3-105.

## 3.0.0 — 2026-07-19

- publication de la version finale du cahier des charges aux formats ODT et PDF ;
- recentrage du document sur les spécifications fonctionnelles, la veille technologique, les spécifications techniques et le diagramme de classes UML ;
- ajout d’un sommaire paginé et amélioration de la mise en page ;
- retrait du Backlog Produit du cahier des charges, celui-ci restant publié séparément sur GitHub ;
- conservation des cinq diagrammes de cas d’utilisation en annexes complémentaires.

## 2.1.0 — 2026-07-19

- ajout du Kanban public du Backlog Produit ;
- présentation graphique en cartes et colonnes « Prêt », « En cours » et « Terminé » ;
- formalisation de la Definition of Ready et de la Definition of Done ;
- documentation des dépendances explicites entre les 17 User Stories ;
- ajout des liens d’accès au Kanban dans le dépôt.

## 2.0.0 — 2026-07-19

- restructuration du dépôt en dossier client HomeSkolar ;
- consolidation des décisions de cadrage ;
- mise à jour des spécifications fonctionnelles et techniques ;
- intégration du cahier des charges client aux formats PDF et ODT ;
- ajout du backlog produit priorisé et estimé ;
- ajout des cinq diagrammes de cas d’utilisation et du diagramme de classes validé ;
- suppression des contenus sans lien avec le produit ou sa conception.

## 1.0.0

- première version du dossier de conception.
