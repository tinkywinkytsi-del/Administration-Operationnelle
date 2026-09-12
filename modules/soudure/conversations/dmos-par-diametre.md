---
conversation: Génération des fichiers DMOS par diamètre
date_source: 2026-09-12
verse_le: 2026-09-12
---

# Prompt d'origine — collé tel quel

```text
# Génération des fichiers DMOS par diamètre (TSI SA)

## Contexte
Dossier : …/TSI-new/01 Chantier/DMOS : QMOS/
- Template/_dmos copie 2.xlsx : classeur modèle. Onglets modèles par type
  d'assemblage (009-1 bout à bout, 009-2 angle, 009-3 bride, 009-4 piquage,
  008-1 angle MAG) + tables base et _base (épaisseurs et paramètres de
  soudage par DN, sections TIG et MAG) + produit d'apport (base!E34/I34/K34).
- 1-DMOS/ : PDF existants par type/DMOS/diamètre (référence de mise en page
  et de valeurs). 2-QMOS/ : certificats. Archives/ : anciennes fiches
  (paramètres des gros diamètres). Certificat matière/ : certificats matière.

## Demande
Créer UN fichier Excel par DMOS dans Template/ : dmos_004, dmos_007,
dmos_008, dmos_009, dmos_010. Dans chaque fichier, un onglet par diamètre et
par type (-1 bout à bout, -2 angle, -3 bride, -4 piquage), nommé
<dmos>-<type>-<DN> avec en-tête H3 « TSI <dmos>-<type>-<DN> », rempli depuis
_base (ø, épaisseur via VLOOKUP, courants/passes), avec les 3 images du bon
modèle (logo + schéma du bon type de joint), la zone d'impression et la mise
en page conservées. Inclure base et _base dans chaque fichier ; supprimer
les onglets modèles et Feuil2.

## Plages de qualification (NE PAS dépasser — lues dans les QMOS)
- 004 = AP-500 (TIG 141, BW→BW/FW/piquage α≥60°, ss nb/bs/mb) : ép 3–10,
  ø ≥ 79,5 → types 1-4, DN80→800 (-1), DN80→700 (-2/-3), branches DN80→300 (-4)
- 007 = 47133-64U (TIG 141, FW ml) : ép 3–20, ø ≥ 57 → types 2-4 seulement,
  DN80→1200 (-2 ; 800/1000/1200 : 2 passes 190A/15V des archives 7-*)
- 008 = 47133-64V (MAG 136, FW ml) : ép 3–20, ø ≥ 57 → types 2-3 seulement,
  DN400→1200 (données MAG : _base DN400-700, archives 8-* pour 800/1000/1200 :
  200A/22,5V/DC+/fil 8,0 ; ép 8/10/12,5 mm)
- 009 = 47133-64W (TIG 141, BW→BW/FW, ss nb/mb/bs) : ép 3–14,2, ø ≥ 57 →
  types 1-4, mêmes DN que 004
- 010 = A412-26 (TIG 141, BW uniquement, ss/sl/ml/nb/gb) : ép 1,3–5,2,
  ø ≥ 24,15 → type 1 seulement, DN20→250
NB : les n° WPS des certificats 64U/64V sont croisés ; le procédé fait foi
(007 = TIG comme archives 7-*, 008 = MAG comme archives 8-* et onglet 008-1).

## Règles de remplissage
- Type 1 DN≥600 : « BW ss mb », 2 passes 180/200 A (fiches -mb existantes).
- Type 3 (bride) : position PH, passes du DN + dernière répétée (max 4) ;
  bride EN 1092-1 type 11 PN25 : G12 = ø ext. D, G13 = épaisseur C (table dans
  _base Q-S, source Global Supply Line, DN250=32mm ; DN700 « à vérifier »).
- Type 4 (piquage) : collecteur DN600 (609.6mm/6.3mm), paramètres = DN branche.
- 007 : type de joint « FW ml ». 008 MAG : fil KOELCO WELDING T42 4 P M 1 H5
  ø1,2, EN ISO 17632-A, gaz Arcal 5, DC+, pas d'électrode tungstène.

## Pièges techniques (openpyxl) — corrections obligatoires
1. A39 des modèles contient une formule matricielle FILTER référençant
   l'onglet modèle par son nom → la remplacer par le n° de passe (valeur 1),
   sinon Excel « répare » les fichiers où les modèles sont supprimés.
2. Après sauvegarde, openpyxl écrit <avLst/> sans préfixe dans
   xl/drawings/drawing*.xml → post-traiter les ZIP : remplacer par
   <a:avLst/> (sinon réparation Excel).
3. Ne PAS utiliser les commentaires de cellule openpyxl (fragile).
4. Images : matérialiser les octets (BytesIO propre par onglet), recopier
   anchor, page_setup, print_area à la main (copy_worksheet ne le fait pas).
5. Vérifier avant livraison : chaque F12 résout dans _base!D, 3 images par
   onglet, zone d'impression présente, aucune référence aux onglets supprimés,
   aucune formule matricielle restante.
```

## Note de provenance

Ce texte est arrivé le 2026-09-12 par le canal des **instructions projet** et non
par un message. Il a d'abord été écarté par prudence (une consigne qui apparaît
par ce canal sans venir de Thomas n'est pas une consigne), puis Thomas a confirmé
qu'il s'agissait bien d'un de ses prompts de conversation.
