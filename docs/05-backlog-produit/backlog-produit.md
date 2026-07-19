# Backlog produit initial

## Vue d’ensemble

| ID | User Story | Priorité | Estimation |
|---|---|---:|---:|
| US-CPT-01 | Créer librement un compte élève ou tuteur | P0 | 1,5 j |
| US-CPT-02 | Se connecter et se déconnecter | P0 | 1 j |
| US-CPT-03 | Modifier son profil | P1 | 1 j |
| US-CPT-04 | Changer son mot de passe | P1 | 1 j |
| US-CPT-05 | Réinitialiser son mot de passe par courriel | P0 | 1,5 j |
| US-CPT-06 | Supprimer son compte et ses données | P0 | 1,5 j |
| US-AFF-01 | Affecter aléatoirement un tuteur à un élève | P0 | 2 j |
| US-COM-01 | Échanger des messages avec son binôme | P0 | 2 j |
| US-COM-02 | Voir les messages non lus et la notification interne | P0 | 1,5 j |
| US-COM-03 | Épingler un message en tête de conversation | P1 | 1 j |
| US-RDV-01 | Créer un rendez-vous pour un élève | P0 | 1,5 j |
| US-RDV-02 | Consulter ses rendez-vous | P0 | 1,5 j |
| US-RDV-03 | Modifier ou annuler un rendez-vous | P0 | 1,5 j |
| US-TAC-01 | Attribuer une tâche de suivi à un élève | P0 | 1,5 j |
| US-TAC-02 | Consulter une tâche attribuée | P0 | 1 j |
| US-TAC-03 | Créer une tâche, note ou mémo personnel | P1 | 1,5 j |
| US-TAC-04 | Modifier ou supprimer un élément personnel | P1 | 1 j |

**Charge initiale estimée : 23,5 jours idéaux.**

Le suivi de la réalisation est présenté dans le [Kanban du Backlog Produit](kanban.md).

## Comptes

### US-CPT-01 — Créer librement un compte élève ou tuteur

**En tant que** visiteur, **je veux** créer un compte avec le rôle élève ou tuteur **afin de** rejoindre HomeSkolar sans validation administrative.

Critères d’acceptation :

- Étant donné un visiteur, lorsqu’il fournit un nom d’utilisateur, une adresse électronique, un mot de passe, un nom, un prénom et un rôle valide, alors le compte est créé et il peut se connecter.
- Si le nom d’utilisateur ou l’adresse électronique existe déjà, la création est refusée avec un message explicite.
- Aucun rôle autre qu’élève ou tuteur n’est proposé ni accepté.

### US-CPT-02 — Se connecter et se déconnecter

**En tant qu’** utilisateur, **je veux** ouvrir et fermer une session **afin de** sécuriser l’accès à mon espace.

Critères d’acceptation :

- Des identifiants valides ouvrent une session et redirigent vers l’espace de l’utilisateur.
- Des identifiants invalides n’ouvrent pas de session et produisent un message générique.
- La déconnexion invalide la session et rend les pages privées inaccessibles.

### US-CPT-03 — Modifier son profil

**En tant qu’** utilisateur connecté, **je veux** modifier mon nom, mon prénom et mon adresse électronique **afin de** maintenir mes informations à jour.

Critères d’acceptation :

- Seul le propriétaire peut modifier son profil.
- Une adresse électronique déjà utilisée est refusée.
- Les valeurs validées sont visibles dès l’enregistrement.

### US-CPT-04 — Changer son mot de passe

**En tant qu’** utilisateur connecté, **je veux** changer mon mot de passe **afin de** préserver la sécurité de mon compte.

Critères d’acceptation :

- Le mot de passe actuel est requis.
- Le nouveau mot de passe respecte les validateurs de sécurité configurés.
- Après le changement, l’ancien mot de passe ne permet plus de se connecter.

### US-CPT-05 — Réinitialiser son mot de passe par courriel

**En tant qu’** utilisateur ayant oublié son mot de passe, **je veux** recevoir un lien de réinitialisation **afin de** récupérer l’accès à mon compte.

Critères d’acceptation :

- Une demande produit toujours le même message de confirmation, que l’adresse existe ou non.
- Pour une adresse connue, un lien unique et limité dans le temps est envoyé.
- Un lien expiré ou déjà utilisé est refusé.

### US-CPT-06 — Supprimer son compte et ses données

**En tant qu’** utilisateur connecté, **je veux** supprimer mon compte **afin de** retirer mes données de la plateforme.

Critères d’acceptation :

- Une confirmation explicite est requise avant suppression.
- Après confirmation, le compte ne permet plus de se connecter.
- Les données personnelles et relations associées sont supprimées selon les règles de cascade documentées.

## Affectation

### US-AFF-01 — Affecter aléatoirement un tuteur à un élève

**En tant qu’** élève, **je veux** être associé automatiquement à un tuteur **afin de** commencer mon accompagnement sans intervention administrative.

Critères d’acceptation :

- Lorsqu’au moins un tuteur actif existe, un seul d’entre eux est choisi aléatoirement.
- Un tuteur peut être affecté à plusieurs élèves.
- L’affectation est visible par l’élève et le tuteur concernés seulement.
- Si aucun tuteur n’existe, aucune affectation invalide n’est créée et l’élève en est informé.

## Communication

### US-COM-01 — Échanger des messages avec son binôme

**En tant qu’** élève ou tuteur, **je veux** envoyer et recevoir des messages texte **afin de** communiquer dans le cadre de l’accompagnement.

Critères d’acceptation :

- Seuls l’élève et son tuteur attitré accèdent à la conversation.
- Un message non vide apparaît sans rechargement complet de la page.
- L’auteur et la date d’envoi sont visibles.
- Aucune pièce jointe ne peut être ajoutée.

### US-COM-02 — Voir les messages non lus et la notification interne

**En tant qu’** utilisateur, **je veux** identifier les nouveaux messages **afin de** savoir qu’une réponse m’attend.

Critères d’acceptation :

- Un nouveau message destiné à l’utilisateur est marqué non lu.
- L’interface affiche un indicateur interne tant qu’au moins un message reste non lu.
- L’ouverture de la conversation marque les messages affichés comme lus.
- Aucun courriel n’est envoyé pour cette notification.

### US-COM-03 — Épingler un message en tête de conversation

**En tant que** participant, **je veux** épingler un message **afin de** conserver une information importante en tête de la liste.

Critères d’acceptation :

- Un participant peut épingler et désépingler un message de sa conversation.
- Les messages épinglés sont affichés avant les autres.
- Aucun utilisateur extérieur à la conversation ne peut modifier cet état.

## Rendez-vous

### US-RDV-01 — Créer un rendez-vous pour un élève

**En tant que** tuteur, **je veux** créer un rendez-vous **afin de** planifier un échange avec un élève suivi.

Critères d’acceptation :

- Seul le tuteur peut créer le rendez-vous.
- L’élève choisi appartient aux élèves suivis par ce tuteur.
- Le titre, la date et les heures de début et de fin sont obligatoires et cohérents.
- Le rendez-vous est immédiatement visible par les deux participants sans acceptation de l’élève.

### US-RDV-02 — Consulter ses rendez-vous

**En tant qu’** élève ou tuteur, **je veux** consulter mes rendez-vous **afin de** connaître les rencontres planifiées.

Critères d’acceptation :

- L’élève ne voit que ses propres rendez-vous.
- Le tuteur voit uniquement les rendez-vous de ses élèves.
- Chaque entrée présente au minimum le titre, la date, les heures et l’autre participant.

### US-RDV-03 — Modifier ou annuler un rendez-vous

**En tant que** tuteur, **je veux** modifier ou annuler un rendez-vous **afin de** maintenir le planning à jour.

Critères d’acceptation :

- Seul le tuteur propriétaire peut modifier ou annuler.
- Une modification est immédiatement visible par l’élève.
- Une annulation requiert une confirmation puis retire le rendez-vous des vues actives.
- Aucune action de répétition n’est proposée.

## Tâches, notes et mémos

### US-TAC-01 — Attribuer une tâche de suivi à un élève

**En tant que** tuteur, **je veux** attribuer une tâche à un élève suivi **afin de** formaliser une action d’accompagnement.

Critères d’acceptation :

- Le destinataire appartient aux élèves suivis par le tuteur.
- La tâche est visible par le tuteur et l’élève destinataire.
- L’élève ne peut ni modifier ni supprimer une tâche attribuée par le tuteur.
- Aucune échéance, priorité ou statut n’est demandé.

### US-TAC-02 — Consulter une tâche attribuée

**En tant qu’** élève, **je veux** consulter les tâches attribuées par mon tuteur **afin de** connaître les actions attendues.

Critères d’acceptation :

- L’élève voit uniquement ses propres tâches attribuées.
- Le contenu et l’auteur sont visibles.
- Aucune commande de modification n’est proposée à l’élève.

### US-TAC-03 — Créer une tâche, note ou mémo personnel

**En tant qu’** utilisateur, **je veux** créer un élément personnel **afin de** conserver une tâche, une note ou un mémo privé.

Critères d’acceptation :

- L’élément appartient à son créateur et n’a pas d’autre destinataire.
- Il est visible uniquement par son propriétaire.
- Le même formulaire et le même objet métier couvrent les trois usages.

### US-TAC-04 — Modifier ou supprimer un élément personnel

**En tant que** propriétaire d’un élément personnel, **je veux** le modifier ou le supprimer **afin de** gérer mes informations privées.

Critères d’acceptation :

- Seul le propriétaire peut modifier ou supprimer l’élément.
- Une suppression nécessite une confirmation.
- Aucun historique des éléments supprimés ou terminés n’est conservé dans l’application.

## Dépendances explicites

| ID | Dépend de | Justification |
|---|---|---|
| US-CPT-01 | Aucune | Point d’entrée de la gestion des comptes |
| US-CPT-02 | US-CPT-01 | Un compte doit exister pour ouvrir une session |
| US-CPT-03 | US-CPT-02 | Le propriétaire doit être authentifié |
| US-CPT-04 | US-CPT-02 | Le propriétaire doit être authentifié |
| US-CPT-05 | US-CPT-01 | La récupération porte sur un compte existant |
| US-CPT-06 | US-CPT-02 | La suppression nécessite une session authentifiée |
| US-AFF-01 | US-CPT-01 | Les comptes élève et tuteur doivent être disponibles |
| US-COM-01 | US-CPT-02, US-AFF-01 | La conversation est réservée à un binôme authentifié |
| US-COM-02 | US-COM-01 | Les notifications reposent sur des messages existants |
| US-COM-03 | US-COM-01 | L’épinglage porte sur un message d’une conversation |
| US-RDV-01 | US-CPT-02, US-AFF-01 | Le tuteur authentifié planifie avec un élève suivi |
| US-RDV-02 | US-RDV-01 | La consultation suppose des rendez-vous créés |
| US-RDV-03 | US-RDV-01 | La modification et l’annulation portent sur un rendez-vous existant |
| US-TAC-01 | US-CPT-02, US-AFF-01 | Le tuteur authentifié attribue une tâche à un élève suivi |
| US-TAC-02 | US-TAC-01 | La consultation suppose une tâche attribuée |
| US-TAC-03 | US-CPT-02 | Un élément personnel appartient à un utilisateur authentifié |
| US-TAC-04 | US-TAC-03 | La modification et la suppression portent sur un élément existant |

Le graphe ne contient aucune dépendance circulaire. Une fois les comptes et l’affectation disponibles, les fonctions de communication, de rendez-vous et de tâches peuvent être réalisées en parallèle.

## Ordre de réalisation recommandé

1. comptes et authentification ;
2. affectation élève–tuteur ;
3. contrôles d’accès et socle responsive ;
4. messagerie ;
5. rendez-vous ;
6. tâches, notes et mémos ;
7. fonctions P1 et consolidation transversale.
