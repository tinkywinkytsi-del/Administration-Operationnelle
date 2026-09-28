# Module Gestion de la boîte mail

Tenir la boîte de réception **vide tous les jours**. Pas « à peu près rangée » :
vide. Un message qui reste en inbox est un message dont on ne sait pas encore
quoi faire — c'est le seul sens qu'on lui donne.

> ⛔ **Aucune donnée réelle de messagerie n'entre dans ce dépôt public.**
> Ni adresse, ni nom d'expéditeur, ni objet de message, ni nom de client, ni nom
> de chantier, ni numéro d'affaire. Ce README porte la **méthode** et les
> **conventions de nommage**. L'arborescence réelle vit dans la boîte, et nulle
> part ailleurs. Voir `contexte-partage/regles-tsi.md` §2.

## Le système de messagerie

Messagerie **SmarterMail**, hébergée chez **Swisscenter**, accès par webmail.
Ce n'est ni Microsoft 365 ni Gmail : les automatismes de ces plateformes ne
s'appliquent pas, et les règles se posent dans SmarterMail.

Deux leviers, à ne pas confondre :

| levier | quand il agit | ce qu'il règle |
|---|---|---|
| **Règles de filtrage** (côté serveur) | à l'arrivée de chaque message, pour toujours | le flux **futur** |
| **Tri de rattrapage** | une fois, sur ce qui est déjà là | le **stock** accumulé |

Poser des règles sans vider le stock laisse la boîte pleine. Vider le stock sans
poser de règles la laisse se remplir à nouveau la semaine suivante. **Les deux,
dans cet ordre : d'abord comprendre le stock, car c'est lui qui dicte les
règles.**

## Principe de classement

Un dossier se crée quand il y a **du volume récurrent**, pas par anticipation.
Trois familles :

| famille | critère | exemple de forme |
|---|---|---|
| **Affaire / chantier** | un chantier qui génère des échanges suivis | `<Canton>-<Chantier>` |
| **Thème permanent** | un processus de l'entreprise qui revient toujours | `Radiographies`, `Attestations`, `Appels d'offres` |
| **Archive** | ce qui n'est ni l'un ni l'autre et ne demande rien | `Archive` |

**Règle du canton en tête** pour les chantiers : le préfixe géographique regroupe
visuellement les affaires d'un même donneur d'ordre et rend la liste lisible
quand elle grandit.

## Cycle de vie d'un dossier de chantier

Un chantier se termine, son dossier ne se supprime pas : il **descend** en
sous-dossier d'`Archive`. Ce déplacement est **manuel et décidé par Thomas** —
un agent ne clôt jamais un chantier de lui-même, parce que rien dans la
messagerie ne dit de façon fiable qu'un chantier est fini.

## Ce qui ne se fait jamais sans validation explicite

Conformément à `contexte-partage/regles-tsi.md` §0 :

- **supprimer** un message — jamais, en aucun cas, même « manifestement inutile » ;
  ce qui ne sert pas va dans `Archive`, qui est réversible ;
- **envoyer** ou **répondre** à un message ;
- **créer ou modifier une règle de filtrage** — une règle agit sur tout le
  courrier futur, c'est la modification la plus lourde de conséquences ;
- **déplacer en masse** — chaque lot est proposé, chiffré et validé avant.

Créer un dossier vide est la seule action sans risque : elle n'affecte aucun
message.

## Méthode de mise en place

1. **Relever l'existant** — arborescence actuelle, volume de l'inbox, profondeur
   d'historique.
2. **Mesurer le stock** sur les 3 derniers mois : qui écrit le plus, sur quels
   sujets. On classe par volume décroissant, parce que **les dix premiers
   expéditeurs font l'essentiel du désordre**.
3. **Proposer l'arborescence** — et seulement les dossiers que le volume
   justifie.
4. **Créer les dossiers** validés.
5. **Trier le stock**, un lot à la fois, chaque lot annoncé avec son compte.
6. **Poser les règles de filtrage** pour que le flux futur se range seul.
7. **Vérifier** : compter l'inbox avant/après, s'assurer qu'aucun message n'a
   disparu — un message déplacé se retrouve, un message perdu ne se retrouve pas.

## État

Étape 1 en cours. Aucune arborescence n'est arrêtée à ce jour.
