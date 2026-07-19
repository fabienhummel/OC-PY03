# Spécifications fonctionnelles

## 1. Gestion des comptes

- l’inscription est libre et ne nécessite aucune validation ;
- l’utilisateur choisit le rôle élève ou tuteur à l’inscription ;
- les seuls rôles autorisés sont élève et tuteur ;
- les données minimales sont le nom d’utilisateur, l’adresse électronique, le mot de passe, le nom et le prénom ;
- l’utilisateur peut se connecter, se déconnecter et modifier ses informations personnelles ;
- l’utilisateur peut changer son mot de passe lorsqu’il est connecté ;
- l’utilisateur peut demander un lien de réinitialisation par courriel ;
- la suppression du compte entraîne la suppression des données personnelles associées selon les règles d’intégrité définies par l’application.

## 2. Affectation élève–tuteur

- un élève est associé à zéro ou un tuteur ;
- un tuteur peut être associé à plusieurs élèves ;
- l’application choisit aléatoirement un tuteur existant lors de l’affectation ;
- lorsqu’aucun tuteur n’est disponible, l’élève reste temporairement sans affectation et en est informé ;
- le changement de tuteur et l’historique des affectations ne sont pas gérés.

## 3. Communication

- une conversation est accessible uniquement à l’élève et à son tuteur attitré ;
- les messages texte sont affichés de manière quasi instantanée sans rechargement complet de la page ;
- les pièces jointes ne sont pas autorisées ;
- un participant peut épingler ou désépingler un message ;
- les messages épinglés apparaissent en tête de la liste de la conversation ;
- la présence de messages non lus est signalée dans l’interface ;
- aucune notification de nouveau message n’est envoyée par courriel.

## 4. Rendez-vous

- seul le tuteur peut créer, modifier ou annuler un rendez-vous ;
- l’élève consulte les rendez-vous créés pour son accompagnement ;
- aucune acceptation de l’élève n’est requise ;
- un rendez-vous comporte au minimum un titre, une date, une heure de début, une heure de fin et les participants ;
- la récurrence, les rappels, les fuseaux horaires et la visioconférence ne sont pas gérés.

## 5. Tâches, notes et mémos

- un seul objet métier représente une tâche, une note ou un mémo ;
- le tuteur peut créer un élément pour lui-même ou attribuer une tâche à l’élève ;
- l’élève peut créer un élément uniquement pour lui-même ;
- une tâche attribuée par le tuteur est visible par l’élève mais non modifiable par celui-ci ;
- une note ou un mémo personnel est strictement privé ;
- aucune échéance, priorité, statut ou conservation d’un historique de fin n’est prévue.

## 6. Exigences transverses

- l’interface est responsive sur mobile, tablette et ordinateur ;
- les contrôles d’autorisation sont appliqués côté serveur ;
- les erreurs et confirmations sont présentées dans l’interface ;
- aucune fonction de recherche n’est proposée ;
- les notifications restent internes à l’application ;
- les mots de passe ne sont jamais stockés en clair.

## 7. Règles de cohérence

- un élève ne peut accéder qu’aux données de son propre accompagnement ;
- un tuteur ne peut accéder qu’aux données de ses élèves ;
- la suppression d’une ressource est confirmée avant exécution ;
- les fonctionnalités absentes du périmètre ne doivent pas apparaître comme actions disponibles dans l’interface.
