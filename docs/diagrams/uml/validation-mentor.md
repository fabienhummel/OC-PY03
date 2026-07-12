# Dossier de validation mentor — Diagramme UML HomeSkolar

## Livrables proposés

- [Diagramme SVG](diagramme-classes-homeskolar.svg)
- [Source PlantUML](diagramme-classes-homeskolar.puml)
- [Documentation, conventions et traçabilité](README.md)

## Contrôles déjà réalisés

- syntaxe PlantUML valide ;
- type reconnu : `ClassDiagram` ;
- aucun avertissement du moteur ;
- correspondance entre `.puml` et SVG vérifiée après chaque rendu ;
- couverture des 14 User Stories contrôlée ;
- nommage, visibilités, types, opérations et multiplicités relus ;
- héritages limités aux relations « est un » ;
- aucune agrégation faible ajoutée ;
- compositions limitées aux cycles de vie jugés dépendants ;
- contrôle visuel en ratio compatible A4 paysage.

## Questions nécessitant une validation humaine

1. Un tuteur peut-il accompagner plusieurs élèves simultanément ?
2. Qui peut créer une tâche de suivi destinée à l’élève ?
3. Un accompagnement doit-il posséder un seul fil de conversation ?
4. Quelles données personnelles doivent être représentées précisément ?
5. Une notification concerne-t-elle toujours exactement un message ou une tâche de suivi ?
6. Le mentor confirme-t-il les héritages, compositions et cardinalités proposés ?

## Décision attendue

Pour chaque question : **confirmé**, **à corriger** ou **hors périmètre**. Les remarques doivent être consignées dans OCPY3-71 avant de déclarer le diagramme validé et de clôturer OCPY3-93.
