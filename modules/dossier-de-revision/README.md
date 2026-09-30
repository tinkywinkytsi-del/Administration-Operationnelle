# Module Dossier de révision

Le **dossier de révision** — le DOE, dossier des ouvrages exécutés — remis au
maître d'ouvrage ou à l'entreprise générale à la fin d'un chantier. C'est la
**preuve de l'ouvrage exécuté** : qui a soudé, selon quel mode opératoire, avec
quelle matière, contrôlé comment, éprouvé à quelle pression.

Un dossier par chantier, et il y en a beaucoup. La structure ne s'invente pas à
chaque fois : **le destinataire demande souvent « la même arborescence que le
dossier précédent »**. Commencer par lui demander laquelle, ou la relever sur le
dernier dossier remis au même client.

## Conversation source
- [`conversations/dossier-revision-conduite-enterree.md`](conversations/dossier-revision-conduite-enterree.md)

## Skill
- [`skills/monter-dossier-revision`](../../skills/monter-dossier-revision/SKILL.md)
  — la procédure pas à pas, avec les techniques d'outillage.

---

## 1. La structure

```
01 Dossier de révision/
    Cahier de soudure/
    Certificat ISO/                 9001 et 3834-2
    Certificat matière:apport/      par fournisseur si le volume le justifie
    Certificat professionnel/       un certificat par poinçon ayant soudé
    Contrôle/
        Radio/                      rapports CND — MT, RT, PT
        Manchon/                    si réseau préisolé
        essai de pression/          protocole · enregistrements · étalonnages · validation
    DMOS:QMOS/                      le mode opératoire appliqué et son QMOS
    Isométrie/
    rapport-fin-travaux_<affaire>.pdf
```

**Ce qui n'y entre pas** : métré, plan d'hygiène et sécurité, plans d'exécution,
suivi de chantier, offres, confirmations de commande, planning, photos de
chantier. Le dossier de révision n'est pas l'historique commercial ni le journal
de chantier.

**Ce qui dépend du client** : un dossier d'attestations de l'entreprise
(attestations sociales, OCIRT, registre du commerce, RC). Certains l'exigent,
d'autres non. Demander plutôt que supposer.

---

## 2. La règle qui gouverne tout

> ⛔ **Le dossier ne doit contenir aucune pièce qui ne corresponde pas à ce qui a
> été exécuté.** Ni un certificat plus large que nécessaire « au cas où », ni un
> mode opératoire de la bonne famille mais de la mauvaise configuration, ni un
> jeu d'enregistrements dont on n'est pas sûr qu'il soit le bon.

Un dossier trop fourni n'est pas plus sûr : chaque pièce en trop est un point de
recoupement offert au maître d'ouvrage. **Une pièce, une justification.**

Corollaire : ⛔ **on ne modifie jamais un enregistrement pour le faire coïncider
avec une pièce justificative.** Si le cahier de soudure et le certificat ne
concordent pas, c'est la réalité du chantier qui tranche — pas le document le
plus facile à changer. Une correction n'est légitime que si elle rétablit ce qui
s'est réellement passé, et elle se signale au destinataire si le document est
déjà parti.

---

## 3. Les recoupements qui paient

Ce sont eux qui font la différence entre un dossier qui passe et un dossier qui
revient. Tous ont attrapé une vraie erreur au moins une fois.

| recouper | contre | ce qu'on y trouve |
|---|---|---|
| n° de série des manomètres du rapport d'essai | certificats d'étalonnage joints | un rapport produit avec un autre instrument rend les certificats sans objet |
| pièces jointes des courriels d'envoi | certificats matière classés | ce qui est arrivé par mail et n'a jamais été classé |
| nombre de pièces spéciales au cahier | nombre de lignes aux rapports CND | des soudures contrôlées et absentes du registre |
| poinçons du cahier | certificats disponibles, **aux dates de soudage** | un soudeur sans qualification couvrante |
| épaisseurs et matériaux des certificats matière | plage du mode opératoire | un mode opératoire qui ne décrit pas des soudures du chantier |
| les deux numérotations du cahier entre elles | rapports CND | doublons et transpositions |
| date d'un document déjà transmis | courriels d'envoi | une version corrigée qui contredit une version déjà chez le client |

**Le dépouillement des courriels du chantier fait partie du montage**, pas des
finitions. On y trouve la validation d'un essai, des certificats jamais classés,
des réserves à solder, et la confirmation de quelle version d'un fichier est la
bonne.

---

## 4. Ce qui manque presque toujours

- **La validation du maître d'ouvrage sur l'essai de pression.** Elle n'existe
  souvent que dans un courriel — « comme échangé au téléphone, nous validons ».
  C'est une pièce : l'imprimer en PDF avec son en-tête complet et la classer.
- **Les certificats d'étalonnage des manomètres**, qui vivent avec le matériel et
  non avec le chantier.
- **Les contrôles non destructifs de pièces spéciales** — coutures de fermeture,
  cordons longitudinaux — contrôlés par le laboratoire mais jamais portés au
  cahier de soudure.
- **La colonne « mode opératoire » du cahier de soudure**, laissée vide à la
  saisie.
- **La traçabilité d'un lot de matière** quand un certificat fournisseur couvre
  plusieurs nuances : rien ne dit laquelle a servi.

---

## 5. Contrôles obligatoires avant remise

- **`relecteur`** — un dossier de révision part chez un tiers : déclencheur de
  blocage du §4 de [`docs/ORGANISATION.md`](../../docs/ORGANISATION.md).
- **`gardien-confidentialite`** — le dossier sort du poste.
- **`soudure`** — toute question de plage de qualification ou de mode opératoire.
  Ce module **consomme** ce référentiel, il ne le corrige pas, et ne tranche
  jamais une lecture de norme à sa place.
- **`essai-de-pression`** — tout ce qui touche à l'épreuve hydraulique.

## 6. Règles dures
- ⛔ **Copier, jamais déplacer.** Les originaux restent à leur place.
- ⛔ **Sauvegarde horodatée avant toute correction** d'un document de production,
  conservée **hors** du dossier remis.
- ⛔ **Aucune donnée inventée**, et aucune valeur portée sur un document sans une
  pièce qui la soutienne. Une colonne vide se comble ; une référence fausse dans
  un DOE se retourne contre l'entreprise.
- Un document déjà transmis qui est corrigé est **renvoyé en disant qu'il
  remplace le précédent**.
- Le bordereau de travail interne **ne part pas** avec le dossier.
