# 🗂️ Kanban du Backlog Produit

> [!NOTE]
> **État initial de HomeSkolar** — les 17 User Stories sont prêtes pour la planification et le développement n’a pas commencé.

La priorité indique la valeur métier. Les dépendances précisent les prérequis techniques ou fonctionnels à terminer avant de commencer une User Story.

| 🟣 **PRÊT** | 🔵 **EN COURS** | 🟢 **TERMINÉ** |
|:---:|:---:|:---:|
| **17 cartes** | **0 carte** | **0 carte** |
| DoR satisfaite | Développement non commencé | Aucune DoD validée |

## Tableau visuel

<table>
  <thead>
    <tr>
      <th width="46%">🟣 PRÊT · 17</th>
      <th width="27%">🔵 EN COURS · 0</th>
      <th width="27%">🟢 TERMINÉ · 0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top"><strong>🔴 US-CPT-01 · P0 · 1,5 j</strong><br>Créer librement un compte élève ou tuteur<br><sub>↳ Prérequis : aucun</sub></td>
      <td rowspan="17" valign="top"><strong>Aucune carte</strong><br><br>Une carte entre ici lorsque sa réalisation commence et que ses prérequis sont terminés.</td>
      <td rowspan="17" valign="top"><strong>Aucune carte</strong><br><br>Une carte entre ici uniquement après validation de ses critères d’acceptation et de la Definition of Done.</td>
    </tr>
    <tr><td valign="top"><strong>🔴 US-CPT-02 · P0 · 1 j</strong><br>Se connecter et se déconnecter<br><sub>↳ US-CPT-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-CPT-05 · P0 · 1,5 j</strong><br>Réinitialiser son mot de passe par courriel<br><sub>↳ US-CPT-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-CPT-06 · P0 · 1,5 j</strong><br>Supprimer son compte et ses données<br><sub>↳ US-CPT-02</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-AFF-01 · P0 · 2 j</strong><br>Affecter aléatoirement un tuteur à un élève<br><sub>↳ US-CPT-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-COM-01 · P0 · 2 j</strong><br>Échanger des messages avec son binôme<br><sub>↳ US-CPT-02, US-AFF-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-COM-02 · P0 · 1,5 j</strong><br>Voir les messages non lus et la notification interne<br><sub>↳ US-COM-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-RDV-01 · P0 · 1,5 j</strong><br>Créer un rendez-vous pour un élève<br><sub>↳ US-CPT-02, US-AFF-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-RDV-02 · P0 · 1,5 j</strong><br>Consulter ses rendez-vous<br><sub>↳ US-RDV-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-RDV-03 · P0 · 1,5 j</strong><br>Modifier ou annuler un rendez-vous<br><sub>↳ US-RDV-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-TAC-01 · P0 · 1,5 j</strong><br>Attribuer une tâche de suivi à un élève<br><sub>↳ US-CPT-02, US-AFF-01</sub></td></tr>
    <tr><td valign="top"><strong>🔴 US-TAC-02 · P0 · 1 j</strong><br>Consulter une tâche attribuée<br><sub>↳ US-TAC-01</sub></td></tr>
    <tr><td valign="top"><strong>🟠 US-CPT-03 · P1 · 1 j</strong><br>Modifier son profil<br><sub>↳ US-CPT-02</sub></td></tr>
    <tr><td valign="top"><strong>🟠 US-CPT-04 · P1 · 1 j</strong><br>Changer son mot de passe<br><sub>↳ US-CPT-02</sub></td></tr>
    <tr><td valign="top"><strong>🟠 US-COM-03 · P1 · 1 j</strong><br>Épingler un message en tête de conversation<br><sub>↳ US-COM-01</sub></td></tr>
    <tr><td valign="top"><strong>🟠 US-TAC-03 · P1 · 1,5 j</strong><br>Créer une tâche, note ou mémo personnel<br><sub>↳ US-CPT-02</sub></td></tr>
    <tr><td valign="top"><strong>🟠 US-TAC-04 · P1 · 1 j</strong><br>Modifier ou supprimer un élément personnel<br><sub>↳ US-TAC-03</sub></td></tr>
  </tbody>
</table>

**Légende :** 🔴 P0 — indispensable · 🟠 P1 — important · ↳ dépendance.

## Règles d’entrée et de sortie

| 🟣 **Definition of Ready — DoR** | 🟢 **Definition of Done — DoD** |
|---|---|
| Le besoin et les tâches sont compris. | Tous les critères d’acceptation sont vérifiés. |
| La User Story respecte les objectifs du produit. | Les tests unitaires sont réussis. |
| Les critères d’acceptation sont explicites. | La fonctionnalité est déployée dans un environnement d’essai. |
| Les compétences nécessaires sont disponibles. | La fonctionnalité est validée par l’équipe. |
| Les dépendances externes sont levées. | La fonctionnalité peut être présentée au client. |

## Règles de déplacement

```text
🟣 PRÊT  ───────────────▶  🔵 EN COURS  ───────────────▶  🟢 TERMINÉ
  DoR satisfaite             réalisation démarrée          DoD satisfaite
```

- une User Story passe dans « En cours » lorsque sa réalisation commence et que ses prérequis internes sont terminés ;
- elle passe dans « Terminé » lorsque tous ses critères d’acceptation et toute la DoD sont validés ;
- une carte inachevée à la fin d’un sprint retourne dans le Product Backlog ;
- la priorité ne dispense pas de respecter les dépendances ;
- toute modification du périmètre est validée avant l’ajout, le retrait ou la réestimation d’une User Story.

> **Charge de base : 23,5 jours idéaux** · Enveloppe avec marge de 20 % : **28 jours idéaux**.

Les critères détaillés sont disponibles dans le [Backlog Produit](backlog-produit.md).
