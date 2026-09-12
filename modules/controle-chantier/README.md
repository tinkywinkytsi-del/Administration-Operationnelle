# Module Contrôle de chantier

Le **procès-verbal de contrôle de chantier** : 3 contrôles par an, un PV chacun.

## Conversation source
- [`conversations/pv-v4.md`](conversations/pv-v4.md) — refonte du PV en V4,
  2 pages A4 maximum, avec liaison automatique vers les qualifications soudeurs.

## Dossier source (iCloud — hors repo)
```
TSI-new/01 Chantier/Contrôle de chantier/
    Procès-verbal-chantier.xlsx           ← original, à ne pas toucher
    Procès-verbal-chantier_V4_2026.xlsx   ← une V4 existe DÉJÀ (07.09.2026)
    PV_Controle_chantier_TSI.docx         ← variante Word (03.07.2026)
    00 Archive/<année>/controle-chantier_<aa-mm-jj>.pdf
```

## État constaté le 2026-09-12 (reconnaissance en lecture seule)
**21 PV archivés**, de 2020 à 2025 :

| année | nb | anomalie |
|---|---|---|
| 2020 | 2 | sous la cadence annoncée de 3/an |
| 2021 | 4 | au-dessus |
| 2022 | 4 | au-dessus |
| 2023 | 5 | au-dessus |
| 2024 | 3 | conforme |
| 2025 | 3 | conforme |

- **Aucun PV pour 2026** dans les archives, alors qu'un `_V4_2026.xlsx` existe.
- Trois fichiers coexistent à la racine (xlsx original, xlsx V4, docx) sans
  qu'un seul soit désigné comme la version de référence — **le versionnement
  est à clarifier avant de produire une V4 de plus.**

## Règles dures
- L'original `Procès-verbal-chantier.xlsx` **reste intact** : on travaille sur copie.
- **2 pages A4 portrait maximum** à l'impression, zone d'impression et saut de page
  définis — c'est la contrainte structurante, pas un souhait.
- Analyse **avant** construction : le taux de remplissage réel des PV archivés
  décide de ce qu'on supprime et de ce qu'on renforce.
- **Personne ne valide seul son propre travail** : un agent relecteur distinct
  relit fichier et script, et la revue repasse jusqu'à approbation.
- Pas de lien de formule entre fichiers iCloud (fragile) : feuille interne masquée
  + menus déroulants.
- Jamais de blanc silencieux sur une qualification : « NON QUALIFIÉ »,
  « requalif. avant [date] » ou « ÉCHUE ».

## Dépendance
La liaison soudeurs consomme le tableau fiabilisé par le [module Soudure](../soudure/README.md).
Fiabiliser d'abord, câbler ensuite.
