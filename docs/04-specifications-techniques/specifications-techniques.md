# HomeSkolar — Spécifications techniques

## 1. Objet et entrées

Les présentes spécifications décrivent comment la solution répond aux besoins validés : comptes, communication, rencontres et calendrier, tâches et notifications internes. Elles s’appuient sur les spécifications fonctionnelles, les 14 User Stories fonctionnelles validées, la veille technologique et les consignes du projet.

Contraintes confirmées : application web Python, équipe de quatre développeurs compétents, absence de formation à prévoir, cahier des charges destiné à une autre équipe de maintenance. L’hébergeur et l’outil de déploiement restent hors périmètre.

## 2. Architecture générale

HomeSkolar utilisera une **architecture web monolithique modulaire**. Un seul projet Django assurera le rendu des pages, les règles métier, l’authentification et la persistance. Les domaines fonctionnels seront séparés en applications Django afin d’éviter un monolithe non structuré.

### Couches

1. **Présentation** : gabarits Django, composants Bootstrap et JavaScript limité aux interactions utiles.
2. **Application et métier** : vues, formulaires, services métier et règles d’autorisation.
3. **Persistance** : modèles Django, ORM, contraintes et transactions PostgreSQL.

Cette organisation réduit les échanges réseau internes et la duplication, tout en permettant de tester et faire évoluer chaque domaine séparément.

## 3. Pile technique et environnement

| Technologie | Version de référence | Rôle et justification |
| --- | --- | --- |
| Python | 3.13 | Version moderne prise en charge par Django 5.2 ; typage et écosystème adaptés à l’équipe |
| Django | série 5.2 LTS | Authentification, sessions, formulaires, ORM, vues et gabarits intégrés ; support de sécurité prolongé |
| Bootstrap | série 5.3 | Grille responsive et composants accessibles sans application front-end séparée |
| PostgreSQL | 17 | Base relationnelle transactionnelle, mature et compatible avec Django 5.2 |
| HTML5/CSS3 | standards actuels | Structure et présentation des interfaces |
| JavaScript | natif, usage ponctuel | Interactions du calendrier et améliorations non bloquantes |

Les versions correctives les plus récentes des séries retenues seront verrouillées dans le fichier de dépendances au démarrage du développement. SQLite pourra être utilisé uniquement pour des essais locaux simples ; les tests d’intégration devront utiliser PostgreSQL afin d’éviter les écarts de comportement.

## 4. Organisation modulaire

| Module | Responsabilités principales |
| --- | --- |
| `accounts` | inscription, connexion, mot de passe, profil et rôles élève/tuteur |
| `relationships` | association entre l’élève et le tuteur, sans définir le processus d’affectation non précisé |
| `messaging` | conversations, messages, lecture et épinglage par l’élève |
| `calendar` | rencontres et événements affichés dans la vue calendrier |
| `tasks` | tâches de suivi et éléments personnels de type tâche, note ou mémo |
| `notifications` | notifications internes de messages non lus et de tâches |
| `core` | composants partagés, navigation, contrôles transverses et page d’accueil authentifiée |

## 5. Front-end et expérience utilisateur

Les pages seront rendues côté serveur avec les gabarits Django. Un gabarit de base définira l’en-tête, la navigation, les messages de retour et la zone de contenu. Les composants de formulaire réutiliseront une présentation homogène.

Principes :

* fonctionnement sur mobile, tablette et ordinateur grâce à la grille Bootstrap ;
* navigation au clavier et libellés explicites pour les champs ;
* messages d’erreur placés à proximité des données concernées ;
* conservation des données valides après erreur de formulaire ;
* indicateurs non lus compréhensibles sans dépendre uniquement de la couleur ;
* calendrier utilisable sans masquer l’accès à une liste textuelle des éléments ;
* JavaScript non indispensable aux fonctions critiques d’inscription, connexion, messagerie et tâches.

## 6. Back-end et règles métier

### Comptes

Django Auth fournira le stockage sécurisé du mot de passe, les sessions et les mécanismes d’authentification. Un modèle utilisateur personnalisé sera défini dès la première migration afin de porter un rôle `ELEVE` ou `TUTEUR` sans modifier ultérieurement le modèle natif.

Les modifications de mot de passe exigeront le mot de passe courant pour un utilisateur connecté. Les règles de récupération d’un mot de passe oublié restent à confirmer avec le client.

### Relation élève–tuteur

Une relation explicite associera un élève à son tuteur. Les modules de communication, rencontres et suivi vérifieront cette relation avant toute consultation ou modification. Le processus d’affectation n’étant pas décrit, il ne sera pas automatisé dans ces spécifications.

### Communication

Une conversation reliera les deux membres d’une relation. Chaque message stockera son auteur, son contenu, sa date de création et les informations permettant de déterminer sa lecture. L’épinglage sera une propriété personnelle de l’élève et ne modifiera ni le message ni sa visibilité pour le tuteur.

### Rencontres et calendrier

Une rencontre reliera l’élève et le tuteur avec une date de début et une date de fin. La validation interdira une fin antérieure ou égale au début. Les rendez-vous et événements autorisés seront convertis en données de calendrier puis rendus dans la page dédiée. La récurrence, l’annulation et les rappels restent à confirmer.

### Tâches

Le modèle distinguera :

* une tâche de suivi visible dans la relation élève–tuteur et destinée à l’élève ;
* un élément personnel visible uniquement par son propriétaire, pouvant servir de tâche, note ou mémo.

La personne autorisée à créer une tâche de suivi devra être confirmée. En attendant, aucune règle plus large que le besoin client n’est imposée.

### Notifications internes

Les notifications signaleront les messages non lus et les tâches portées à l’attention de l’élève. Elles contiendront un type, un destinataire, une référence vers l’objet concerné, une date et un état lu/non lu. Aucun courriel, SMS ou notification push n’est inclus.

## 7. Persistance et données

PostgreSQL assurera l’intégrité relationnelle. Les clés étrangères protégeront les associations entre utilisateur, relation, conversation, message, rencontre, tâche et notification. Les suppressions seront définies explicitement pour éviter la disparition en cascade de données métier sans contrôle.

Règles principales :

* adresse de connexion unique si elle est retenue comme identifiant ;
* un utilisateur possède un seul rôle métier actif ;
* seuls les membres d’une relation peuvent accéder à ses messages et rencontres ;
* un élément personnel possède exactement un propriétaire ;
* une notification possède exactement un destinataire ;
* les dates sont stockées avec information de fuseau horaire et présentées dans le fuseau configuré par l’application.

Les migrations Django seront versionnées avec le code. Les données sensibles ne seront jamais placées dans les migrations, fixtures publiques ou journaux.

## 8. Authentification, autorisations et protection des données

* mots de passe gérés exclusivement par les mécanismes de hachage et validation de Django ;
* protection CSRF activée sur tous les formulaires modifiant des données ;
* cookies de session `HttpOnly`, `Secure` en environnement HTTPS et politique `SameSite` adaptée ;
* contrôle d’autorisation côté serveur pour chaque objet, même si l’interface masque l’action ;
* validation et échappement des contenus utilisateur pour limiter injections et scripts malveillants ;
* secrets et paramètres sensibles fournis par l’environnement, jamais inscrits dans GitHub ;
* collecte limitée aux données nécessaires ;
* journalisation sans mot de passe, jeton de session ni contenu privé de message.

## 9. Interfaces et flux

L’interface principale est HTTP entre le navigateur et Django. Les formulaires HTML transmettent les commandes. Les réponses renvoient une page ou une redirection après succès afin d’éviter la répétition d’une soumission.

Flux d’envoi d’un message : navigateur → contrôle de session → contrôle de la relation → validation du contenu → transaction PostgreSQL → création de l’état non lu/notification → redirection vers la conversation.

Flux de création d’une rencontre : navigateur → contrôle de session et de relation → validation des dates → enregistrement transactionnel → affichage dans les calendriers concernés.

Flux de consultation des tâches : navigateur → contrôle de session → filtrage par destinataire, relation ou propriétaire → rendu de la liste autorisée.

Aucune API publique ni intégration externe n’est requise dans le périmètre actuel.

## 10. Exigences non fonctionnelles

| Domaine | Exigence vérifiable proposée |
| --- | --- |
| Accessibilité | parcours critiques réalisables au clavier, champs libellés et erreurs associées |
| Compatibilité | deux dernières versions stables des principaux navigateurs de bureau et mobiles au moment du développement |
| Performance | pages courantes rendues sans requêtes répétitives évitables ; listes paginées lorsque leur volume le nécessite |
| Sécurité | aucune action métier accessible sans authentification et contrôle d’objet approprié |
| Maintenabilité | modules séparés, conventions PEP 8, typage des interfaces métier utiles et documentation des décisions |
| Qualité | tests automatisés des parcours critiques et des règles d’autorisation |
| Résilience | une erreur métier affiche un retour compréhensible sans exposer de détail interne |

Les objectifs chiffrés de charge, disponibilité et temps de réponse nécessitent une volumétrie client ; ils ne doivent pas être inventés.

## 11. Gestion des erreurs et journalisation

Les erreurs de validation seront renvoyées au formulaire. Les accès interdits produiront une réponse 403 ou une redirection vers la connexion selon le contexte. Les objets absents produiront une réponse 404 sans révéler l’existence d’une ressource non autorisée. Les erreurs inattendues seront journalisées avec un identifiant de corrélation et présenteront à l’utilisateur un message générique.

Niveaux recommandés : `INFO` pour les événements techniques non sensibles, `WARNING` pour les actions refusées ou situations anormales prévues, `ERROR` pour les échecs inattendus. Le contenu des messages et les données personnelles ne seront pas enregistrés par défaut.

## 12. Stratégie de tests

* tests unitaires des validations et règles métier ;
* tests d’intégration ORM avec PostgreSQL ;
* tests des autorisations entre élève, tuteur et utilisateur extérieur à la relation ;
* tests des formulaires d’inscription, connexion, profil et mot de passe ;
* tests des scénarios de messagerie, calendrier, tâches et notifications ;
* tests fonctionnels des parcours critiques à partir des critères Gherkin ;
* contrôle responsive, clavier et lisibilité des erreurs ;
* analyse statique, formatage et vérification des dépendances dans l’intégration continue.

## 13. Matrice de traçabilité

| Besoin / User Stories | Réponse technique | Modules | Vérification principale |
| --- | --- | --- | --- |
| US-CPT-01 à 04 | Auth Django, modèle utilisateur personnalisé, formulaires et sessions | `accounts` | tests comptes et autorisations |
| US-COM-01 à 04 | conversation, message, lecture, épinglage et notification interne | `messaging`, `notifications`, `relationships` | tests d’accès, envoi, lecture et épinglage |
| US-CAL-01 à 02 | rencontre, événement et vue calendrier | `calendar`, `relationships` | tests des dates, visibilité et rendu |
| US-TAC-01 à 04 | tâche de suivi, élément personnel et notification | `tasks`, `notifications`, `relationships` | tests de visibilité et propriété |

## 14. Questions et décisions reportées

Les points suivants doivent être arbitrés avec le mentor/client : création et validation des comptes, processus d’affectation, cardinalité élève–tuteur, auteur des tâches de suivi, définition des événements, récurrence et modification des rencontres, données personnelles obligatoires, récupération du mot de passe et volumétrie attendue.

Toute réponse modifiant le périmètre entraînera une mise à jour coordonnée des User Stories, des présentes spécifications, du futur diagramme UML et du Backlog Produit.

## 15. Validation

La solution répond aux quatre domaines fonctionnels avec une architecture proportionnée. Les technologies proviennent de la veille, les modules et flux sont identifiés, la sécurité et les tests sont intégrés, et les hypothèses non confirmées sont isolées. Le document est prêt à être intégré au cahier des charges et à servir d’entrée au diagramme de classes.
