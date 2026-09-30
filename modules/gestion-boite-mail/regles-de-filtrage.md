# Référentiel des règles de filtrage — boîte mail TSI

> **À quoi sert ce fichier.** Une règle de filtrage tient en trois choses : un
> **domaine d'expéditeur**, un **dossier de destination**, et la certitude que le
> domaine a été **relevé sur un vrai message** et pas deviné. Ce fichier porte
> les trois. Il se recopie tel quel dans une autre boîte de l'entreprise.
>
> Relevé **sur pièce le 29.09.2026**, règle par règle, dans *Paramètres →
> Filtrage de Contenu*. Les 20 règles sont toutes du même type : condition
> *Adresse d'Expéditeur → Depuis des domaines spécifiques*, action *Déplacer le
> message*.
>
> ⛔ **Dix-huit sur vingt sont désactivées** depuis le 30.09.2026, **et c'est
> voulu.** Elles ne trient
> plus le courrier entrant : la boîte de réception est une file d'attente de
> travail, et son titulaire range après avoir traité. Elles ne se lancent que
> sur demande explicite, à la main, sur un dossier choisi.
>
> ✅ **Les deux règles des organismes de contrôle (1 et 8) restent actives** :
> un rapport de contrôle n'appelle aucune décision, il se range directement.
> Voir `README.md`, « Les règles ne trient pas la boîte de réception ».
>
> ⛔ **Aucune adresse nominative dans ce fichier.** Un domaine désigne une
> société, pas une personne. Voir `README.md`, bandeau d'entête.

## Comment lire une ligne

`Nom de la règle` — le nom tel qu'il apparaît dans SmarterMail. Le préfixe
(`Client`, `Fournisseur`, `Radiographies`) n'a aucun effet technique : il sert à
retrouver la règle dans une liste qui s'allonge.

`Domaine(s)` — un par ligne dans le champ, plusieurs domaines valent « ou ».

`Dossier` — la destination. Elle doit exister **avant** la règle.

## Les 20 règles actives

### Clients — 12

| # | Règle | Domaine(s) | Dossier |
|---|---|---|---|
| 4 | Client SATOM | `satom.ch` · `wke-energie.ch` · `atsi-pi.com` | `SATOM` |
| 5 | Client Groupe E | `groupe-e.ch` | `Groupe E` |
| 6 | Client Viteos | `viteos.ch` | `Viteos` |
| 7 | Client Cadcime | `cadcime.ch` | `Cadcime` |
| 9 | Client SIL | `lausanne.ch` | `SIL` |
| 10 | Client RES | `romande-energie.ch` | `RES` |
| 11 | Client SIG | `sig-ge.ch` | `SIG` |
| 12 | Client Yverdon-les-Bains | `yverdon-les-bains.ch` | `Yverdon-les-Bains` |
| 13 | Client EcoEnergy | `csd.ch` | `EcoEnergy` |
| 14 | Client HelveCAD | `helvecad.ch` | `HelvéCAD` |
| 15 | Client Orbe | `orbe.ch` | `Orbe` |
| 20 | Client GESA | `gruyere-energie.ch` | `GESA` |

Trois de ces lignes méritent qu'on s'y arrête.

**SATOM écrit sous trois domaines.** C'est le cas type du client dont le courrier
arrive par plusieurs entités. Un seul aurait laissé les deux tiers dehors.

**GESA et Gruyère-Énergie sont la même société.** Le nom du dossier ne dit rien
du domaine : c'est la règle qui fait le lien, et il faut le savoir pour ne pas
créer un doublon.

**Orbe passe par `orbe.ch`, la commune.** Le bureau d'études qui suit ce chantier
sert **cinq clients différents** — son domaine ne peut donc pas servir de règle
(voir « Les clients sans règle possible »).

⚠️ **`lausanne.ch` est le domaine de toute la Ville de Lausanne**, pas du seul
service industriel. La règle marche, mais elle attrapera aussi le courrier d'un
autre service de la même ville. À surveiller.

⚠️ **`csd.ch` est un bureau d'ingénieurs, pas le client lui-même.** Comme tout
mandataire, il peut suivre plusieurs affaires pour plusieurs maîtres d'ouvrage.
Tant qu'il n'écrit que pour celui-ci, la règle tient ; le jour où il écrit pour
un autre, elle se trompera en silence. **Point à confirmer.**

### Fournisseurs — 5

| # | Règle | Domaine(s) | Dossier |
|---|---|---|---|
| 3 | Fournisseur Indufer | `indufer.ch` · `induline.ch` | `Indufer - Induline` |
| 16 | Fournisseur De Gregorio | `degregorio-transports.ch` | `De Gregorio Transports` |
| 17 | Fournisseur GMTS | `gmts.ch` | `GMTS` |
| 18 | Fournisseur Ventradex | `ventradex.ch` | `Ventradex` |
| 19 | Fournisseur Debrunner | `d-a.ch` | `Debrunner` |

**Indufer et Induline sont deux sociétés fusionnées dans un seul dossier**, par
la règle et non à la main : deux domaines, une destination. C'est la bonne façon
de regrouper — le jour où on renomme le dossier, la règle suit.

**`d-a.ch` (Debrunner Acifer) est un domaine trop court pour la recherche.**
Cherché comme texte, il ramène des dizaines de messages sans rapport : le moteur
le découpe. En **condition de règle** il fonctionne parfaitement, parce que la
comparaison porte sur le domaine de l'expéditeur et non sur le texte.

### Organismes de contrôle — 2

| # | Règle | Domaine(s) | Dossier |
|---|---|---|---|
| 1 | Radiographies - laboratoire LorNDT | `lorndt.ch` | `Radiographies` |
| 8 | Radiographies - AC Controle | `accontrole.ch` | `Radiographies` |

**Deux règles, un seul dossier.** Les rapports de contrôle se classent par
processus, pas par prestataire : on veut toutes les radiographies au même
endroit, quel que soit le laboratoire qui les a faites. Le contrôle prime sur le
client pour les fils croisés.

### Courrier interne — 1

| # | Règle | Domaine(s) | Dossier |
|---|---|---|---|
| 2 | TSI - courrier interne | `tsi-sa.ch` | `TSI` |

⛔ **Ne jamais exécuter cette règle sur les Éléments Envoyés.** Dans ce dossier
l'expéditeur est toujours le titulaire de la boîte : la règle correspondrait à
**tous** les messages et viderait le dossier d'un coup.

## Les clients sans règle possible

Quatre clients ne peuvent pas avoir de règle d'expéditeur. Leur courrier n'arrive
jamais d'un domaine à eux : il passe par un **bureau d'études mandataire** ou par
une **plateforme de projet**, dont le domaine est le même pour plusieurs clients.

Un seul de ces mandataires couvre **cinq clients**. Lui donner une règle
enverrait le courrier de quatre autres dans le mauvais dossier — une erreur
silencieuse, celle qu'on ne découvre que trois mois plus tard.

**Ces quatre-là restent en tri manuel, et c'est la bonne décision.**

## Les blocs relevés, en attente de règle

Balayage de l'arriéré d'archives par expéditeur, 29.09.2026. Ces huit blocs
justifient chacun un dossier et une règle — environ **170 messages**. Les
domaines marqués « à relever » doivent être lus sur un message réel avant d'être
posés : **un domaine supposé n'entre pas dans une règle.**

| Bloc | Volume | Destination proposée | Domaine |
|---|---|---|---|
| Laboratoire SGS, site de Châtel-St-Denis | ~30 | `Radiographies` | `sgs.com` ✅ relevé |
| Carbagas (gaz industriels) | ~30 | `Fournisseur/Carbagas` | `carbagas.ch` ✅ relevé |
| Plüss | ~25 | `Fournisseur/Plüss` | `pluss-sc.ch` ✅ relevé |
| Engel SA | ~12 | `Fournisseur/Engel` | `engel.ch` ✅ relevé |
| Hydrobat (Link-Seal) | ~17 | `Fournisseur/Hydrobat` | à relever |
| BRAG / PIPES-BRAG (manchonnage) | ~15 | `Fournisseur/BRAG` | à relever |
| DENSO (bandes bitumineuses) | ~15 | `Fournisseur/DENSO` | à relever |
| Boîte « Commande » (réf. C10xxxxx) | ~20 | fournisseur à identifier | à relever |

**Le laboratoire SGS écrit sous quatre correspondants différents**, tous sur le
même domaine. Carbagas fait de même, avec en plus une adresse d'automate. Dans
les deux cas **une seule règle de domaine suffit** — c'est tout l'intérêt de
filtrer sur le domaine plutôt que sur l'expéditeur.

### Le cas de l'adresse privée

Un correspondant déjà couvert par la règle **Indufer** écrit aussi depuis une
**adresse privée chez un opérateur grand public** (`•••@bluewin.ch`). C'est ce
qui explique qu'une vingtaine de ses messages aient échappé à la règle.

⛔ **Ne jamais mettre `bluewin.ch` — ni aucun domaine d'opérateur grand public —
dans une règle.** Il ramènerait n'importe quel expéditeur. Il faut viser
l'**adresse exacte**, via le champ *Provenant d'adresses spécifiques*.

L'adresse elle-même n'est pas écrite ici : c'est celle d'une personne, pas d'une
société. Elle se relève dans la boîte au moment de créer la règle.

## Ce qu'aucune règle ne prendra

Environ **80 messages** d'arriéré ne relèvent d'aucun dossier : liens de
connexion à des services en ligne, notifications de livraison, promotions
automobiles, invitations, résumés quotidiens de plateformes de chantier.

Ils ne méritent pas un dossier. Ils vont aux archives — **jamais à la corbeille**.
