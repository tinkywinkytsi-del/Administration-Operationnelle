# Conversation source — monter un dossier de révision

**Date** : 09.2026
**Objet** : constituer le dossier de révision d'un chantier de conduite
enterrée, à partir de deux dossiers de référence, et le remettre à l'entreprise
générale.

## Caviardage

| retiré | où le retrouver |
|---|---|
| nom du maître d'ouvrage, de l'entreprise générale, du laboratoire de contrôle | `TSI-new/07 Communication/Base Client/Base-clients.xlsx` |
| numéros et noms de chantiers | `TSI-new/01 Chantier/Client/<client>/` |
| poinçons, noms et n° de certificat des soudeurs | `TSI-new/03 Collaborateur/Certificat professionnel/` |
| numéros de DMOS, de QMOS et de CTG | `TSI-new/01 Chantier/DMOS : QMOS/` et le dossier CTG du client |
| pièces du dossier (cahier, isométrie, rapports, certificats) | dossier du chantier |

Seule la méthode est conservée. Aucune valeur de chantier, aucune référence de
document contractuel.

---

## Le déroulé, et ce qu'il a appris

### 1. L'arborescence ne s'invente pas
Deux dossiers de référence ont été relevés avant de commencer. Puis le
dépouillement des courriels a montré que l'entreprise générale avait **écrit
noir sur blanc** quelle arborescence elle voulait — celle d'un chantier
précédent. La question était donc déjà répondue dans la boîte mail : il suffisait
d'y regarder avant de choisir.

### 2. Le dépouillement des courriels est une étape du montage
Le fil du chantier a fourni, en une passe :
- la **validation de l'essai de pression**, qui n'existait nulle part ailleurs —
  pas de procès-verbal signé, juste une phrase dans un message ;
- la confirmation de **quel jeu d'enregistrements était le bon**, un envoi
  précédent ayant mélangé deux séries ;
- la preuve que **le cahier de soudure avait déjà été transmis** plusieurs semaines
  plus tôt — décisif, puisqu'il a ensuite fallu le corriger ;
- la vérification que **tous les certificats matière étaient classés**, en
  comparant les pièces jointes des courriels d'envoi au contenu du dossier.

### 3. Les recoupements attrapent ce que l'œil ne voit pas
- Les **numéros de série des manomètres** lus dans les rapports d'essai ont
  confirmé que les certificats d'étalonnage déjà au dossier du matériel étaient
  bien les bons : mêmes instruments. Sans ce recoupement, c'était une copie au jugé.
- Le **nombre de pièces spéciales** au cahier, comparé au nombre de lignes des
  rapports de contrôle, a révélé **des soudures contrôlées par le laboratoire et
  absentes du registre**. Le compte tombait juste : autant de pièces que de
  cordons.
- Les **épaisseurs des certificats matière**, comparées à la plage du mode
  opératoire, ont montré que celui-ci était écrit pour **une épaisseur nominale
  unique** alors que le chantier en comportait plusieurs.
- Les deux numérotations internes du cahier ne concordaient pas entre elles : des
  doublons et des couples transposés.

### 4. Ce qui a été corrigé, et à quelles conditions
Un soudeur était porté au cahier sur une partie des joints alors qu'il n'avait pas
soudé : **erreur de saisie**, affirmée explicitement par le porteur. La
correction était donc légitime — elle rétablissait ce qui s'était passé.

> ⛔ **La demande initiale avait été refusée.** Elle était formulée comme « mets
> l'autre poinçon partout », dans un contexte où la qualification du premier
> semblait insuffisante. Modifier un registre de traçabilité pour le faire
> coïncider avec une pièce justificative, ce n'est pas corriger, c'est falsifier
> — et le document était déjà chez le client. Ce n'est qu'une fois établi que le
> soudeur n'avait effectivement pas soudé que la correction a été faite.
>
> La règle qui en sort : **c'est la réalité du chantier qui tranche, jamais le
> document le plus facile à changer.**

### 5. Le contre-pouvoir métier a corrigé deux conclusions
L'agent `soudure` a établi, pièces à l'appui, deux choses que l'analyse de
surface avait ratées :
- **une épreuve bout à bout ne qualifie pas la soudure d'angle** : le champ du
  certificat qui affiche « les deux » n'est pas le discriminant, c'est le champ
  « complément de soudure d'angle » qui décide. Le certificat initialement
  retenu ne couvrait donc rien de ce chantier ;
- **un QMOS issu d'une épreuve bout à bout n'accorde aucune plage de gorge**, et
  c'est la gorge qui gouverne un mode opératoire de soudure d'angle.

Il a aussi trouvé qu'un mode opératoire adapté **existait déjà en modèle**, jamais
exporté. Le porteur a finalement retenu l'autre — sa décision, tracée comme telle
avec la réserve du module.

### 6. Le rapport de fin de travaux
Une page : objet, affaire, entreprise, et la déclaration de respect des normes et
des règles de l'art. **C'est une attestation** : elle se prépare, elle ne se
signe pas à la place de celui qui l'endosse.

---

## Outillage — ce qui a coûté du temps

**Excel et Word refusent d'écrire un PDF dans un dossier iCloud.** Erreur de
paramètre à chaque tentative, alors que l'ouverture du fichier source fonctionne.
Il faut écrire dans un dossier local puis déplacer. Trois tentatives perdues
avant de comprendre.

**Le verbe AppleScript est `save workbook as`**, pas `save as` — ce dernier
renvoie la même erreur de paramètre, ce qui brouille le diagnostic.

**openpyxl détruit les zones d'impression** d'un classeur formaté. Un classeur de
production se corrige en **patchant le XML** du `.xlsx`, ce qui préserve tout le
reste octet pour octet. Attention à ne jamais remplacer une chaîne partagée
globalement : la même valeur sert souvent dans plusieurs colonnes.

**Un export Excel emporte tous les onglets**, y compris les onglets de calcul
internes qui n'ont rien à faire dans un document client. Comparer le nombre de
pages à la version d'origine.

**Un dossier a disparu du dossier de révision en cours de montage** — supprimé
par le porteur, qui n'en voulait pas. Le réflexe de le recréer était mauvais :
avant de rétablir quelque chose qui a disparu, demander.
