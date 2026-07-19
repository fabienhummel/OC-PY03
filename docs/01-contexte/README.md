# Contexte et périmètre

## Vision

HomeSkolar facilite l’accompagnement d’un élève par un tuteur au sein d’un espace web unique. L’application regroupe les échanges, les rendez-vous et les tâches utiles au suivi.

## Acteurs

Deux acteurs métier sont retenus :

- **élève** : crée son compte, échange avec son tuteur, consulte ses rendez-vous et gère ses propres tâches ;
- **tuteur** : crée son compte, accompagne plusieurs élèves, échange avec chacun d’eux, organise les rendez-vous et attribue des tâches de suivi.

Il n’existe ni rôle administrateur ni rôle association dans le périmètre.

## Décisions de cadrage

| Domaine | Décision retenue |
|---|---|
| Comptes | Chaque élève et chaque tuteur crée librement son propre compte, sans validation. |
| Données utilisateur | Nom d’utilisateur, mot de passe, adresse électronique, nom et prénom. |
| Âge | Aucune règle liée à la minorité ou à la majorité. |
| Affectation | Un élève possède un seul tuteur ; un tuteur peut suivre plusieurs élèves ; l’affectation est aléatoire. |
| Messagerie | Échanges instantanés limités à l’élève et à son tuteur attitré. |
| Rendez-vous | Le tuteur peut créer, modifier et annuler ; aucune acceptation de l’élève n’est requise. |
| Tâches | Un objet unique sert de tâche, note personnelle ou mémo selon son usage. |
| Notifications | Notifications internes à la plateforme uniquement. |
| Recherche | Aucune fonctionnalité de recherche dans la première version. |
| Interface | Utilisation prévue sur ordinateur, tablette et mobile. |
| Technologies | Django 5.2 LTS, gabarits Django, Bootstrap 5.3 et PostgreSQL. |

## Hors périmètre de la première version

- administration et supervision par une association ;
- gestion de la minorité ou de la majorité ;
- changement de tuteur et historique des affectations ;
- pièces jointes dans la messagerie ;
- rendez-vous récurrents, rappels, fuseaux horaires et visioconférence ;
- échéance, priorité, statut et historique des tâches terminées ;
- recherche ;
- notifications par courriel, à l’exception du courriel nécessaire à la récupération du mot de passe ;
- exigences d’accessibilité spécifiques au-delà des bonnes pratiques générales d’interface.

## Objectifs de réussite

- permettre un parcours autonome sans intervention administrative ;
- garantir l’isolation des données entre accompagnements ;
- proposer une expérience lisible sur mobile, tablette et ordinateur ;
- conserver une architecture simple, maintenable et cohérente avec le périmètre.
