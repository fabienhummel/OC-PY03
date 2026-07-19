# Veille technologique HomeSkolar

## Objectif

La veille vise à maintenir une application sûre, stable et simple à faire évoluer sans augmenter inutilement la complexité technique.

## Choix retenus

| Couche | Technologie | Justification pour HomeSkolar |
|---|---|---|
| Serveur web | Django 5.2 LTS | Framework complet intégrant routage, formulaires, authentification, ORM et protections de sécurité. |
| Interface | Gabarits Django | Rendu côté serveur adapté à une application fonctionnelle sans front-end séparé. |
| Présentation | Bootstrap 5.3 | Composants responsive et cohérents sur ordinateur, tablette et mobile. |
| Données | PostgreSQL | Base relationnelle robuste, adaptée aux relations entre utilisateurs, conversations, rendez-vous et tâches. |

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
