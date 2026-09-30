# Journal de bord

> **40 lignes maximum.** Ce qui est en attente passe en premier ; ce qui est fini
> se comprime à une ligne. Élaguer à chaque `/synchronise`.
> ⛔ Dépôt public : aucun nom complet, aucune donnée nominative.

## Point de départ pour une session neuve

Module opérationnel et à jour. Lire ce fichier, puis `docs/ORGANISATION.md` qui
fait foi, puis `contexte-partage/` — désormais renseigné : l'entreprise, les
enjeux, et le vocabulaire métier. Parler au `coordinateur`. L'accès à la base
documentaire iCloud est accordé automatiquement.

## Dossier de révision — 30.09

Premier dossier monté et **remis**. Le module, le skill et l'agent en
sont sortis : `modules/dossier-de-revision/`, `skills/monter-dossier-revision/`.

Ce qui a compté, et qui resservira à chaque dossier :
- **l'arborescence attendue était écrite dans les courriels du chantier** — la
  chercher avant de choisir une structure ;
- le **dépouillement des courriels fait partie du montage** : il a livré la
  validation d'un essai qui n'existait nulle part ailleurs, la version de
  référence d'un jeu de rapports, et la preuve qu'une pièce était déjà partie ;
- les **recoupements** ont trouvé des soudures contrôlées et absentes du
  registre, et un mode opératoire trop étroit pour la moitié des joints.

⛔ **Une demande de modification d'un registre de traçabilité a été refusée**,
puis faite une fois établi qu'il s'agissait d'une erreur de saisie. La règle est
dans le module : c'est la réalité du chantier qui tranche, jamais le document le
plus facile à changer.

⚠️ **Pièges d'outillage, consignés dans le skill** : Excel et Word refusent
d'écrire un PDF dans iCloud ; openpyxl détruit les zones d'impression d'un
classeur formaté — patcher le XML.

## ⚠️ En attente d'une décision

1. **Soudure** — feuille « Archives » ligne 10 : un n° de certificat attribué au
   mauvais poinçon. Colonne « Pos » vide sur 2 lignes archivées. Une date de
   naissance fausse sur un certificat TSI-010.
2. **Soudure** — le QMOS TSI 008 indique un gaz `I1` (argon pur) alors que le
   procédé est 136 et le fil classé M21 ; le tableau dit ARCAL 5. À faire
   confirmer par l'organisme.
3. **Soudure** — groupe matériaux du TSI 010 : `1.1` au QMOS, `1.2` sur les
   certificats de soudeur. Et toujours pas de TSI 006, ni dans le tableau ni
   dans `2-QMOS/`.
4. **Rapport hebdo** — un collaborateur a rendu 2 fiches sans aucun total
   d'heures : inexploitables, heures à redemander. Un autre a noté un jour sans
   heures avec un libellé hors nomenclature.
5. **Rapport hebdo** — juillet et août n'ont qu'un scan chacun : six semaines
   n'ont jamais été numérisées.
6. **Dossier de révision** — sur le chantier remis : la gorge des soudures
   d'angle n'est écrite sur aucun mode opératoire, et les deux numérotations du
   cahier de soudure divergent. Laissé en l'état sur décision, à reprendre pour
   les prochains.

## Fait — septembre 2026

- **Qualification soudeur** : 44 certificats dépouillés, tableau vérifié, `QS/`
  harmonisé (38/38), un soudeur sorti archivé.
- **Rapport hebdo** : 3 semaines saisies (~80 fiches), récap et suivi « qui doit
  sa fiche » ; scans réorganisés (369 pages, 15 fichiers, 0 anomalie).
- **DMOS/QMOS** : tableau mis à jour pour la première fois depuis 2023.
- **Essai de pression** : volume, critère d'épreuve, lecture manomètre → skill.
- **Boîte mail** : inbox vide, 20 règles de filtrage sur domaine, archives de
  1 993 à 1 618, référentiel publié dans `modules/gestion-boite-mail/`.
- **Essai de pression** : protocole produit, bloqué par les deux contre-pouvoirs
  puis corrigé → module `essai-de-pression`.
- **Dossier de révision** : un dossier monté et remis → module + skill + agent.
- **Module** : 16 agents, 4 skills, 3 commandes, 6 modules.
