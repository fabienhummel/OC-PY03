# Spécifications techniques

## 1. Architecture

HomeSkolar adopte une architecture monolithique Django :

- Django 5.2 LTS pour les règles métier, l’authentification, les formulaires et l’accès aux données ;
- gabarits Django pour le rendu HTML côté serveur ;
- Bootstrap 5.3 pour l’interface responsive ;
- PostgreSQL pour la persistance ;
- JavaScript limité aux interactions nécessitant une mise à jour asynchrone, notamment la messagerie.

Le navigateur communique directement avec les vues Django. Aucune API REST publique ni application front-end distincte n’est prévue.

## 2. Découpage applicatif proposé

| Module Django | Responsabilités |
|---|---|
| `accounts` | inscription, authentification, profil, mot de passe et suppression du compte |
| `assignments` | affectation aléatoire entre élèves et tuteurs |
| `messaging` | conversations, messages, lecture et épinglage |
| `appointments` | rendez-vous et consultation du calendrier |
| `tasks` | tâches attribuées, notes et mémos personnels |

## 3. Modèle de données

Le modèle métier de référence est le [diagramme de classes validé](../06-modelisation-uml/README.md).

Principes structurants :

- un utilisateur étend le modèle d’authentification Django et porte un rôle contrôlé élève ou tuteur ;
- l’adresse électronique est obligatoire et unique pour permettre la récupération du mot de passe ;
- l’affectation relie un élève à un tuteur sans gérer d’historique ;
- une conversation correspond à un accompagnement élève–tuteur ;
- les messages conservent leur auteur, leur date, leur état de lecture et leur état d’épinglage ;
- les rendez-vous appartiennent au tuteur et concernent un élève ;
- un élément de suivi représente indifféremment une tâche, une note ou un mémo, avec une visibilité déterminée par son créateur et son destinataire.

## 4. Affectation aléatoire

L’affectation est exécutée dans une transaction afin d’éviter les incohérences. L’application sélectionne aléatoirement un tuteur actif parmi les comptes existants. Si aucun tuteur n’est disponible, aucune relation n’est créée et l’élève reçoit une information claire ; une nouvelle tentative peut être déclenchée ultérieurement.

## 5. Messagerie

La page de conversation utilise des requêtes asynchrones vers des vues Django internes pour envoyer et récupérer les nouveaux messages. Ces vues appliquent les mêmes contrôles d’authentification et d’autorisation que les pages HTML. Elles ne constituent pas une API publique.

Les messages épinglés sont ordonnés avant les autres messages. L’indicateur non lu est calculé à partir de l’état de lecture des messages destinés à l’utilisateur connecté.

## 6. Sécurité et confidentialité

- hachage des mots de passe par les mécanismes Django ;
- protection CSRF sur les formulaires et requêtes mutatives ;
- contrôle d’autorisation côté serveur sur chaque ressource ;
- validation et nettoyage des données saisies ;
- cookies de session sécurisés en production ;
- secrets et paramètres sensibles fournis par variables d’environnement ;
- messages d’erreur ne révélant pas l’existence d’un compte lors de la récupération du mot de passe ;
- suppression du compte et de ses données personnelles selon des règles de cascade explicites et testées.

## 7. Interface et accessibilité générale

- mise en page responsive Bootstrap ;
- formulaires utilisables au clavier et correctement étiquetés ;
- contrastes, titres et messages d’erreur lisibles ;
- absence d’action inaccessible uniquement par la couleur ou une icône ;
- tests manuels sur formats mobile, tablette et ordinateur.

## 8. Qualité et tests

Chaque User Story comprend au minimum :

- tests unitaires des règles métier ;
- tests d’intégration des vues, formulaires et autorisations ;
- test fonctionnel des critères d’acceptation ;
- revue de code et mise à jour de la documentation concernée.

Les migrations de base de données doivent être versionnées. Les données de test ne doivent contenir aucune donnée personnelle réelle.

## 9. Configuration et déploiement

Les environnements de développement, de validation et de production utilisent une configuration séparée. Les paramètres de connexion PostgreSQL, la clé secrète, les paramètres de courrier et les hôtes autorisés sont externalisés. Une procédure de sauvegarde, de restauration et de déploiement sera détaillée avant la mise en production.
