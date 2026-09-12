---
name: depouiller-certificats
description: Dépouiller les certificats de qualification de soudeur scannés (ISO 9606-1), les croiser avec le tableau de suivi et le dossier QS/, et dresser la liste des incohérences. À utiliser dès qu'il faut lire des certificats scannés, vérifier des échéances semestrielles, ou contrôler la cohérence entre les PDF, le classeur et le dossier de classement.
---

# Dépouiller les certificats de qualification de soudeur

Procédure éprouvée le 12.09.2026 sur 44 certificats. **Lecture et comparaison
d'abord ; aucune écriture sans accord explicite.**

## ⛔ Les trois pièges qui font perdre le plus de temps

**1. Les colonnes `+6` à `+36` du tableau ne disent PAS si un visa est signé.**
Ce sont des échéances calculées par `EDATE` depuis la date de soudage. Lire
« prochaine confirmation le 13.09 » comme une alerte est une erreur : le visa
peut être signé depuis des semaines. **Seul le certificat dit s'il est visé.**
Ne jamais alerter sur une échéance sans avoir ouvert le PDF.

**2. Vérifier que `QS/` n'est pas DÉJÀ à jour avant de remplacer quoi que ce soit.**
Le travail a peut-être été fait dans une session précédente. Contrôle bon marché :
comparer les dates de modification des fichiers de `QS/` avec celles des scans.
Des fichiers postérieurs aux scans sont déjà les versions découpées. Confirmer
sur un ou deux fichiers en les rendant en image. Remplacer des fichiers déjà
corrects par des copies redécoupées est une perte sèche, et un risque.

**3. Deux gabarits de certificat coexistent.** Aucun script ne peut les traiter
uniformément :

| | **SVS/ASS** (Bâle) | **AC Contrôle Sàrl** (Bex) |
|---|---|---|
| Désignation | ligne 2 | ligne 2 « Déscriptif du certificat » |
| Réf. DMOS | ligne 3 | ligne 4 « Référence DMOS / WPS » |
| Nom + n° | ligne 4 | lignes 3 et 5, séparés |
| Visas | ligne 38, **deux blocs** gauche/droite | bloc **K**, **un seul** tableau 6→36 mois |
| Dates | « Date de soudage » / « valide jusqu'au » | « Date d'examen » / « Validité jusqu'au » |

Et **l'ordre nom/prénom diffère selon l'émetteur** — « Prénom Nom » sur l'un,
« Nom Prénom » sur l'autre. Tout rapprochement automatique par nom se casse là ;
rapprocher par **numéro de certificat**.

## Procédure

### 1. Rendre les pages
Les scans n'ont **aucune couche texte**. `pdftoppm` n'est pas installé ; utiliser
**PyMuPDF** :

```python
import fitz
d = fitz.open(chemin)
for i in range(0, d.page_count, 2):        # pages impaires = page de données
    d[i].get_pixmap(dpi=120).save(f"{tag}_c{i//2+1:02d}.png")
```

Un certificat = **2 pages** (données + conditions). Seules les pages impaires
portent les données et les visas. 120 dpi suffit à lire les visas manuscrits.

### 2. Répartir la lecture
Au-delà d'une dizaine de certificats, répartir sur des sous-agents — un par
fichier source. Leur demander de **transcrire, pas d'interpréter** : tout
caractère douteux suivi de `(?)`, aucune donnée déduite. Les visas manuscrits
sont le point faible : `04/25` et `09/25` se confondent, `03/26` et `03/25`
aussi. Une lecture incertaine se signale, elle ne se tranche pas par le calcul
de la cadence semestrielle.

### 3. Extraire le tableau
Feuille de l'année en cours. Colonnes utiles : B = réf. DMOS, C = nom d'onglet,
E = poinçon, **F = n° de certificat**, M = date de soudage, N→S = échéances
`+6` à `+36`, S = fin de validité.

### 4. Croiser — les contrôles qui paient
Rapprocher par **numéro de certificat normalisé** (casse et tirets retirés) :

- lignes du tableau **sans fichier** dans `QS/`
- fichiers `QS/` **sans ligne** dans le tableau
- poinçon du nom de fichier ≠ poinçon du tableau
- **même n° sur plusieurs lignes** → certificat couvrant deux DMOS (cas normal,
  imprimé sur le certificat : « TSI004 + TSI009 »)
- lignes **sans certificat** → NON QUALIFIÉ, à déclarer explicitement
- **certificats du scan absents du tableau** → souvent des certificats **périmés**.
  Un visa apposé après la fin de validité ne prolonge rien : il faut une
  requalification.
- écarts entre tableau et certificat sur la date d'examen et la validité

### 5. Présenter, puis attendre
Montrer les incohérences **avant** toute action définitive. Distinguer nettement :

| | |
|---|---|
| **erreurs du tableau** | à corriger — les certificats font foi |
| **erreurs de la source** | à faire corriger par l'organisme certificateur, jamais par nous |
| **décisions humaines** | doublons, requalifications, sorties de collaborateur |

## Règles de classement
- `QS/` ne contient que des qualifications **valides** de soudeurs **actifs**.
- Certificat échu **ou** soudeur parti → `00 Archive`, et le soudeur parti est
  reporté dans la feuille « Archives » du classeur. Un visa récent ne change
  rien : c'est la personne qui est sortie, pas la qualification qui a expiré.
- Nommage : `<poinçon minuscule>-<procédé>_<N° CERTIFICAT EN MAJUSCULES>.pdf`.
- Sauvegarde du classeur **avant** toute modification. Toute version remplacée
  part dans `00 Archive` (suffixe en cas de collision).

## Détail technique
Le système de fichiers macOS est **insensible à la casse** : renommer `ac-` en
`AC-` demande deux `mv` successifs via un nom temporaire, sinon l'opération est
silencieusement ignorée.
