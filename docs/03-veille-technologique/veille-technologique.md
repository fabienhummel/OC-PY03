# Veille technologique HomeSkolar

## Objectif

La veille vise à maintenir une application sûre, stable et simple à faire évoluer sans augmenter inutilement la complexité technique.

## Méthode suivie

1. Partir des besoins du projet : interface web, back-end Python et base de données.
2. Rechercher des solutions simples avec des requêtes comme `framework web Python LTS`, `Django templates vs React` et `Django supported databases`.
3. Consulter d'abord les documentations officielles, puis recouper les avantages et limites entre plusieurs solutions.
4. Retenir une source si elle est pertinente, récente, maintenue, bien documentée et adaptée au budget. Écarter les contenus non datés, non sourcés ou concernant une version obsolète.

Les sources ont été consultées les 12 et 22 juillet 2026. La veille est revue avant une mise en production et lors d'une alerte de sécurité ou d'une nouvelle version majeure. Elle permet d'anticiper les problèmes de sécurité, de compatibilité et de maintenance.

## Choix retenus

| Couche | Technologie | Justification pour HomeSkolar |
|---|---|---|
| Langage | Python 3.14 | Version stable prise en charge par Django 5.2 et maintenue jusqu’en octobre 2030. |
| Serveur web | Django 5.2 LTS, dernière 5.2.x | Framework complet intégrant routage, formulaires, authentification, ORM et protections de sécurité. |
| Interface | Gabarits Django | Rendu côté serveur adapté à une application fonctionnelle sans front-end séparé. |
| Présentation | Bootstrap, dernière 5.3.x | Composants responsive et cohérents sur ordinateur, tablette et mobile. |
| Données | PostgreSQL 17, dernière 17.x | Base relationnelle robuste, maintenue jusqu’en novembre 2029. |

## Architecture comparée

Une architecture front-end et back-end séparés augmenterait le nombre de composants, les contrats d’interface et le coût de maintenance. Le monolithe Django répond au périmètre actuel avec un déploiement et une sécurité centralisés. Aucune API REST publique n’est nécessaire.

## Sujets suivis

- bulletins de sécurité et versions de maintenance de Django ;
- correctifs et évolutions de Bootstrap 5.3 ;
- versions prises en charge de PostgreSQL ;
- recommandations de sécurité relatives à l’authentification et au courrier de réinitialisation ;
- compatibilité des navigateurs mobiles et de bureau ;
- performance du mécanisme de rafraîchissement de la messagerie.

## Cadence

La veille est réévaluée avant chaque mise en production et lors de la publication d’un bulletin de sécurité concernant un composant du produit. Toute évolution est consignée dans le journal des versions et, si elle modifie le produit, dans le backlog.

## Références officielles

- [Documentation Django](https://docs.djangoproject.com/)
- [Notes de version Django](https://docs.djangoproject.com/en/5.2/releases/)
- [Documentation Bootstrap 5.3](https://getbootstrap.com/docs/5.3/)
- [Documentation PostgreSQL](https://www.postgresql.org/docs/)
- [Versions prises en charge de Python](https://devguide.python.org/versions/)
- [Politique de version de PostgreSQL](https://www.postgresql.org/support/versioning/)
