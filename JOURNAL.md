# Journal de bord

> **40 lignes maximum.** Ce qui est cassé ou en attente passe en premier et reste
> entier ; ce qui est fini se comprime à une ligne. Élaguer à chaque
> `/synchronise` — un journal long renchérit la relève là où elle doit être
> bon marché.
>
> ⛔ Dépôt public : **aucun nom complet, aucune donnée nominative ici.**
> Les personnes se désignent par leur poinçon ou leur nom d'onglet.

## ⚠️ En attente d'une décision — module soudure

1. **Feuille « Archives », ligne 10** : le certificat `AC-24-00089` y est attribué au
   poinçon LF, alors que ce numéro est celui du poinçon JM, actif en 2026 et
   confirmé sur le certificat. Deux personnes ne peuvent porter le même numéro.
   Pas corrigé : on ignore lequel des deux champs est faux.
2. **Colonne « Pos » vide** sur les 2 lignes nouvellement archivées — la feuille
   2026 n'a pas de source pour ce champ. Ne pas inventer.
3. **Erreur de source non tranchée** : une date de naissance fausse sur un
   certificat TSI-010 (celle d'un autre soudeur). Décision attendue : demander
   une réédition, ou laisser.

## ⚠️ À FAIRE À LA MAIN — caches de calcul perdus

**Ouvrir `certificat-qualification-soudeur.xlsx` dans Excel une fois et le
réenregistrer.** L'écriture par openpyxl a vidé les valeurs en cache des colonnes
`+6` à `+36` (245 cellules en 2026, 185 en 2025). `fullCalcOnLoad` est actif, donc
Excel recalcule à l'ouverture — mais tant que ce n'est pas fait, **tout outil qui
lit le classeur sans moteur de calcul verra ces colonnes vides** et conclura à tort
que les confirmations semestrielles ont disparu.

## Erreurs de la source — à faire corriger par l'organisme certificateur

Une date de naissance erronée sur un certificat TSI-010 · six désignations
tronquées (`D` sans diamètre, `s7.11` au lieu de `s7.1`) · un patronyme
probablement mal orthographié · une macrographie cochée « réalisé » et
« non requis » à la fois.

## Fait

- **12.09.2026 — soudeur sorti (poinçon SC) archivé.** Ses 2 lignes transposées de
  « 2026 » vers « Archives » (les 2 feuilles n'ont pas le même ordre de colonnes),
  41 formules `EDATE` réécrites pour référencer chacune leur propre ligne, styles
  et formats d'affichage repris de la feuille cible. Sauvegarde dans `00 Archive/`.
  Relu par un agent indépendant : **0 écart** sur les autres lignes et sur les
  feuilles historiques. 43 lignes → 41, 40 certificats → 38.
- **12.09.2026 — décisions tranchées** : les 2 TSI-004 d'un même soudeur (poinçon CP)
  sont **complémentaires** (3–7 mm + angle · 2,6–5,2 mm dès Ø25) et restent tous deux.
  `AC-26-0303` : la version signée est déjà celle de `QS/`, rien à faire. Rien de
  caduc dans un emplacement actif. Les 2 lignes sans certificat sont une note
  personnelle, pas une anomalie — ne pas y toucher.
- **12.09.2026 — dépouillement complet des 44 certificats** (6 PDF scannés,
  lecture répartie sur 4 sous-agents). Résultat : le tableau **ne contient
  aucune erreur** sur le n° de certificat, la date d'examen et la validité ; le
  dossier `QS/` était **déjà à jour** depuis le 09.09. Seule harmonisation
  nécessaire et appliquée : **19 noms de fichiers** passés en majuscules
  (38/38 cohérents).
- **12.09.2026** — création du module, de ses 3 sous-modules et de leurs agents.
- **12.09.2026** — architecture portée à **11 agents** : un coordinateur, 3 métier,
  5 transverses (par verbe, pas par dossier), 2 de contrôle obligatoires.
  Commandes de continuité, `JOURNAL.md`, skill `depouiller-certificats`, et
  exposition sous `.claude/` par liens symboliques.

## Modules sans activité

`controle-chantier` · `rapport-hebdomadaire` — définis, jamais exercés.
