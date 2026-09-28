---
name: saisir-fiches-heures
description: Saisir les fiches hebdomadaires d'heures et de frais dans le rapport mensuel Excel, à partir des scans PDF, et tenir à jour les récapitulatifs. À utiliser dès qu'un nouveau scan de fiches arrive, ou qu'il faut savoir qui doit encore sa feuille.
---

# Saisir les fiches d'heures et tenir les récapitulatifs

Procédure éprouvée sur les semaines du 31.08, 07.09 et 14.09.2026 — environ
80 fiches. **Lecture d'abord, écriture ensuite, relecture toujours.**

## ⛔ Les cinq pièges qui coûtent le plus cher

**1. Ne jamais écrire dans un classeur ouvert dans Excel.**
Si Excel a le fichier ouvert et que le script écrit sur le disque, le prochain
`Cmd+S` de l'utilisateur écrase tout le travail par la version en mémoire
d'Excel. Vérifier avant d'écrire :
```bash
osascript -e 'tell application "Microsoft Excel" to get name of every workbook'
```
Et prévenir explicitement après chaque écriture : **fermer sans enregistrer,
puis rouvrir**.

**2. Apparier par NOM, jamais par numéro de ligne.**
Les onglets de suivi hebdomadaires sont en ordre alphabétique ; le récap a été
retrié par chantier. Un appariement positionnel produit des statuts faux et
crédibles — des gens déclarés débiteurs alors que leur fiche vient d'être
saisie. Construire systématiquement les dictionnaires depuis la colonne « Nom »
de **chaque** onglet.

**3. `D` = le total NOTÉ sur la fiche, jamais un recalcul.**
Un départ à 6h00 avec un total noté de 8,5 est normal : le trajet n'est pas
compté, il est couvert par le déplacement. Corriger ce total est une faute.

**4. Une valeur hors grille est une erreur de lecture, pas une exception.**
La grille des frais est **25 / 65 / 105 / 145**. Toute autre valeur doit être
relue avant d'être saisie — un « 85 » lu sur une fiche s'est révélé être un
« 25 » après rendu à 500 dpi, soit 35 CHF de déplacement indus dans un document
qui alimente la paie.

**5. Ne jamais deviner une donnée illisible.** Deux recours légitimes, dans cet
ordre : le **total hebdomadaire noté sur la fiche** (c'est une donnée écrite par
le collaborateur, pas une déduction) puis un **rendu à 300–500 dpi** de la seule
cellule. Si ni l'un ni l'autre ne tranche, on le signale et on demande.

## Le repérage des lignes

`row = 12 + numéro du jour`. Pour septembre 2026 :

| semaine | lignes |
|---|---|
| Lu 07 → Ve 11 | 19 à 23 |
| Lu 14 → Ve 18 | 26 à 30 |
| Lu 21 → Ve 25 | 33 à 37 |

Colonnes éditables : **C, D, E, F, H, I**, plus `G` pour la seule formule
`=Dn-Cn`. Ne jamais écrire dans A et B.

## La procédure

### 1. Rendre les pages
Les scans n'ont aucune couche texte. `pdftoppm` n'est pas installé ;
**PyMuPDF** l'est : `page.get_pixmap(dpi=130)`. Attendre des versos vierges —
les compter, ne pas les saisir.

### 2. Répartir la lecture
Au-delà d'une dizaine de fiches, répartir sur des sous-agents, 8 pages chacun.
Leur transmettre mot pour mot la règle « transcris, n'interprète pas ».

### 3. Identifier le collaborateur
⚠️ Beaucoup de fiches sont écrites sur un **formulaire pré-imprimé au nom d'un
autre**, barré. Retenir le **nom manuscrit non barré**. Le rapprochement se fait
par la table nom complet → onglet du récap, jamais par le prénom seul :
plusieurs collaborateurs partagent un prénom ou un patronyme.

### 4. Convertir les frais
`E` = repas, `F` = déplacement = total noté − repas, **vide si ≤ 0**.

| noté | E | F |
|---|---|---|
| 25 | 25 | vide |
| 65 | 25 | 40 |
| 105 | 25 | 80 |
| 145 | 25 | 120 |

**Exception** : deux collaborateurs ont un repas à **50 CHF/jour** — leur `E` vaut
50 même s'ils notent 25, et leur `F` est alors vide. La liste est dans le prompt
source du module.

### 5. Les absences
| cas | C | D | E/F | H | I |
|---|---|---|---|---|---|
| **Férié / congé offert** | **0** | 0 | vides | **pas de H** | libellé |
| **Congé · vacances · maladie · arrêt** | **8,5 ou 7,5** | 0 | vides | **1** | libellé exact |

La distinction est la source d'erreur la plus fréquente : un relecteur a réclamé
`C=0` pour des vacances en invoquant la règle du férié. **C ne vaut 0 que pour un
férié.** Pour un congé, le salarié « doit » ses heures et son solde est décompté.

Conséquence à signaler : une semaine d'absence retire **41,5 h** au cumul d'heures
supplémentaires, en plus des 5 jours de solde. C'est la convention du classeur,
mais elle mérite d'être dite.

### 6. Jamais de blanc silencieux
Un jour ouvré sans heures et sans libellé se marque **« À clarifier »** en
colonne I. Une case vide ne se distingue pas d'un oubli.

### 7. Les trois récapitulatifs
Ils doivent dire la même chose, pour tout le monde :
- l'**onglet de suivi** de la semaine (`JJ.MM.AA`), créé par copie du précédent ;
- le **récap mensuel**, une colonne par semaine ;
- **« Qui doit sa fiche »**, trié par urgence, les débiteurs en tête et en gras.

Contrôle final obligatoire : croiser les trois par nom et exiger **zéro écart**.

### 8. Statuts utilisés
`Reçu` · `Manquant` · `Incomplète` (rendue mais inexploitable) · `Vacances` ·
`Congé maladie` · et tout statut d'affectation déclaré. Chaque statut a sa
couleur, et la légende doit rester exacte.

## Contrôles avant livraison
- `C44 = 174,5` pour un mois de septembre sans absence
- tout jour `H=1` a bien `C` non nul, `D=0`, `E`/`F` vides et un libellé
- aucun `E`/`F` rempli avec `D` vide ou nul
- chaque formule `=Dn-Cn` référence **sa propre ligne**
- `H44 ≥ 0`, sauf les exceptions déjà documentées
- les totaux recalculés en Python concordent avec ceux notés sur les fiches

## Enregistrement
**Une version = une sauvegarde.** `vN` → `vN+1`, jamais d'écrasement. Les
formules écrites par openpyxl n'ont pas de valeur en cache : il faut **ouvrir le
classeur dans Excel et l'enregistrer une fois** pour les reconstruire.

## Rangement des scans
Un PDF par semaine, nommé **par le lundi** : `rapport-JJ-MM-AAAA.pdf`, dans le
dossier du mois de ce lundi. Un scan qui mélange deux semaines se scinde ; les
versos vierges restent attachés à leur recto. Les sources partent en
`00 Archive`, jamais supprimées — et on vérifie que le total de pages est
conservé.

⚠️ Contrôler que **chaque date de fichier tombe bien un lundi** : c'est ce test
qui a révélé un fichier mal daté d'un jour depuis des mois.
