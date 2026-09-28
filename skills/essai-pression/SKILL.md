---
name: essai-pression
description: Essais de pression des réseaux CAD — calcul du volume d'eau, pression d'épreuve, lecture des rapports de manomètre enregistreur, transmission au maître d'ouvrage. À utiliser dès qu'il est question d'épreuve hydraulique, de volume de remplissage, de rinçage ou de rapport d'essai de pression.
---

# Essai de pression d'un réseau CAD

## Calculer le volume d'eau

Le volume dépend du **diamètre intérieur du tube de service**. L'enveloppe
(`De`) est l'isolation : elle ne contient pas d'eau.

| désignation | tube de service | Ø intérieur | **volume** |
|---|---|---|---|
| `DN 100 / De 250` | 114,3 × 3,6 | **107,1 mm** | **9,01 l/m** |

Formule : `V = π × (Di/2)² × L`.

⚠️ **Attention à ce que recouvre la longueur.** Un réseau aller-retour compte
**deux fois** la longueur de tranchée. Le linéaire à retenir est le **linéaire de
tube**, recoupé sur les bons de livraison, coudes compris :

> 36 barres de 12 m (432 m) + 18 coudes 1×1 m (36 m) + 2 coudes 1×2 m (6 m)
> + 2 coudes 1×1,5 m (5 m) = **479 m** → 479 × 9,01 = **4,32 m³**

Ne jamais mesurer une longueur au pixel sur un plan : la demander, ou la lire sur
les bons de livraison.

## La pression d'épreuve

**1,5 × la pression de service** — mais la pression de service dépend du cahier
des charges applicable, et ils ne donnent pas tous la même valeur.

⛔ **Ne jamais retenir un chiffre sans identifier la prescription qui s'applique.**
Le tableau des valeurs par prescription, et les pièges de numérotation relevés
dans ces documents, sont dans le module
[`essai-de-pression`](../../modules/essai-de-pression/README.md) — s'y référer
avant tout calcul.

⛔ **Vérifier l'arithmétique du protocole lui-même.** Un protocole a longtemps
porté « 37,5 bar — 1,5 × 24 bars » : les deux chiffres ne peuvent pas être vrais
ensemble, 1,5 × 24 = 36. Selon qu'on retient l'un ou l'autre, une même courbe
passe ou ne passe pas le critère.

## Lire un rapport de manomètre

Les rapports donnent : pression requise, dérive, variation nette, durée, et les
extrema de la courbe. **Le critère, c'est le minimum de la courbe comparé à la
pression d'épreuve** — pas la variation.

La variation s'apprécie au regard de l'incertitude du manomètre et de la
**température de l'eau**, dont la courbe figure sur le rapport. Les CTG du maître
d'ouvrage ne fixent **aucune tolérance chiffrée** : la validation est
**contradictoire** entre TSI et la Direction des Travaux. Ne jamais affirmer
seul la conformité — la proposer.

Durée : minimum **6 h** selon les CTG.

## Ce qu'il faut recouper

- **Pression requise du rapport** contre celle du protocole
- **Numéros de série des manomètres** contre les certificats d'étalonnage annexés
  au protocole : un rapport produit avec un autre instrument rend les certificats
  sans objet
- La mention « la dépressurisation finale n'est pas enregistrée » est normale et
  sans effet sur le résultat

## Après l'épreuve
1. **Test d'étanchéité des vannes** : redescendre à la pression de service, fermer,
   vidanger en aval, contrôler 2 h.
2. **Rinçage final** avant mise en service : un volume complet, puis environ deux
   fois ce volume.
3. Les conduites restent **en eau, sans air**, ramenées à 1 bar au point haut.

## Transmettre au maître d'ouvrage
Un tableau court suffit : durée, pression minimale, variation nette, par conduite.
Annoncer le maintien de la pression, proposer la validation contradictoire, et
annoncer les étapes suivantes. Joindre les rapports **et** le protocole.
