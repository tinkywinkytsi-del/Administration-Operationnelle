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

## Principe de classement — deux niveaux

L'arborescence **reproduit celle du classement papier/iCloud**, `01 Chantier/Client/<client>/`.
C'est délibéré : une seule logique à apprendre, et un collaborateur qui sait
ranger un dossier sait ranger un mail.

```
Client/                     <- un seul dossier parent, au singulier
    <Client>/               <- un dossier par donneur d'ordre récurrent
        <Chantier>/         <- un sous-dossier par affaire de ce client
<Thème>/                    <- les processus permanents restent à la racine
1- Archives/                <- ce qui est clos ou sans suite
```

**Le client prime sur la géographie.** Un chantier se classe sous le donneur
d'ordre qui le commande, pas sous le canton où il se trouve : c'est le client
qui paie, relance et réceptionne, donc c'est lui qui structure les échanges.
Un nom de chantier peut garder son préfixe géographique — il devient alors une
simple étiquette, plus un niveau de classement.

| famille | critère de création | où |
|---|---|---|
| **Client** | un donneur d'ordre qui revient | sous `Client/` |
| **Chantier** | une affaire qui génère des échanges suivis | sous son client |
| **Thème permanent** | un processus de l'entreprise, tous clients confondus | à la racine |
| **Archives** | ce qui est clos, ou ce qui ne demande rien | `1- Archives/` |

Un dossier se crée sur **du volume récurrent constaté**, jamais par anticipation.

## Cycle de vie d'un dossier de chantier

Un chantier se termine, son dossier ne se supprime pas : il **descend** en
sous-dossier d'archives. Ce déplacement est **manuel et décidé par Thomas** —
un agent ne clôt jamais un chantier de lui-même, parce que rien dans la
messagerie ne dit de façon fiable qu'un chantier est fini.

## Le geste, dans SmarterMail

| action | chemin |
|---|---|
| créer un dossier | bouton **dossier** en tête du volet des dossiers → *Nouveau Dossier* ; le champ **Dossier Parent** décide du niveau |
| déplacer un dossier | **clic droit** sur le dossier → *Déplacer le Dossier* |
| règles automatiques | *Paramètres* → *Filtrage de Contenu* |

⚠️ Deux pièges constatés :
- le menu **Déplacer le Dossier** propose `1- Archives` **par défaut** — valider
  sans changer la destination envoie le dossier aux archives ;
- déplacer un dossier **emporte tous ses messages**. C'est réversible, mais il
  faut le savoir avant de cliquer.

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

Étapes 1, 3 et 4 faites : l'existant est relevé, la structure à deux niveaux est
arrêtée et les dossiers clients sont créés, les chantiers déjà suivis y sont
rattachés.

Reste à faire, dans l'ordre :
2. **mesurer le stock** — quels expéditeurs font le volume, sur 3 mois ;
5. **trier le stock**, lot par lot, chaque lot annoncé avec son compte ;
6. **poser les règles de filtrage** pour que le flux futur se range seul ;
7. **vérifier** les comptes avant/après.

Points ouverts :
- un chantier reste à la racine, sans client rattaché ;
- la boîte occupe **82 % de son quota** — à surveiller avant que le serveur
  refuse le courrier entrant ;
- aucune règle de filtrage n'a été vue dans le compte ; à confirmer.
