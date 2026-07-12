# HomeSkolar — User Stories fonctionnelles

## 1. Périmètre et conventions

Ce document constitue la première partie du Backlog Produit. Il décrit uniquement les comportements attendus par les deux acteurs explicitement cités par HomeSkolar : **l’élève** et **le tuteur bénévole**. Les choix techniques, la priorisation définitive et les estimations seront ajoutés après validation des spécifications techniques et du diagramme UML.

Format d’une User Story : **En tant que [acteur], je souhaite [action] afin de [valeur].**

Format des critères : **Étant donné / Lorsque / Alors.**

Identifiants : `US-CPT` pour le compte, `US-COM` pour la communication, `US-CAL` pour les rencontres et le calendrier, `US-TAC` pour les tâches.

## 2. Acteurs et parcours

### Élève

1. créer et gérer son compte ;
2. communiquer avec son tuteur ;
3. retrouver les messages importants et identifier les messages non lus ;
4. planifier et consulter ses rencontres ;
5. consulter les tâches à réaliser avant la rencontre suivante ;
6. créer une tâche personnelle, une note ou un mémo.

### Tuteur bénévole

1. créer et gérer son compte ;
2. communiquer avec l’élève qui lui est assigné ;
3. identifier les messages non lus ;
4. planifier et consulter les rencontres ;
5. consulter les tâches de suivi de l’élève ;
6. créer une tâche personnelle, une note ou un mémo.

## 3. User Stories et critères d’acceptation

### Epic A — Gestion du compte

#### US-CPT-01 — Inscription

**En tant qu’élève ou tuteur bénévole, je souhaite m’inscrire afin d’accéder aux fonctions de HomeSkolar.**

* Étant donné que je ne possède pas de compte, lorsque je fournis les informations obligatoires valides, alors mon compte est créé et je peux poursuivre vers la connexion.
* Étant donné qu’une information obligatoire est absente ou invalide, lorsque je soumets le formulaire, alors le compte n’est pas créé et les erreurs sont indiquées.

#### US-CPT-02 — Connexion

**En tant qu’élève ou tuteur bénévole, je souhaite me connecter afin d’accéder à mon espace personnel.**

* Étant donné un compte existant, lorsque je fournis des identifiants valides, alors j’accède à mon espace personnel.
* Étant donné des identifiants invalides, lorsque je tente de me connecter, alors l’accès est refusé sans révéler quelle donnée est incorrecte.

#### US-CPT-03 — Gestion du mot de passe

**En tant qu’élève ou tuteur bénévole, je souhaite gérer mon mot de passe afin de conserver l’accès sécurisé à mon compte.**

* Étant donné que je suis connecté, lorsque je fournis mon mot de passe actuel et un nouveau mot de passe valide, alors le mot de passe est remplacé.
* Étant donné que le mot de passe actuel est incorrect ou que le nouveau mot de passe ne respecte pas les règles, lorsque je valide, alors aucune modification n’est effectuée et une explication est affichée.

#### US-CPT-04 — Données personnelles

**En tant qu’élève ou tuteur bénévole, je souhaite consulter et modifier mes données personnelles afin de maintenir mon profil à jour.**

* Étant donné que je suis connecté, lorsque j’ouvre mon profil, alors seules mes données personnelles modifiables sont affichées.
* Étant donné des données valides, lorsque je confirme mes modifications, alors elles sont enregistrées et visibles dans mon profil.

### Epic B — Communication

#### US-COM-01 — Envoyer un message

**En tant qu’élève ou tuteur bénévole, je souhaite envoyer un message à mon interlocuteur afin de communiquer à distance.**

* Étant donné que je suis connecté et associé à mon interlocuteur, lorsque j’envoie un message non vide, alors il apparaît dans leur conversation.
* Étant donné un message vide, lorsque je tente de l’envoyer, alors aucun message n’est créé.

#### US-COM-02 — Consulter les messages

**En tant qu’élève ou tuteur bénévole, je souhaite consulter les messages échangés afin de suivre la conversation.**

* Étant donné une conversation existante, lorsque je l’ouvre, alors les messages sont présentés dans l’ordre chronologique avec leur auteur et leur date.
* Étant donné un message reçu non lu, lorsque je l’affiche, alors il est considéré comme lu pour mon compte.

#### US-COM-03 — Épingler un message

**En tant qu’élève, je souhaite épingler ou désépingler un message afin de retrouver facilement une information importante.**

* Étant donné un message de ma conversation, lorsque je l’épingle, alors il apparaît parmi mes messages épinglés.
* Étant donné un message déjà épinglé, lorsque je le désépingle, alors il n’apparaît plus parmi mes messages épinglés sans être supprimé de la conversation.

#### US-COM-04 — Messages non lus

**En tant qu’élève ou tuteur bénévole, je souhaite être informé de mes messages non lus afin d’identifier les échanges nécessitant mon attention.**

* Étant donné qu’un nouveau message m’est adressé, lorsque je consulte l’application, alors une notification interne signale qu’un message reste non lu.
* Étant donné que tous mes messages ont été lus, lorsque je consulte l’indicateur, alors aucun message non lu n’est signalé.

### Epic C — Rencontres et calendrier

#### US-CAL-01 — Planifier une rencontre

**En tant qu’élève ou tuteur bénévole, je souhaite planifier une rencontre avec mon interlocuteur afin d’organiser le suivi scolaire.**

* Étant donné que je suis connecté et associé à mon interlocuteur, lorsque je renseigne une date et des horaires valides, alors la rencontre est enregistrée et visible dans le calendrier des deux personnes.
* Étant donné des horaires incohérents, lorsque je tente d’enregistrer la rencontre, alors elle n’est pas créée et l’erreur est indiquée.

#### US-CAL-02 — Consulter le calendrier

**En tant qu’élève ou tuteur bénévole, je souhaite consulter mes rendez-vous et événements dans une vue calendrier afin d’organiser mes rencontres.**

* Étant donné des rendez-vous ou événements enregistrés, lorsque j’ouvre le calendrier, alors ils sont affichés aux dates correspondantes.
* Étant donné un élément du calendrier, lorsque je le sélectionne, alors ses informations utiles sont consultables.

### Epic D — Gestion des tâches

#### US-TAC-01 — Consulter les tâches de suivi

**En tant qu’élève, je souhaite consulter les tâches à réaliser avant la prochaine rencontre afin d’organiser mon travail.**

* Étant donné des tâches associées à mon suivi, lorsque j’ouvre ma liste, alors je vois les tâches à réaliser avant la rencontre suivante.
* Étant donné qu’aucune tâche de suivi n’est enregistrée, lorsque j’ouvre la liste, alors l’application indique qu’aucune tâche n’est disponible.

#### US-TAC-02 — Notification des tâches

**En tant qu’élève, je souhaite être informé des tâches qui me sont destinées afin de ne pas oublier le travail prévu.**

* Étant donné une tâche de suivi portée à mon attention, lorsque je consulte l’application, alors une notification interne me permet d’accéder à cette tâche.

#### US-TAC-03 — Tâche personnelle de l’élève

**En tant qu’élève, je souhaite créer une tâche personnelle, une note ou un mémo afin d’organiser mon propre travail.**

* Étant donné que je suis connecté, lorsque je saisis un contenu valide et confirme, alors l’élément personnel est enregistré dans ma liste.
* Étant donné une tâche personnelle, lorsque mon tuteur consulte ses propres éléments, alors il ne peut pas accéder à cet élément personnel.

#### US-TAC-04 — Tâche personnelle du tuteur

**En tant que tuteur bénévole, je souhaite créer une tâche personnelle, une note ou un mémo afin d’organiser mon suivi.**

* Étant donné que je suis connecté, lorsque je saisis un contenu valide et confirme, alors l’élément personnel est enregistré dans ma liste.
* Étant donné une tâche personnelle, lorsque l’élève consulte ses propres éléments, alors il ne peut pas accéder à cet élément personnel.

## 4. Contrôle de maturité

| Critère | Résultat |
| --- | --- |
| Valeur utilisateur identifiable | Conforme pour les 14 User Stories |
| Acteur explicite | Conforme |
| Absence de choix d’implémentation | Conforme |
| Critères observables et testables | Conforme |
| Taille compatible avec un développement incrémental | Conforme, à confirmer lors de l’estimation |
| Couverture des spécifications fonctionnelles | Conforme |
| Fonctionnalités hors périmètre | Aucune introduite comme exigence |

## 5. Points à confirmer avant finalisation du backlog

* mode de création des comptes et éventuelle validation d’inscription ;
* règles d’assignation entre élèves et tuteurs ;
* capacité d’un tuteur à suivre plusieurs élèves ;
* personne autorisée à créer les tâches de suivi destinées à l’élève ;
* définition exacte d’un « événement » distinct d’une rencontre ;
* récurrence, modification et annulation des rencontres ;
* données personnelles obligatoires ;
* politique de récupération d’un mot de passe oublié.

Ces questions n’empêchent pas la validation fonctionnelle initiale, mais elles devront être arbitrées avant l’estimation définitive et le développement.
