# Kanban du Backlog Produit

Ce tableau présente l’état initial du Backlog Produit HomeSkolar. Il sert de support public de planification et doit être actualisé au fil de la réalisation.

La priorité indique la valeur métier. Les dépendances précisent les prérequis techniques ou fonctionnels à terminer avant de commencer une User Story.

## À faire

| Ordre | ID | User Story | Priorité | Estimation | Dépendances |
|---:|---|---|:---:|---:|---|
| 1 | US-CPT-01 | Créer librement un compte élève ou tuteur | P0 | 1,5 j | Aucune |
| 2 | US-CPT-02 | Se connecter et se déconnecter | P0 | 1 j | US-CPT-01 |
| 3 | US-CPT-05 | Réinitialiser son mot de passe par courriel | P0 | 1,5 j | US-CPT-01 |
| 4 | US-CPT-06 | Supprimer son compte et ses données | P0 | 1,5 j | US-CPT-02 |
| 5 | US-AFF-01 | Affecter aléatoirement un tuteur à un élève | P0 | 2 j | US-CPT-01 |
| 6 | US-COM-01 | Échanger des messages avec son binôme | P0 | 2 j | US-CPT-02, US-AFF-01 |
| 7 | US-COM-02 | Voir les messages non lus et la notification interne | P0 | 1,5 j | US-COM-01 |
| 8 | US-RDV-01 | Créer un rendez-vous pour un élève | P0 | 1,5 j | US-CPT-02, US-AFF-01 |
| 9 | US-RDV-02 | Consulter ses rendez-vous | P0 | 1,5 j | US-RDV-01 |
| 10 | US-RDV-03 | Modifier ou annuler un rendez-vous | P0 | 1,5 j | US-RDV-01 |
| 11 | US-TAC-01 | Attribuer une tâche de suivi à un élève | P0 | 1,5 j | US-CPT-02, US-AFF-01 |
| 12 | US-TAC-02 | Consulter une tâche attribuée | P0 | 1 j | US-TAC-01 |
| 13 | US-CPT-03 | Modifier son profil | P1 | 1 j | US-CPT-02 |
| 14 | US-CPT-04 | Changer son mot de passe | P1 | 1 j | US-CPT-02 |
| 15 | US-COM-03 | Épingler un message en tête de conversation | P1 | 1 j | US-COM-01 |
| 16 | US-TAC-03 | Créer une tâche, note ou mémo personnel | P1 | 1,5 j | US-CPT-02 |
| 17 | US-TAC-04 | Modifier ou supprimer un élément personnel | P1 | 1 j | US-TAC-03 |

**Charge initiale estimée : 23,5 jours idéaux.**

## En cours

Aucune User Story : la réalisation n’a pas encore commencé.

## Terminé

Aucune User Story : les éléments seront déplacés ici après vérification de tous leurs critères d’acceptation.

## Règles de mise à jour

- une User Story passe dans « En cours » lorsque sa réalisation commence et que ses dépendances sont terminées ;
- elle passe dans « Terminé » lorsque tous ses critères d’acceptation ont été vérifiés ;
- la priorité ne dispense pas de respecter les dépendances ;
- toute modification du périmètre est validée avant l’ajout, le retrait ou la réestimation d’une User Story.

Les critères détaillés sont disponibles dans le [Backlog Produit](backlog-produit.md).
