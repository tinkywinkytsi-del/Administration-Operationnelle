---
conversation: Procès-verbal de contrôle de chantier — V4
date_source: 2026-09-12
verse_le: 2026-09-12
---

# Prompt d'origine — collé tel quel

```text
Contexte : je suis Thomas Faedda, technologue en soudage et responsable de
l'exploitation chez TSI SA. Je réalise 3 contrôles de chantier par an, documentés
par un procès-verbal. Ce travail concerne TSI uniquement — aucun rapport avec le
projet ouvert, ne rien committer. Utilise les agents disponibles pour répartir le
travail (analyse, construction, revue) : personne ne valide seul son propre travail.

Dossier de travail :
iCloud/TSI-new/01 Chantier/Contrôle de chantier
(fichiers iCloud : force le téléchargement si les fichiers sont « dataless »)

Mission — améliorer « Procès-verbal-chantier.xlsx » en créant une COPIE
(original intact) :

1. ANALYSE D'ABORD : fais dépouiller les PV archivés dans « 00 Archive/ » (les plus
   récents en priorité) pour mesurer le taux de remplissage réel champ par champ.
   Supprime ce qui n'est jamais rempli, garde et renforce ce qui produit des
   remarques. Signale les anomalies de classement ou de versionnement au passage.

2. CONSTRUIS la V4 : très succincte, 2 pages A4 portrait MAXIMUM à l'impression
   (zone d'impression et saut de page définis). Page 1 = check-list remplissable
   sur place ; page 2 = suites du PV précédent + écarts/actions correctives
   (responsable, délai, soldé le) + observations libres. Reprends le logo TSI.
   Versionne honnêtement.

3. LIE LES SOUDEURS : la liste vient de
   iCloud/TSI-new/03 Collaborateur/Certificat professionnel/Qualification soudeur/
   certificat-qualification-soudeur.xlsx (feuille de l'année en cours).
   Pas de lien de formule entre fichiers iCloud (fragile) : feuille interne masquée
   + menus déroulants. Le choix nom + DMOS doit remplir seul le poinçon, le n° de
   qualification et la PROCHAINE CONFIRMATION SEMESTRIELLE ISO 9606-1 (pas la fin
   de validité à 3 ans). États explicites : « NON QUALIFIÉ », « requalif. avant
   [date] », « ÉCHUE » — jamais un blanc silencieux. Protège la feuille (sans mot
   de passe) pour que les formules ne soient pas écrasées. Ignore les lignes sans
   certificat ; recalcule les échéances depuis la date de soudage et signale tout
   écart avec la source au lieu de recopier une valeur douteuse.

4. REVUE OBLIGATOIRE avant remise : fais relire le fichier et le script par un agent
   relecteur ; corrige les bloquants et repasse la revue jusqu'à approbation.

5. ERREURS SOURCES : liste-moi les erreurs trouvées dans les fichiers sources. Ne les
   corrige que sur preuve (les certificats PDF font foi dans le dossier QS), avec
   copie de sauvegarde avant modification, et dis-moi ce que tu n'as pas pu trancher.

Dépose le fichier final dans le dossier de travail, à côté de l'original.
```
