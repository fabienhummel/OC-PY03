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

- **Étant donné** un visiteur. **Quand** il fournit un nom d’utilisateur, une adresse électronique, un mot de passe, un nom, un prénom et un rôle valide. **Alors** le compte est créé et il peut se connecter.
- **Étant donné** un nom d’utilisateur ou une adresse déjà utilisée. **Quand** le visiteur valide l’inscription. **Alors** la création est refusée avec un message explicite.
- **Étant donné** le formulaire d’inscription. **Quand** le visiteur choisit un rôle. **Alors** seuls les rôles élève et tuteur sont proposés et acceptés.

### US-CPT-02 — Se connecter et se déconnecter

**En tant qu’** utilisateur, **je veux** ouvrir et fermer une session **afin de** sécuriser l’accès à mon espace.

Critères d’acceptation :

- **Étant donné** un compte existant. **Quand** l’utilisateur saisit des identifiants valides. **Alors** sa session s’ouvre et son espace s’affiche.
- **Étant donné** des identifiants invalides. **Quand** l’utilisateur tente de se connecter. **Alors** aucune session ne s’ouvre et un message générique s’affiche.
- **Étant donné** une session ouverte. **Quand** l’utilisateur se déconnecte. **Alors** la session est invalidée et les pages privées deviennent inaccessibles.

### US-CPT-03 — Modifier son profil

**En tant qu’** utilisateur connecté, **je veux** modifier mon nom, mon prénom et mon adresse électronique **afin de** maintenir mes informations à jour.

Critères d’acceptation :

- **Étant donné** un utilisateur connecté sur son profil. **Quand** il enregistre des valeurs valides. **Alors** les nouvelles informations sont immédiatement visibles.
- **Étant donné** une adresse déjà utilisée ou le profil d’un autre utilisateur. **Quand** une modification est tentée. **Alors** elle est refusée.

### US-CPT-04 — Changer son mot de passe

**En tant qu’** utilisateur connecté, **je veux** changer mon mot de passe **afin de** préserver la sécurité de mon compte.

Critères d’acceptation :

- **Étant donné** un utilisateur connecté. **Quand** il fournit son mot de passe actuel et un nouveau mot de passe valide. **Alors** le mot de passe est changé.
- **Étant donné** un mot de passe actuel incorrect ou un nouveau mot de passe non conforme. **Quand** le formulaire est validé. **Alors** le changement est refusé.
- **Étant donné** un changement réussi. **Quand** l’utilisateur tente de se connecter avec l’ancien mot de passe. **Alors** l’accès est refusé.

### US-CPT-05 — Réinitialiser son mot de passe par courriel

**En tant qu’** utilisateur ayant oublié son mot de passe, **je veux** recevoir un lien de réinitialisation **afin de** récupérer l’accès à mon compte.

Critères d’acceptation :

- **Étant donné** une adresse saisie. **Quand** une réinitialisation est demandée. **Alors** le même message de confirmation s’affiche que l’adresse existe ou non.
- **Étant donné** une adresse connue. **Quand** la demande est validée. **Alors** un lien unique et limité dans le temps est envoyé.
- **Étant donné** un lien expiré ou déjà utilisé. **Quand** l’utilisateur l’ouvre. **Alors** la réinitialisation est refusée.

### US-CPT-06 — Supprimer son compte et ses données

**En tant qu’** utilisateur connecté, **je veux** supprimer mon compte **afin de** retirer mes données de la plateforme.

Critères d’acceptation :

- **Étant donné** un utilisateur connecté. **Quand** il demande la suppression sans la confirmer. **Alors** le compte est conservé.
- **Étant donné** une suppression confirmée. **Quand** l’opération se termine. **Alors** le compte, ses données personnelles et ses relations associées sont supprimés et la connexion devient impossible.

## Affectation

### US-AFF-01 — Affecter aléatoirement un tuteur à un élève

**En tant qu’** élève, **je veux** être associé automatiquement à un tuteur **afin de** commencer mon accompagnement sans intervention administrative.

Critères d’acceptation :

- **Étant donné** au moins un tuteur actif. **Quand** un élève demande une affectation. **Alors** un seul tuteur est choisi aléatoirement et la relation est visible par les deux personnes concernées.
- **Étant donné** qu’un tuteur suit déjà un élève. **Quand** une autre affectation le sélectionne. **Alors** il peut suivre ce nouvel élève également.
- **Étant donné** qu’aucun tuteur n’existe. **Quand** l’élève demande une affectation. **Alors** aucune relation n’est créée et l’élève en est informé.

## Communication

### US-COM-01 — Échanger des messages avec son binôme

**En tant qu’** élève ou tuteur, **je veux** envoyer et recevoir des messages texte **afin de** communiquer dans le cadre de l’accompagnement.

Critères d’acceptation :

- **Étant donné** un élève et son tuteur attitré. **Quand** l’un ouvre la conversation. **Alors** il voit les messages avec leur auteur et leur date.
- **Étant donné** la conversation ouverte. **Quand** un participant envoie un message texte non vide. **Alors** il apparaît sans rechargement complet de la page.
- **Étant donné** un utilisateur extérieur ou une tentative d’ajout de pièce jointe. **Quand** l’action est demandée. **Alors** elle est refusée.

### US-COM-02 — Voir les messages non lus et la notification interne

**En tant qu’** utilisateur, **je veux** identifier les nouveaux messages **afin de** savoir qu’une réponse m’attend.

Critères d’acceptation :

- **Étant donné** un nouveau message reçu. **Quand** le destinataire n’a pas ouvert la conversation. **Alors** le message reste non lu et un indicateur interne s’affiche sans envoi de courriel.
- **Étant donné** des messages non lus. **Quand** le destinataire ouvre la conversation. **Alors** les messages affichés sont marqués comme lus et l’indicateur est mis à jour.

### US-COM-03 — Épingler un message en tête de conversation

**En tant que** participant, **je veux** épingler un message **afin de** conserver une information importante en tête de la liste.

Critères d’acceptation :

- **Étant donné** un message de sa conversation. **Quand** un participant l’épingle ou le désépingle. **Alors** son état est modifié et les messages épinglés apparaissent en premier.
- **Étant donné** un utilisateur extérieur à la conversation. **Quand** il tente de modifier l’épinglage. **Alors** l’action est refusée.

## Rendez-vous

### US-RDV-01 — Créer un rendez-vous pour un élève

**En tant que** tuteur, **je veux** créer un rendez-vous **afin de** planifier un échange avec un élève suivi.

Critères d’acceptation :

- **Étant donné** un tuteur connecté et l’un de ses élèves. **Quand** il saisit un titre, une date et des horaires cohérents. **Alors** le rendez-vous est créé et immédiatement visible par les deux participants.
- **Étant donné** un autre utilisateur, un élève non suivi ou des horaires invalides. **Quand** la création est demandée. **Alors** elle est refusée.

### US-RDV-02 — Consulter ses rendez-vous

**En tant qu’** élève ou tuteur, **je veux** consulter mes rendez-vous **afin de** connaître les rencontres planifiées.

Critères d’acceptation :

- **Étant donné** un élève connecté. **Quand** il consulte le calendrier. **Alors** seuls ses rendez-vous s’affichent avec le titre, la date, les heures et le tuteur.
- **Étant donné** un tuteur connecté. **Quand** il consulte le calendrier. **Alors** seuls les rendez-vous de ses élèves s’affichent avec les mêmes informations.

### US-RDV-03 — Modifier ou annuler un rendez-vous

**En tant que** tuteur, **je veux** modifier ou annuler un rendez-vous **afin de** maintenir le planning à jour.

Critères d’acceptation :

- **Étant donné** un rendez-vous existant. **Quand** son tuteur propriétaire le modifie. **Alors** les changements sont immédiatement visibles par l’élève.
- **Étant donné** un rendez-vous existant. **Quand** son tuteur confirme l’annulation. **Alors** il disparaît des vues actives.
- **Étant donné** un autre utilisateur ou une demande de répétition. **Quand** l’action est tentée. **Alors** elle n’est pas proposée ou est refusée.

## Tâches, notes et mémos

### US-TAC-01 — Attribuer une tâche de suivi à un élève

**En tant que** tuteur, **je veux** attribuer une tâche à un élève suivi **afin de** formaliser une action d’accompagnement.

Critères d’acceptation :

- **Étant donné** un tuteur et l’un de ses élèves. **Quand** le tuteur attribue une tâche. **Alors** elle est visible par les deux et ne comporte ni échéance, ni priorité, ni statut.
- **Étant donné** une tâche attribuée. **Quand** l’élève tente de la modifier ou de la supprimer. **Alors** l’action est refusée.

### US-TAC-02 — Consulter une tâche attribuée

**En tant qu’** élève, **je veux** consulter les tâches attribuées par mon tuteur **afin de** connaître les actions attendues.

Critères d’acceptation :

- **Étant donné** un élève connecté. **Quand** il consulte ses tâches. **Alors** seules celles qui lui sont attribuées s’affichent avec leur contenu et leur auteur.
- **Étant donné** une tâche attribuée affichée à l’élève. **Quand** il la consulte. **Alors** aucune commande de modification n’est proposée.

### US-TAC-03 — Créer une tâche, note ou mémo personnel

**En tant qu’** utilisateur, **je veux** créer un élément personnel **afin de** conserver une tâche, une note ou un mémo privé.

Critères d’acceptation :

- **Étant donné** un utilisateur connecté. **Quand** il crée une tâche, une note ou un mémo personnel avec le formulaire commun. **Alors** un `ElementSuivi` privé sans destinataire est créé.
- **Étant donné** un élément personnel. **Quand** un autre utilisateur consulte ses éléments. **Alors** cet élément ne lui est pas visible.

### US-TAC-04 — Modifier ou supprimer un élément personnel

**En tant que** propriétaire d’un élément personnel, **je veux** le modifier ou le supprimer **afin de** gérer mes informations privées.

Critères d’acceptation :

- **Étant donné** un élément personnel. **Quand** son propriétaire le modifie. **Alors** les nouvelles valeurs sont enregistrées.
- **Étant donné** un élément personnel. **Quand** son propriétaire confirme sa suppression. **Alors** il est supprimé sans historique.
- **Étant donné** un utilisateur non propriétaire. **Quand** il tente de modifier ou supprimer l’élément. **Alors** l’action est refusée.

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
