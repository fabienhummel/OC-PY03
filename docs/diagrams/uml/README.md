# Diagramme de classes UML — HomeSkolar

## Objectif et périmètre

Ce dossier contient le modèle UML métier unique de HomeSkolar. Il couvre les comptes, l’accompagnement élève–tuteur, la communication, les notifications internes, les rencontres et événements de calendrier, les tâches de suivi ainsi que les tâches, notes et mémos personnels.

Le fichier `.puml` est la source de vérité. Le SVG est régénéré à partir de cette source et ne doit jamais être modifié directement.

![Diagramme de classes HomeSkolar](diagramme-classes-homeskolar.svg)

## Sources analysées

- note de lancement HomeSkolar ;
- spécifications fonctionnelles validées ;
- User Stories US-CPT-01 à US-TAC-04 et critères d’acceptation ;
- spécifications techniques validées ;
- questions et clarifications conservées dans Confluence ;
- consignes OpenClassrooms relatives au diagramme de classes.

## Conventions UML

- classes en `PascalCase` ;
- attributs, paramètres et méthodes en `snake_case` ;
- visibilité privée `-` pour l’état et publique `+` pour les opérations métier ;
- types explicites et valeur de retour après `:` ;
- multiplicités placées à chaque extrémité ;
- triangle fermé vers la superclasse pour l’héritage ;
- composition seulement lorsque le contenu n’a pas de sens hors de son propriétaire ;
- association simple dans tous les autres cas ;
- notes jaunes pour les hypothèses et contraintes à valider ;
- modèle métier, et non schéma physique PostgreSQL ni représentation des pages Django.

## Glossaire et responsabilités

| Concept | Responsabilité |
| --- | --- |
| `Utilisateur` | État et comportements communs aux comptes HomeSkolar |
| `Eleve` | Spécialisation représentant l’élève accompagné |
| `Tuteur` | Spécialisation représentant le bénévole accompagnant |
| `DonneesPersonnelles` | Valeur regroupant les données personnelles dont le détail reste à confirmer |
| `Accompagnement` | Relation métier active entre un élève et son tuteur |
| `Conversation` | Regroupe les échanges d’un accompagnement |
| `Message` | Contenu envoyé, lu et éventuellement épinglé par l’élève |
| `Notification` | Signale à un utilisateur un message non lu ou une tâche à réaliser |
| `EvenementCalendrier` | Abstraction commune aux éléments datés affichables dans le calendrier |
| `EvenementPersonnel` | Événement propre à un utilisateur |
| `Rencontre` | Rendez-vous planifié dans le cadre d’un accompagnement |
| `ElementTravail` | Abstraction commune aux éléments de travail |
| `TacheSuivi` | Travail destiné à l’élève avant la rencontre suivante |
| `ElementPersonnel` | Tâche, note ou mémo privé appartenant à un utilisateur |

## Exigences, choix et hypothèses

### Exigences confirmées

- l’élève et le tuteur gèrent un compte et leurs données personnelles ;
- chaque élève inscrit est assigné à un tuteur ;
- les deux acteurs échangent des messages ;
- l’élève peut épingler un message ;
- les messages non lus et les tâches donnent lieu à une notification interne ;
- les rencontres et événements apparaissent dans un calendrier ;
- l’élève consulte ses tâches de suivi ;
- les deux acteurs créent des tâches, notes ou mémos personnels.

### Choix de modélisation

- `Utilisateur` est abstrait et spécialisé en `Eleve` et `Tuteur` ;
- `Accompagnement` porte la relation structurante entre les deux acteurs ;
- une `Conversation` regroupe les `Message` de l’accompagnement ;
- `EvenementCalendrier` et `ElementTravail` factorisent uniquement de véritables concepts communs ;
- les pages, formulaires, vues Django, tables et contrôleurs sont exclus du modèle métier ;
- aucune agrégation faible n’est utilisée : son sens de cycle de vie n’est pas démontré.

### Hypothèses à valider

- **H-01** : un tuteur peut accompagner plusieurs élèves ;
- **H-02** : la personne autorisée à créer une tâche de suivi reste à préciser ;
- **H-03** : un seul fil de conversation est associé à un accompagnement actif ;
- **H-04** : le détail des données personnelles est laissé ouvert ;
- **H-05** : la notification référence soit un message, soit une tâche de suivi, de manière exclusive.

## Éléments volontairement exclus

- administrateur et représentant légal ;
- processus d’affectation et historique des changements de tuteur ;
- pièces jointes et visioconférence ;
- rappels de rendez-vous, récurrence, acceptation et annulation ;
- échéance, priorité, statut détaillé et historique des tâches ;
- courriels, SMS et notifications push ;
- classes techniques Django, API, hébergement et déploiement.

## Traçabilité

| Élément UML | Responsabilité | Source | Critère couvert | Ticket | Validation | Hypothèse |
| --- | --- | --- | --- | --- | --- | --- |
| `Utilisateur`, `Eleve`, `Tuteur`, `DonneesPersonnelles` | Comptes, mot de passe et profil | US-CPT-01 à 04 | création, connexion et modification réservée au propriétaire | OCPY3-63 à 65 | Contrôlé | H-04 |
| `Accompagnement` et associations avec `Eleve`/`Tuteur` | Relation autorisant les échanges et rencontres | Note de lancement, US-COM-01, US-CAL-01 | utilisateur associé à son interlocuteur | OCPY3-66 | Partiel | H-01 |
| `Conversation`, `Message` | Envoi, ordre chronologique, lecture et épinglage | US-COM-01 à 03 | message non vide, auteur/date, lecture et épinglage | OCPY3-63 à 66 | Contrôlé | H-03 |
| `Notification`, `TypeNotification` | Messages non lus et tâches signalées | US-COM-04, US-TAC-02 | indicateur non lu et accès à la tâche | OCPY3-63 à 66 | Contrôlé | H-05 |
| `EvenementCalendrier`, `EvenementPersonnel`, `Rencontre` | Éléments datés du calendrier | US-CAL-01 à 02 | horaires valides et affichage aux dates correspondantes | OCPY3-63 à 66 | Contrôlé | — |
| `ElementTravail`, `TacheSuivi` | Tâches de suivi destinées à l’élève | US-TAC-01 à 02 | liste avant prochaine rencontre et notification | OCPY3-63 à 66 | Partiel | H-02 |
| `ElementPersonnel`, `TypeElementPersonnel` | Tâche, note ou mémo privé | US-TAC-03 à 04 | création et confidentialité par propriétaire | OCPY3-63 à 66 | Contrôlé | — |

## Contrôle de couverture

Les 14 User Stories trouvent une traduction dans le modèle. Aucun élément fonctionnel confirmé n’est dépourvu de classe ou de relation. Les classes techniques d’interface et d’infrastructure ont été écartées. Les cinq hypothèses sont signalées et doivent être soumises au mentor.

## Contrôle de conformité UML

- nommage, visibilités, types, paramètres et retours : conformes ;
- multiplicités placées aux bonnes extrémités : contrôlées ;
- héritages fondés sur une relation « est un » : conformes ;
- compositions limitées aux données personnelles et aux messages d’une conversation : justifiées comme choix de cycle de vie ;
- aucune agrégation faible ajoutée ;
- source PlantUML et SVG généré : correspondance contrôlée par rendu local ;
- syntaxe : `ClassDiagram`, 169 lignes analysées, aucun avertissement ;
- lisibilité : contrôle visuel effectué, organisation en quatre domaines, ratio compatible avec une page A4 paysage et croisements inter-domaines limités aux relations structurantes.

## Moteur de rendu

- paquet : `@plantuml/mcp-js@0.2.0` ;
- moteur embarqué : PlantUML `1.2026.7beta3` compilé en JavaScript avec TeaVM ;
- placement : `@viz-js/viz` / Graphviz WebAssembly ;
- commande : `node /tmp/plantuml-js-test/render-local.mjs diagramme-classes-homeskolar.puml diagramme-classes-homeskolar.svg` ;
- serveur public : aucun.

## Dossier de validation mentor

Le mentor doit confirmer ou corriger :

1. H-01, multiplicité des accompagnements côté tuteur ;
2. H-02, auteur autorisé des tâches de suivi ;
3. H-03, unicité de la conversation par accompagnement ;
4. H-04, contenu des données personnelles ;
5. H-05, rattachement exclusif d’une notification ;
6. conformité générale des héritages, compositions et multiplicités.

La validation humaine n’est pas acquise tant qu’un retour explicite n’a pas été consigné dans Jira.

## Historique

| Version | État | Contenu |
| --- | --- | --- |
| 0.1 | Version de travail | Classes, attributs, opérations et relations initiales |
| 0.2 | Candidat mentor | Contrôles de couverture et conformité, hypothèses explicites, rendu SVG final |

## Livrables

- [Source PlantUML](diagramme-classes-homeskolar.puml)
- [Rendu SVG](diagramme-classes-homeskolar.svg)
- [Dossier de validation mentor](validation-mentor.md)
