# Module Soudure

Tout ce qui relève de la **qualification des soudeurs** et des **modes opératoires
de soudage (DMOS/QMOS)**. Deux conversations sources, un seul module : les deux
travaillent sur le même référentiel — un certificat qualifie un soudeur *pour un
DMOS donné*, dans une plage de diamètres et d'épaisseurs.

## Conversations sources
- [`conversations/qualification-soudeur.md`](conversations/qualification-soudeur.md)
  — dépouiller les certificats scannés, fiabiliser le tableau de suivi, ranger `QS/`.
- [`conversations/dmos-par-diametre.md`](conversations/dmos-par-diametre.md)
  — générer un classeur Excel par DMOS, un onglet par diamètre et par type de joint.

## Dossiers sources (iCloud — hors repo)
```
TSI-new/03 Collaborateur/Certificat professionnel/Qualification soudeur/
    certificat-qualification-soudeur.xlsx   ← tableau de suivi, une feuille par année
    QS/                                     ← qualifications valides, soudeurs actifs
    00 Archive/                             ← échues, soudeurs partis, scans « a jour »
    01 Demande/                             ← demandes de qualification
TSI-new/01 Chantier/DMOS : QMOS/
    Template/ · 1-DMOS/ · 2-QMOS/ · Archives/ · Certificat matière/
```

## État constaté le 2026-09-12 (reconnaissance en lecture seule)
- `QS/` contient **38 PDF**, nommés `<poinçon>-<procédé>_<n° certificat>.pdf`.
  La casse du n° de certificat est **incohérente** (`AC-25-0104` vs `ac-24-00090`).
- Les scans **« TSI-0XX a jour.pdf » sont dans `00 Archive/`**, pas à la racine :
  6 fichiers — 004, 005, 007, 008, 009, 010. Le prompt mentionne 004/007/008/009/010 ;
  **`TSI-005` est en plus** et n'apparaît dans aucune plage de qualification décrite.
- `01 Demande/` contient 11 demandes `TSI-010-<prénom>.pdf` (juin 2026).

## Tenir le tableau DMOS/QMOS

`01 Chantier/DMOS : QMOS/dmos-qmos.xlsx` — un DMOS par ligne, avec sa plage de
qualification. Les QMOS sont dans `2-QMOS/`, un PDF par certificat.

⛔ **La plage se lit dans le QMOS, jamais ailleurs.** Colonne
« Geltungsbereich / domaine de validité », à ne pas confondre avec la colonne
« Durchführung / exécuté », qui donne la pièce d'essai. Les certificats de
soudeur portent des plages différentes : eux qualifient une personne, le QMOS
qualifie le mode opératoire.

Les QMOS récents sont des PDF numériques (lecture directe) ; ceux de 2021 sont
des scans dont la couche texte est inexploitable — les rendre en image à 320 dpi,
où ils redeviennent parfaitement lisibles.

## Règles dures
- **Rien n'est écrit sans accord explicite.** Les incohérences se montrent d'abord.
- **Les certificats PDF font foi** — une valeur du tableau qui les contredit est
  une erreur du tableau, pas l'inverse.
- ⛔ **Un PDF de certificat ne se modifie jamais.** C'est un document officiel émis
  par l'organisme certificateur. Ni retouche, ni annotation, ni régénération, ni
  écrasement — même pour corriger une erreur manifeste (date de naissance fausse,
  nom mal orthographié). La seule voie est une **réédition demandée à l'organisme**.
- ⛔ **Le classeur `certificat-qualification-soudeur.xlsx` ne s'écrase pas.** Il doit
  rester la **copie conforme des certificats valides de `QS/`**. Aucune écriture, pas
  même un réenregistrement par Excel pour reconstruire des caches de calcul. On
  signale l'écart, chiffres et fichier source à l'appui ; Thomas tranche.
- Si une écriture est un jour autorisée : sauvegarde d'abord, et les formules `EDATE`
  doivent référencer leur propre ligne après insertion/suppression.
- **Le poinçon fait le lien**, pas le prénom. Mapping poinçon ↔ collaborateur dans
  `TSI-new/03 Collaborateur/collaborateur.xlsx` (feuilles `en-service`,
  `hors-service`, `monteur-soudeur`). Vérifier là avant d'attribuer un certificat.
- Une ligne d'anomalie se désigne par **feuille + ligne** (« Archives ligne 10 »,
  pas « ligne 10 ») : les feuilles ont des numérotations qui se ressemblent.
- La **confirmation semestrielle ISO 9606-1** n'est pas la fin de validité à 3 ans.
  Ne jamais confondre les deux.
- Plages de qualification : **ne jamais les dépasser** (détail dans le prompt DMOS).

## Faits métier à ne pas re-demander
⚠️ **Retirés du repo** — dépôt public. Deux situations individuelles sont connues et
tranchées : un **échec d'épreuve TSI-010 en 06/2026** (le n° de certificat attendu
n'existe donc pas, ne pas le réclamer) et un **départ en 09/2026** (→ `00 Archive`
+ feuille « Archives »). Les identités sont dans le prompt original, hors repo.
L'agent doit les relire là avant d'agir.
