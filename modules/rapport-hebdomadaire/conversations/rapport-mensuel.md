---
conversation: Rapport mensuel TSI à partir des fiches hebdomadaires
date_source: 2026-09-12
verse_le: 2026-09-12
source: "iCloud/TSI-new/09 Dossier personnel/Thomas/rapport hebdo/prompt_claude_code_septembre_2026_v2.md"
caviarde: true
---

> ⚠️ **Version caviardée.** Ce dépôt est public. Les **noms complets**, les **données
> de santé** (arrêts maladie, chômage technique) et les **dates de sortie** ont été
> retirés du prompt d'origine. Seuls les **noms d'onglet** sont conservés.
> L'original intégral reste dans iCloud, à l'emplacement indiqué ci-dessus.
> La correspondance onglet ↔ nom complet se lit dans `collaborateur.xlsx`, hors repo.

# Prompt d'origine — caviardé

```text
# Rapport mensuel TSI — septembre 2026 (v2, 12.09.2026)

## CONTEXTE & MISSION
TSI SA (Tuyauterie et Soudures Industrielles SA), Ecublens (Vaud) — tsi-sa.ch
Chauffage à distance, obturations en charge, direction de travaux tuyauterie.
DMOS TIG/141, matériau P235GH (DN 88.9 / 114 / 273).

Chaque collaborateur reçoit une fiche hebdomadaire imprimée, la remplit à la main
(heures et frais), et la rend. Mission : tenir à jour rapport_<mois>_<année>_vN.xlsx
à partir de ces fiches scannées en PDF — 1 fiche = 1 collaborateur × 1 semaine.

Fichier de travail courant : Claude/rapport_septembre_2026_v2.xlsx. Ne jamais
repartir d'un template vierge ni recréer le mois : ouvrir la version vN la plus
haute, compléter, sauver en vN+1.

## ÉTAT AU 12.09.2026
- Fichier de septembre en v2, cloné de rapport_juillet_2026.xlsx.
- Structure : onglet « Recap septembre 2026 », puis les onglets de suivi
  hebdomadaire, puis 36 onglets collaborateurs classés alphabétiquement.
- Semaine du 31.08 → 04.09 saisie (onglet 31.08.26). 31 fiches exploitables sur
  34 pages scannées (3 versos).
- C44 = 174.5 h sur les 36 onglets : le contrôle du total théorique passe.

### Arbitrages déjà tranchés — ne pas rouvrir
1. Lundi 31.08.2026 appartient à août : heures abandonnées. Il n'existe aucun
   rapport d'août et on n'en crée pas. Seuls Ma 01 → Ve 04.09 ont été repris.
2. Reports de juillet : G12 = G44 juillet et H12 = H44 juillet, bien que juillet
   ne couvre que 2 semaines sur 5 et qu'aucune semaine d'août n'ait été saisie.
   Les soldes de départ de septembre sont approximatifs — c'est assumé.
3. Périmètre : fonctions techniques uniquement.

### Reste ouvert
- Huit collaborateurs n'avaient pas d'onglet en juillet, donc aucun solde à
  reprendre : Brahna, Carvalho, Graca, Jones, Nélio, Petit Tiago, Ricardo, Santos.
  Leur H12 est vide. Conséquence : H44 négatif pour Carvalho (−3) et Nélio (−1).
  Ne pas mettre 20 à la place — demander les soldes réels au 31.08.
- Un collaborateur n'a aucune fonction dans collaborateur.xlsx : hors périmètre
  pour l'instant.

## PÉRIMÈTRE
Source : collaborateur.xlsx, onglet « en-service », colonne Fonction.
Retenus : Monteur · Monteur-soudeur · Soudeur · Aide-monteur · Contremaître.
Écartés : Directeur, Directrice administrative, Assistante administrative,
Chargé d'affaires, Assistant technico-administratif, Conducteur de travaux,
Technicien en tuyauterie.
Écartés aussi : toute Date de sortie antérieure au 1er septembre 2026.

À ce jour : 36 collaborateurs, un onglet chacun.

[TABLE DES 36 ONGLETS — noms complets retirés, voir collaborateur.xlsx]
Antonio · Barros · Brahna · Bruno · Calinas · Cardoso · Carlos · Carvalho ·
Diego · Fabio · Graca · Jesus · Jones · Juan · Levi · Luis · Mag · Marcelo ·
Marcio · Marco · Mario · Martins · Mathias · Nélio · OMAR · Osmar · Paulo ·
Pedro · Petit Tiago · Ricardo · Ruben · Rui · Santos · Sergio · Tiago · Zé

Fonctions : Contremaître = Mag, Nélio, Paulo. Soudeur = Fabio, Graca, Jesus,
Mario. Monteur-soudeur = Bruno, Calinas, Juan, Levi, Marcelo, Ruben, Rui,
Santos, Tiago. Monteur = Antonio, Barros, Cardoso, Carvalho, Jones, Osmar,
Pedro, Zé. Aide-monteur = les autres.

[SORTIS — noms et dates retirés, voir collaborateur.xlsx]

## CALENDRIER SEPTEMBRE 2026 (30 jours)
Mapping ligne ↔ jour : row = 12 + numéro_du_jour → jour 1 = ligne 13, jour 30 = 42.
Ma 1 · Me 2 · Je 3 · Ve 4 · Sa 5 · Di 6 · Lu 7 · Ma 8 · Me 9 · Je 10 · Ve 11 ·
Sa 12 · Di 13 · Lu 14 · Ma 15 · Me 16 · Je 17 · Ve 18 · Sa 19 · Di 20 ·
Lu 21 (Jeûne fédéral) · Ma 22 · Me 23 · Je 24 · Ve 25 · Sa 26 · Di 27 · Lu 28 ·
Ma 29 · Me 30.

C = 8.5 du lundi au jeudi · 7.5 le vendredi · vide samedi et dimanche ·
0 le lundi 21. La ligne 43 est vide (30 jours) ; la ligne Total reste en 44 et
les formules restent en SUM(x13:x43).
Total théorique du mois, hors férié du 21 : 174.5 h — contrôle de C44.

### Onglets de suivi hebdomadaire (format JJ.MM.AA), après le Recap
- 31.08.26 — fait (seuls Ma 01 → Ve 04.09 saisis)
- 07.09.26 — Lu 07 → Ve 11
- 14.09.26 — Lu 14 → Ve 18
- 21.09.26 — Lu 21 → Ve 25 (Lu 21 = Jeûne fédéral)
- 28.09.26 — Lu 28 → Me 30 (les 1er et 2 octobre iront dans le rapport d'octobre)

### Fériés Vaud 2026 — reste de l'année
Lu 21/09 Jeûne fédéral · Ve 25/12 Noël. En cas de doute sur un férié cantonal,
demander.

## RÈGLES ABSOLUES DE SAISIE (aucune exception)

### Structure d'un onglet collaborateur
A = jour de la semaine (ne pas toucher) · B = numéro du jour (ne pas toucher) ·
C = heures normales (valeurs fixes) · D = heures effectives (lues sur la fiche) ·
E = frais repas · F = frais déplacement · G = différentiel =Dn-Cn (formule, écrite
uniquement sur les jours saisis) · H = jours d'absence décomptés (1 par jour) ·
I = libellé / remarque.

G12 = report heures sup · H12 = solde vacances de départ · ligne 44 = totaux :
C44=SUM(C13:C43) · D44=SUM(D13:D43) · E44=SUM(E13:E43) · F44=SUM(F13:F43) ·
G44=G12+SUM(G13:G43) · H44=H12-SUM(H13:H43)
C5 porte « <Mois> <Année> — Nom complet (Fonction) ».

### Heures (C et D)
- C = valeurs fixes. Ne JAMAIS modifier C sur un jour ouvré standard.
- D = le total d'heures NOTÉ sur la fiche, pas le calcul des horaires de présence.
  C'est la règle qui tranche le cas fréquent d'un départ à 6h00 ou 6h30 avec un
  total noté de 8.5 : le trajet n'est pas compté, il est couvert par le
  déplacement (frais 105). Ne « corriger » jamais le total noté.
- Quand un total est barré et remplacé à la main, retenir le chiffre NON BARRÉ
  et le signaler en colonne I.

### Frais de repas (E)
- 25 CHF fixe par jour travaillé.
- EXCEPTION : deux collaborateurs (onglets Paulo et Pedro) = 50 CHF/jour
  travaillé, même s'ils n'ont rien noté.

### Frais de déplacement (F)
F = montant total noté − frais repas (25 ou 50), et vide si ≤ 0.
25 → E=25, F=vide · 65 → E=25, F=40 · 105 → E=25, F=80 · 145 → E=25, F=120
Paulo/Pedro : 105 → E=50, F=55 · rien de noté → E=vide, F=vide

### FÉRIÉ / CONGÉ OFFERT TSI / JEÛNE FÉDÉRAL → neutre
C=0 · D=0 · E et F vides · PAS de H=1 · I = libellé.
TSI ne doit rien, le salarié ne doit rien.

### CONGÉ / VACANCES / MALADIE / ARRÊT TRAVAIL → différentiel négatif + décompte
C=8.5 (Lu-Je) ou 7.5 (Ve) — pas 0, pas vide · D=0 · E et F vides · H=1 ·
I = libellé exact : Congé · Vacances · Congé maladie · Arrêt travail.
Le salarié « doit » ses heures, et le solde de 20 j/an est décompté.

### Travail le week-end
Samedi et dimanche ont C vide. Une heure travaillée y passe donc intégralement
en heure supplémentaire. Le signaler : la majoration du dimanche n'est pas tranchée.

## PROCÉDURE À CHAQUE RÉCEPTION DE FICHES
1. Convertir le PDF en images et les lire une par une. Les scans n'ont pas de
   couche texte. pdftoppm n'est pas installé sur ce Mac, mais PyMuPDF (fitz) l'est :
   page.get_pixmap(dpi=140).save(...) donne des PNG lisibles. Attendre des versos
   et des pages blanches : les ignorer, mais les compter.
2. Identifier chaque collaborateur (nom de la fiche → onglet).
   ⚠️ Sur beaucoup de fiches un nom imprimé est BARRÉ et remplacé à la main :
   toujours prendre le nom manuscrit non barré.
3. Ouvrir la dernière version vN du fichier du mois.
4. Créer l'onglet de suivi de la semaine s'il n'existe pas (copie du suivi
   précédent, statuts remis à zéro, titre mis à jour en A1).
5. Saisir pour chaque collaborateur selon les règles ci-dessus.
6. Mettre à jour l'onglet Recap : une colonne par semaine, statut Reçu / Manquant,
   et le compteur de fiches manquantes.
7. Sauvegarder en incrémentant la version (vN → vN+1). Ne jamais écraser.
8. Livrer : le fichier + un récapitulatif court + la liste des fiches manquantes
   + la liste des anomalies.

### Contrôles de cohérence systématiques avant livraison
- C44 = 174.5 pour tout collaborateur sans absence
- aucun E ou F rempli alors que D est vide ou nul
- aucun F aberrant (F=1 a déjà été vu deux fois : corriger en vide et le signaler)
- tout jour avec H=1 a bien C=8.5/7.5, D=0, E/F vides et un libellé en I
- le 21.09 a bien C=0, D=0 et PAS de H=1
- H44 ≥ 0 pour tout le monde — sauf Carvalho et Nélio tant que leur H12 est vide
- A43, B43, C43 vides (mois de 30 jours)
- les jours ouvrés sans fiche et sans libellé sont listés comme « à clarifier »,
  jamais laissés silencieusement à D vide

## PIÈGES DE LECTURE DES FICHES

### Noms barrés — prendre le manuscrit
Cas déjà rencontrés, exprimés en onglets : une fiche pré-imprimée au nom d'un
collaborateur est réutilisée par un autre. Corrections connues → Barros, Ruben,
Diego, Fabio. Confusion fréquente Luis ↔ Levi. Ruben reçoit souvent des feuilles
barrées d'autres onglets (Antonio, Martins, Osmar).

### Homonymies et variantes à ne pas confondre
- Osmar (monteur) ≠ OMAR (aide-monteur)
- Marco ≠ Mario
- Tiago ≠ Carvalho ≠ Petit Tiago ≠ Santos — quatre personnes distinctes
  (Tiago est appelé « Primo » dans collaborateur.xlsx)
- Brahna (onglet) = Branha dans collaborateur.xlsx
- Mathias (onglet) = Matias dans collaborateur.xlsx
- Mag ≠ Marcelo (patronyme proche)

### Cas particuliers connus
- Paulo et Pedro : repas 50 CHF/jour.
- Carlos : frais notés avec suffixe « FR » (25FR) → saisir le nombre seul.
  26FR = erreur d'écriture probable → 25 et F vide.
- Luis : heures de nuit à calcul complexe, indemnité soir (+100 CHF) — saisir le
  total d'heures et détailler en I.
- Rui : heures sup. avec indemnité soir ; travaille parfois à Fleurier ; peut
  avoir des « Congé offert TSI » individuels → demander confirmation ; a déjà
  travaillé un dimanche.
- Levi : modèle de fiche différent, avec colonnes Chantiers, 25 %, 50 %,
  Frais & km. Chantier Prilly.
- Mathias : congés en milieu de semaine ; chantiers Gland / Bulle / Genève (en I).
- Cardoso / Osmar / Mag / Mario / Petit Tiago / Santos / Brahna : déplacements
  lointains (65 = 25+40 · 105 = 25+80 · 145 = 25+120).

## NOTES TECHNIQUES PYTHON / OPENPYXL
- Cellules éditables : C, D, E, F, H, I uniquement. Ne pas écrire dans A, B, G
  (sauf la formule =Dn-Cn sur les jours saisis).
- Ne jamais écrire sur une MergedCell. Cas connu : A43:B43 →
  ws.unmerge_cells('A43:B43').
- Copier un onglet : wb.copy_worksheet(src) puis renommer et repositionner.
- Lire un fichier existant demande DEUX chargements : data_only=True donne les
  valeurs calculées, le chargement par défaut donne les formules. Ne jamais sauver
  un classeur ouvert en data_only=True : ça détruit toutes les formules.
- ⚠️ LibreOffice n'est pas installé sur ce Mac, donc recalc.py ne peut pas tourner.
  Les formules écrites par openpyxl n'ont pas de valeur en cache et se calculeront
  à l'ouverture dans Excel. Vérifier les totaux en recalculant soi-même en Python
  à partir des valeurs des cellules, et dire ce qui a été contrôlé.

## RÈGLES DE COMPORTEMENT
- Ne jamais deviner une donnée illisible : la lister et demander.
- Ne jamais modifier une saisie existante sans le signaler.
- Une version = une sauvegarde : toujours incrémenter vN.
- Répondre en français, avec un récapitulatif court : ce qui a été saisi, ce qui
  manque, ce qui est douteux.
- À la clôture du mois : contrôle final des H44 et des G44, puis préparer le mois
  suivant en reportant G44→G12 et H44→H12. Ne JAMAIS remettre H12 à 20 : les
  20 jours sont un droit annuel qui se consomme au fil des mois.
```

## Ce qui a été retiré du prompt d'origine

| retiré | pourquoi | où le retrouver |
|---|---|---|
| Les 36 noms complets (table onglet ↔ nom ↔ fonction) | données RH nominatives, dépôt public | `collaborateur.xlsx`, onglet `en-service` |
| Noms et dates des 3 collaborateurs sortis | idem | `collaborateur.xlsx` |
| Nom du collaborateur sans fonction renseignée | idem | `collaborateur.xlsx` |
| Mentions d'arrêt maladie et de chômage technique nominatives | données de santé / situation individuelle | prompt original dans iCloud |
| Noms complets dans les exemples de fiches barrées | données nominatives | prompt original dans iCloud |
