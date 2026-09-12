---
conversation: Dépouillement des certificats de qualification soudeur
date_source: 2026-09-12
verse_le: 2026-09-12
---

> ⚠️ **Version caviardée.** Ce dépôt est public : les rappels nominatifs
> (échec d'examen, départ de l'entreprise) ont été retirés.

# Prompt d'origine — caviardé

```text
Je suis le technologue en soudage de TSI SA. Voici le tableau de suivi des
qualifications de soudeur (certificat-qualification-soudeur.xlsx) et les
certificats renouvelés/signés scannés (fichiers « TSI-0XX a jour.pdf », un
par DMOS ; certains certificats couvrent deux DMOS à la fois, ex. TSI004+TSI009).

Dossier de travail : iCloud/TSI-new/03 Collaborateur/Certificat professionnel/
Qualification soudeur/

1. Dépouille chaque PDF scanné (1 certificat = 2 pages : données + conditions)
   et identifie pour chacun : n° de certificat, soudeur, référence DMOS/WPS,
   date d'examen, validité, visas 6 mois signés.
2. Compare avec le dossier QS/ et la feuille de l'année du tableau. Montre-moi
   les incohérences AVANT toute action définitive : certificat sans ligne ou
   sans fichier, numéro erroné dans le tableau, certificat échu, doublon.
3. Après mon accord : découpe les PDF (1 page = la page de données signée),
   nomme-les <poinçon minuscule>-<procédé>_<n° certificat>.pdf et remplace les
   versions non signées dans QS/. Toute version remplacée part dans 00 Archive
   (suffixe si collision de nom). Archive aussi les PDF sources.
4. Mets à jour la feuille de l'année : n° certificat (col. F), date de soudage
   (col. M), validité (col. S), en conservant les formules EDATE (+6 à +36 mois)
   — après insertion/suppression de ligne, chaque formule doit référencer sa
   propre ligne. Sauvegarde le fichier avant modification.
5. Règles : QS/ ne contient que des qualifications valides de soudeurs actifs ;
   un certificat échu ou un soudeur parti va dans 00 Archive, et un soudeur
   parti est reporté dans la feuille « Archives » du classeur.

[RAPPELS NOMINATIFS RETIRÉS — dépôt public : un échec d'épreuve TSI-010 en 06/2026
dont le n° de certificat n'existe donc pas, et un départ en 09/2026 à reporter dans
la feuille « Archives ». Identités et références dans le prompt original, hors repo.]
```
