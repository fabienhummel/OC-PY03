# Veille technologique — HomeSkolar

## 1. Objet et périmètre

Cette veille prépare l’orientation technique de HomeSkolar sans détailler encore l’implémentation. Elle porte uniquement sur trois choix structurants : interface web, back-end Python et base de données. Les besoins couverts sont la gestion des comptes, la messagerie et ses notifications internes, le calendrier des rencontres et événements, ainsi que le suivi des tâches.

## 2. Critères d’évaluation

Les solutions sont comparées selon une grille commune : adéquation fonctionnelle, simplicité de mise en œuvre, simplicité de maintenance, stabilité et maturité, qualité de la documentation, activité de la communauté, évolutivité raisonnable, coût et disponibilité. Le principe directeur est de préférer une solution intégrée et maintenable à une architecture distribuée dont la complexité n’est pas justifiée par le besoin.

## 3. Besoins techniques issus des fonctionnalités

| Domaine fonctionnel | Besoins techniques à couvrir |
|---|---|
| Comptes | inscription, authentification, autorisations, mot de passe et données personnelles |
| Communication | conservation et affichage des messages, statut lu/non lu, épinglage et notification interne |
| Rencontres | création et consultation des rendez-vous et événements dans une vue calendrier |
| Tâches | création, attribution, suivi jusqu’à la prochaine rencontre et notification interne |
| Ensemble | interface responsive, règles métier centralisées, validation des données et persistance relationnelle |

## 4. Solutions étudiées

### Interface web

| Solution | Avantages | Limites | Appréciation |
|---|---|---|---|
| Gabarits Django + Bootstrap 5.3 | architecture unique, peu d’outillage, composants responsive et approche mobile-first | interactions très riches à compléter ponctuellement en JavaScript | très adaptée au périmètre |
| React | composants réutilisables et écosystème important | application front séparée, chaîne de build et API à maintenir | robuste mais surdimensionnée ici |
| Vue | progressif, accessible et intégrable | ajoute tout de même un framework JavaScript et une gestion d’état côté client | alternative crédible si l’interface devient plus interactive |

### Back-end Python

| Solution | Avantages | Limites | Appréciation |
|---|---|---|---|
| Django 5.2 LTS | authentification, ORM, formulaires, vues et gabarits intégrés ; version à support prolongé | cadre plus structurant et plus volumineux qu’un microframework | meilleur compromis global |
| Flask 3.1 | minimal, flexible et facile à démarrer | assemblage d’extensions nécessaire pour comptes, ORM et structure applicative | simple au départ, maintenance plus dispersée |
| FastAPI | typage, validation et documentation OpenAPI ; très adapté aux API | impose de compléter l’authentification, l’interface et plusieurs fonctions métier | pertinent surtout pour une architecture API/SPA |

### Stockage

| Solution | Avantages | Limites | Appréciation |
|---|---|---|---|
| PostgreSQL | fiable, transactionnel, mature, open source et bien intégré à Django | service de base de données à administrer | choix recommandé |
| SQLite | aucune administration, excellent pour le développement et les tests | concurrence d’écriture et exploitation multi-utilisateur plus limitées | réservé au développement local |
| MySQL | mature, répandu et supporté par Django | aucun avantage décisif pour ce projet face à PostgreSQL | alternative possible |

## 5. Matrice de décision

Échelle : 1 = faible, 5 = très favorable. La note sert d’aide à la décision et non de preuve isolée.

| Solution | Adéquation | Simplicité | Maturité | Documentation / communauté | Maintenance | Coût | Total / 30 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Django + gabarits + Bootstrap | 5 | 5 | 5 | 5 | 5 | 5 | 30 |
| React + API Python | 5 | 2 | 5 | 5 | 3 | 5 | 25 |
| Vue + API Python | 5 | 3 | 5 | 5 | 3 | 5 | 26 |
| Django | 5 | 5 | 5 | 5 | 5 | 5 | 30 |
| Flask | 4 | 3 | 5 | 5 | 3 | 5 | 25 |
| FastAPI | 4 | 3 | 5 | 5 | 3 | 5 | 25 |
| PostgreSQL | 5 | 4 | 5 | 5 | 5 | 5 | 29 |
| SQLite | 3 | 5 | 5 | 5 | 3 | 5 | 26 |
| MySQL | 5 | 4 | 5 | 5 | 5 | 5 | 29 |

## 6. Orientation retenue

L’orientation retenue est une application web monolithique modulaire construite avec Django 5.2 LTS, des gabarits Django enrichis par Bootstrap 5.3 et une base PostgreSQL. Cette combinaison couvre les fonctions demandées dans une seule application, limite les dépendances et les échanges inter-applications, facilite les tests et reste compatible avec une évolution ultérieure vers une API si un besoin réel apparaît.

React et Vue ne sont pas écartés pour des raisons de qualité : ils ne sont simplement pas nécessaires à l’interface actuellement décrite. Flask et FastAPI demanderaient davantage d’assemblage pour couvrir l’ensemble des besoins métier et de sécurité déjà intégrés à Django. SQLite reste adapté au développement local mais n’est pas retenu comme base de production multi-utilisateur.

Cette décision constitue une orientation à préciser dans les spécifications techniques du Sprint S3 ; elle ne fixe pas encore le détail du déploiement, des composants internes ni des versions d’infrastructure.

## 7. Sources validées

Consultation le 12 juillet 2026.

1. Django Software Foundation, « Django 5.2 release notes » et documentation officielle : https://docs.djangoproject.com/en/5.2/releases/5.2/
2. Bootstrap, « Get started with Bootstrap 5.3 » : https://getbootstrap.com/docs/5.3/getting-started/introduction/
3. React, documentation officielle : https://react.dev/
4. Vue.js, « Introduction » : https://vuejs.org/guide/introduction
5. Pallets, documentation Flask 3.1 : https://flask.palletsprojects.com/en/stable/
6. FastAPI, documentation officielle : https://fastapi.tiangolo.com/features/
7. PostgreSQL Global Development Group, documentation officielle : https://www.postgresql.org/docs/current/
8. Django Software Foundation, bases de données supportées : https://docs.djangoproject.com/en/5.2/ref/databases/

## 8. Validation

- Au moins trois sources fiables et directement reliées aux constats : conforme.
- Avantages et limites présentés pour chaque famille : conforme.
- Critères communs et décision justifiée : conforme.
- Technologies stables, documentées et maintenues : conforme.
- Architecture proportionnée au besoin : conforme.
- Absence de duplication détaillée avec les futures spécifications techniques : conforme.

