# Journal de bord

> **40 lignes maximum.** Ce qui est en attente passe en premier et reste entier ;
> ce qui est fini se comprime à une ligne. Élaguer à chaque `/synchronise`.
> ⛔ Dépôt public : aucun nom complet. Les personnes se désignent par leur poinçon.

## Point de départ pour une session neuve
Module **opérationnel**, dépôt propre. Lire ce fichier puis `docs/ORGANISATION.md`
qui fait foi ; parler au `coordinateur`. Accès iCloud via
`permissions.additionalDirectories` (`.claude/settings.local.json`, non versionné).

## ⚠️ En attente d'une décision — module soudure
**Feuille « Archives », ligne 10 (poinçon LF, sorti)** : le n° `AC-24-00089` y est
inscrit alors qu'il appartient au poinçon JM (`QS/jm-141_AC-24-00089.pdf`, lu).
Le certificat de LF dans `00 Archive/` porte **`AC-24-00086`** — même DMOS TSI-004,
même examen 11.10.24, même validité 10.10.27. Erreur héritée de la feuille 2024,
qui portait déjà ce numéro sur 2 lignes (40 et 42). **Non corrigé** — Thomas décide.

**Piège « Archives », colonne « t validité »** : le format de cellule est le
littéral `\3\-\7`, donc Excel affiche « 3-7 » quel que soit le contenu. Dessous,
les lignes 2, 4 et 10 stockent des **numéros de série de date** (45476 = 03.07.24).
À l'œil c'est juste ; toute lecture programmatique est fausse. Ne pas « corriger ».

## Tranché le 12.09.2026 — ne pas y revenir
- Ligne 10 de la feuille **2026** (poinçon RC, `AC-24-00088`) : **juste**, vérifiée
  contre `QS/rc-141_AC-24-00088.pdf`. L'anomalie est sur « Archives », pas là.
- Colonne « Pos » laissée **vide** sur les 2 lignes archivées : pas de source.
- TSI-010 à date de naissance fausse : **jamais de retouche d'un PDF de
  certificat**. Seule voie admissible, une réédition demandée à l'organisme.
- **Aucune écriture dans `certificat-qualification-soudeur.xlsx`**, pas même un
  réenregistrement par Excel : il doit rester copie conforme de `QS/`.
- Mapping poinçon ↔ collaborateur : `03 Collaborateur/collaborateur.xlsx`.

## Fait — 12.09.2026
- **Module créé de zéro** : 14 agents, `docs/ORGANISATION.md`, 3 commandes, skill
  `depouiller-certificats`, 4 prompts sources archivés.
- **44 certificats dépouillés** : tableau sans erreur, `QS/` à jour, 38/38 noms
  cohérents · SC archivé (2 lignes, 41 `EDATE`, relu) · les 2 TSI-004 de CP restent.

## Modules jamais exercés
`controle-chantier` · `rapport-hebdomadaire` · `appels-offres` · `attestations` · `radiographies`.
