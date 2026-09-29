---
conversation: Remplissage du PHS d'un chantier CAD
date_source: 2026-09-16
verse_le: 2026-09-29
extrait_vers: []   # aucun agent PHS n'existe encore — voir « Ce qui reste à faire »
---

# Remplissage du plan d'hygiène et de sécurité (PHS) d'un chantier

> ⚠️ **Archivée caviardée.** Personnes et coordonnées retirées : voir le tableau
> en fin de fichier. Les sociétés, les rôles et les chemins sont conservés — ce
> sont eux qui portent la procédure.

## Contexte

Le génie civil d'un chantier CAD avait remis son PPS (formulaire BST/SSE, art. 4
OTConst). TSI devait produire **son** PHS à partir du template maison
`01 Chantier/Sécurité/_phs_fr.docx`, en Word modifiable, avec la consigne
explicite de **signaler les doutes plutôt que de les combler**.

La conversation a duré une session et a produit : le `.docx` rempli, un code
couleur sûr/douteux, puis une version propre et un PDF. Elle a aussi mis au jour
des pièges techniques du template et une question contractuelle non résolue.

---

## LE PROMPT

> Réutilisable tel quel pour n'importe quel chantier. Remplacer `<AFFAIRE>` et
> `<DOSSIER>`.

```text
Remplis le PHS de TSI pour le chantier <AFFAIRE>.

DOSSIER DU CHANTIER
<DOSSIER>
Tu as accès à tout le dossier. Le PPS du génie civil, s'il existe, est dans PHS/.

TEMPLATE
01 Chantier/Sécurité/_phs_fr.docx — 42 variables entre crochets.
La liste exhaustive des 42 est dans 01 Chantier/Sécurité/phs-variable.xlsx.
Sortie : <DOSSIER>/PHS/phs_<AFFAIRE>.docx (convention : phs_<n° affaire>.docx).

RÈGLE ABSOLUE — LA PIÈCE FAIT FOI
Ne remplis une variable que si un document la donne. Si aucune source ne la
donne, LAISSE LE TOKEN [entre-crochets] EN PLACE : un champ vide se retrouve,
une valeur inventée ne se retrouve pas. Ne déduis jamais une adresse e-mail
d'une convention de nommage, même vérifiée sur dix adresses : les gens ont des
noms composés et ça tombe à côté.

CODE COULEUR
- NOIR (000000) : valeur sourcée ou consigne explicite de l'utilisateur.
- ROUGE (FF0000) : doute — valeur déduite, sources contradictoires, ou token
  laissé vide.
À chaque livraison, liste ce qui est rouge et POURQUOI, une ligne par entrée.

ORDRE DE PRIORITÉ DES SOURCES
1. Contrat d'entreprise signé (SIA 1023) + ses annexes — maître d'ouvrage,
   direction des travaux, objet, dates contractuelles, montant.
2. PPS du génie civil — raison sociale GC, conducteur de travaux (Bauführer),
   contremaître (Polier), chargé de sécurité (SiBe). Les valeurs sont dans les
   CHAMPS DE FORMULAIRE du PDF, pas dans le texte : extrais-les avec
   page.widgets() (PyMuPDF), sinon tu ne vois que des cases ☐ vides.
3. Planning d'exécution du GC — dates réelles, effectifs et engins présents.
4. PV et relevés de séance de chantier — les plus récents priment.
5. Cahier d'appel d'offres — répartition des prestations entre lots.
6. Boîte mail — signatures. Voir plus bas.
7. Un PHS déjà rempli d'un chantier comparable — pour les conventions maison
   (format de date JJ.MM.AA, formulation de l'hôpital, du secouriste, etc.).
Cherche les PHS existants avec : find "01 Chantier" -iname "phs*.docx"

BOÎTE MAIL
Les téléphones et e-mails des intervenants sont dans la boîte, pas dans le
dossier. Procédure et scripts :
/Users/thomasfaedda/kDrive/mail_lecture_thomas/PROMPT_CONNEXION_IMAP.md
LECTURE SEULE, sans exception : select(..., readonly=True) et BODY.PEEK.
Ne retiens un numéro que s'il figure dans un message ENVOYÉ par la personne et
AVANT la première citation — donc dans sa propre signature.

TECHNIQUE — PIÈGES DU TEMPLATE, DÉJÀ PAYÉS
- Les 42 tokens sont TOUS éclatés sur plusieurs runs par le correcteur
  orthographique : « [nom-gc] » vaut ['[nom','-','gc',']']. Un remplacement
  run par run ne trouve jamais rien. Il faut concaténer le texte du paragraphe,
  chercher dedans, puis reposer la valeur sur l'intervalle de runs concerné.
- Pose la valeur dans un RUN NEUF qui clone le rPr du run d'origine, et colore
  ce run-là seulement. Sinon la mise en forme saute.
- Le suffixe (ce qui suit la valeur dans le même run) doit cloner le rPr
  D'ORIGINE, surtout pas celui du run qu'on vient de colorer : sinon le rouge
  déborde sur le texte du template qui suit.
- Après coup, retire la couleur des runs qui ne contiennent que des blancs
  (\t, \n) : sinon ce que l'utilisateur tapera à côté ressortira rouge.
- Ne touche JAMAIS sec.first_page_header / even_page_header avec python-docx :
  le simple accès les CRÉE, et Word affiche ensuite un en-tête vide en page 1.
  Ne parcours que sec.header / sec.footer, et seulement si
  is_linked_to_previous est faux.
- Certains noms sont ÉCRITS EN DUR dans le template, pas en variables
  (conducteur de travaux TSI, coordination sécurité, contrôle des mesures de
  sécurité). Si la personne change, il faut les remplacer par contexte de
  paragraphe, pas par token.

CONTRÔLE AVANT DE LIVRER — les trois, à chaque fois
1. zipfile.ZipFile(sortie).namelist() == celui du template. Toute entrée en
   plus trahit une modification structurelle involontaire.
2. Même nombre de paragraphes que le template.
3. Aucun run rouge ne contient du texte du template.
Annonce les trois résultats.

TABLEAU DES RISQUES (section 6)
Le template arrive pré-rempli d'un chantier générique. Relis-le contre la
réalité et SIGNALE les contradictions, sans les corriger de ton chef :
requalifier un risque est une décision de l'utilisateur. Contradiction la plus
fréquente : « Travaux routiers — heurts par des véhicules en circulation : Non »
alors que le PHS déclare deux pages plus haut que le chantier empiète sur la
voie publique. Quand une ligne passe à Oui, le format impose les trois lignes
Etape / Mesure / Responsable.

PDF
Word refuse « save as » en AppleScript sur ce Mac (erreur -1708, deux syntaxes
essayées). Pages fonctionne mais RECOMPOSE : 24 pages Word deviennent 26. Si la
pagination compte, dis à l'utilisateur de faire Fichier > Enregistrer sous >
PDF depuis Word, et ne présente pas le PDF Pages comme équivalent.

LIVRAISON
À chaque version : le fichier, le compte noir/rouge, la liste du rouge avec sa
raison, et ce qui reste à trancher. Aucune écriture hors du dossier chantier
sans validation.
```

---

## Ce qu'on en retient

**Sur la méthode.** Le gain n'est pas d'avoir rempli 42 cases : c'est d'avoir
maintenu la distinction entre *sourcé* et *déduit* jusqu'au bout. Le code
couleur a servi de mécanisme de validation point par point — l'utilisateur a
tranché une entrée à la fois, et chaque arbitrage a fait passer un rouge en noir.

**Sur la déduction.** Une adresse e-mail a été déduite d'une convention de
nommage vérifiée sur onze adresses réelles de la même société. Elle était
fausse : la personne a un nom composé et son adresse reprend le nom entier. La
vraie adresse est apparue plus tard dans un mail. **La convention de nommage
n'est pas une source.**

**Sur les sources qui se contredisent.** Trois dates de début de chantier
coexistaient — contrat, planning d'exécution, PV de séance. Aucune n'était
fausse ; elles répondaient à des questions différentes. Ce genre d'écart se
présente à l'utilisateur, il ne se résout pas par « la plus récente gagne ».

**Sur le PPS du génie civil.** C'est un PDF à champs de formulaire. Le texte
extrait ne montre que des cases vides ; les valeurs saisies sont dans les
widgets. Sans `page.widgets()`, on conclut à tort que le PPS est vierge.

**Sur l'accès aux données.** Une heure a été perdue à tenter de brancher
l'extension Chrome pour lire le webmail, alors qu'une connexion IMAP en lecture
seule existait déjà, documentée et scriptée, hors du dépôt. **Chercher la
procédure existante avant de monter un accès.**

---

## Question contractuelle laissée ouverte

Elle dépasse le PHS et mérite son propre traitement :

> **Qui descend les tuyaux en fouille — le génie civil ou TSI ?**

- La **série de prix Hydraulique** de l'appel d'offres met, dans le chapitre
  « Installations de chantier », « le levage et la mise en place des conduites
  et des pièces de forme » **à la charge du lot hydraulique**.
- L'**offre TSI**, en format maison, ne comporte **aucune** position
  d'installation de chantier ni de moyen de levage — seulement « mise en place
  et pointage » sur chaque pièce.
- Les **conditions générales** prévoient que toute position laissée vide est
  réputée **incluse**, et les **conventions particulières** excluent
  expressément les travaux en régie.
- Mais le **planning d'exécution du GC**, postérieur au contrat, attribue
  « excavation et **mise en fouille des conduites** » au génie civil.

À clarifier par écrit avec la direction des travaux avant l'arrivée des gros
diamètres. Un relevé de séance a par ailleurs acté « longueur de travail de
fouille pour TSI, env. 40 m » sans dire qui fournit l'engin de levage.

---

## Ce qui reste à faire

- [ ] **module `phs`** — ce sujet n'a pas de module. Il en mérite un :
      `modules/phs/`, avec cette conversation dedans et le prompt ci-dessus
      comme base de skill.
- [ ] **agent `phs`** — périmètre : plan d'hygiène et de sécurité d'un chantier,
      à partir du template maison, du PPS du GC et des pièces contractuelles.
- [ ] **skill `remplir-phs`** — les pièges techniques du template (runs éclatés,
      en-têtes, couleurs) sont une procédure, pas une connaissance de contexte.
- [ ] **règle dans `contexte-partage/`** — « une convention de nommage n'est pas
      une source » vaut bien au-delà du PHS.

---

## Ce qui a été caviardé

| retiré | remplacé par | où le retrouver |
|---|---|---|
| Nom et coordonnées du chef de projet du maître d'ouvrage | « le chef de projet MO » | PHS du chantier, contrat SIA 1023 |
| Nom et coordonnées du conducteur de travaux du GC | « le conducteur de travaux GC » | PPS du GC, dans `PHS/` |
| Nom et coordonnées du contremaître du GC | « le contremaître GC » | PPS du GC, champ *Polier* |
| Nom et coordonnées de la chargée de sécurité du GC | « le chargé de sécurité GC » | PPS du GC, champ *SiBe* |
| Nom et coordonnées de l'ingénieur civil / DT | « la direction des travaux » | contrat SIA 1023, page 1 |
| Noms des collaborateurs TSI cités (direction, chargé d'affaires, contremaître) | rôle seul | `03 Collaborateur/collaborateur.xlsx` |
| Nom et coordonnées du responsable du sous-traitant manchonnage | « le sous-traitant manchonnage » | facture du sous-traitant, dossier chantier |
| Noms des interlocuteurs fournisseurs | société seule | boîte mail, dossier du chantier |
| Tous numéros de téléphone et adresses e-mail | — | boîte mail et PPS |

Les **raisons sociales**, le **n° d'affaire** et le **chemin du dossier** ont eux
aussi été retirés, bien que la règle 2 ne l'impose pas : le prompt gagne à être
générique, il sert pour n'importe quel chantier avec `<AFFAIRE>` et `<DOSSIER>`.
Le chantier d'origine se retrouve par la date `date_source` dans le `JOURNAL.md`
et dans `01 Chantier/Client/`.

Ne subsistent donc ici que des **rôles** et des **procédures** — rien qui
identifie une personne, une société ou un client.
