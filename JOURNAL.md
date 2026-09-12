# Journal de bord

> **40 lignes maximum.** Ce qui est en attente passe en premier et reste entier ;
> ce qui est fini se comprime à une ligne. Élaguer à chaque `/synchronise`.
> ⛔ Dépôt public : aucun nom complet. Les personnes se désignent par leur poinçon.

## ⚠️ À FAIRE À LA MAIN — caches de calcul perdus

**Ouvrir `certificat-qualification-soudeur.xlsx` dans Excel une fois et le
réenregistrer.** L'écriture par openpyxl a vidé les valeurs en cache des colonnes
`+6` à `+36` (245 cellules en 2026, 185 en 2025). `fullCalcOnLoad` est actif, donc
Excel recalcule à l'ouverture — mais tant que ce n'est pas fait, **tout outil qui
lit le classeur sans moteur de calcul verra ces colonnes vides** et conclura à tort
que les confirmations semestrielles ont disparu.

## ⚠️ En attente d'une décision — module soudure

1. **Feuille « Archives », ligne 10** : `AC-24-00089` y est attribué au poinçon LF,
   alors que ce numéro est celui du poinçon JM, actif en 2026 et confirmé sur le
   certificat. Pas corrigé : on ignore lequel des deux champs est faux.
2. **Colonne « Pos » vide** sur les 2 lignes nouvellement archivées — la feuille
   2026 n'a pas de source pour ce champ. Ne pas inventer.
3. **Date de naissance fausse** sur un certificat TSI-010 (celle d'un autre
   soudeur). Demander une réédition à l'organisme, ou laisser ?

## Fait — 12.09.2026

- **Dépouillement des 44 certificats** (6 scans, 4 sous-agents). Le tableau ne
  contient **aucune erreur** sur n°, date d'examen et validité ; `QS/` était déjà à
  jour depuis le 09.09. Seule harmonisation appliquée : 19 noms de fichiers en
  majuscules, 38/38 cohérents.
- **Soudeur sorti (poinçon SC) archivé** : 2 lignes transposées de « 2026 » vers
  « Archives » — les 2 feuilles n'ont pas le même ordre de colonnes — 41 formules
  `EDATE` réécrites sur leur propre ligne, styles et formats repris de la feuille
  cible. Sauvegarde dans `00 Archive/`. Relu par un agent indépendant : 0 écart
  ailleurs. 43 lignes → 41, 40 certificats → 38.
- **Tranché** : les 2 TSI-004 du poinçon CP sont **complémentaires** (3–7 mm + angle
  contre 2,6–5,2 mm dès Ø25) et restent tous deux · `AC-26-0303` signée déjà dans
  `QS/` · rien de caduc en emplacement actif · les 2 lignes sans certificat sont
  une note personnelle, ne pas y toucher.
- **Module** : 11 agents (1 coordinateur, 3 métier, 5 transverses, 2 de contrôle),
  3 commandes de continuité, skill `depouiller-certificats`, exposition `.claude/`
  par liens symboliques.

## Modules sans activité
`controle-chantier` · `rapport-hebdomadaire` — définis, jamais exercés.
