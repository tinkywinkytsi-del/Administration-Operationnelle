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
| **Fournisseur** | qui **vend** ou **livre** : commandes, bons, factures, certificats matières | sous `Fournisseur/` |
| **Thème permanent** | un processus de l'entreprise, tous clients confondus | à la racine |
| **Archives** | ce qui est clos, ou ce qui ne demande rien | `1- Archives/` |

⚠️ **Un mandataire peut servir plusieurs clients.** Un bureau d'ingénieurs
n'appartient donc pas à un client une fois pour toutes : **c'est le message qui
décide, pas l'expéditeur**. Le critère est *qui est en copie* — les
destinataires d'un message trahissent le maître d'ouvrage concerné.

Conséquence : un lot trié sur le nom du mandataire doit être **re-vérifié
client par client** à l'intérieur de son dossier d'arrivée, en cherchant le
domaine de chaque client possible. Tant que la vérification n'est pas faite,
le rattachement est une hypothèse, pas un fait.

⚠️ **Fournisseur ≠ mandataire.** Un bureau d'ingénieurs écrit beaucoup — souvent
plus qu'un fournisseur — mais il **représente un maître d'ouvrage** : son
courrier appartient au client, pas à une catégorie « fournisseur ». On les
distingue à l'objet : *confirmation de commande, bon de livraison, certificat
matières* → fournisseur ; *nom de chantier, PV de séance, adjudication* →
mandataire d'un client.

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
| chercher par dossier + date | *Recherche Avancée* → portée **Courriel**, puis critères *Dossier* et *Reçu avant / après* |
| déplacer en masse | dans la liste : *Sélectionner* → *Tout Sélectionner*, puis menu **⋮** → *Déplacer* |
| renommer un dossier | **clic droit** → *Modifier le dossier* |

⚠️ Pièges constatés :
- le menu **Déplacer le Dossier** propose `1- Archives` **par défaut** — valider
  sans changer la destination envoie le dossier aux archives ;
- déplacer un dossier **emporte tous ses messages**. C'est réversible, mais il
  faut le savoir avant de cliquer ;
- le filtre de la liste ne connaît **aucun critère de date** — seulement lu/non
  lu, marqué, catégories ;
- la **Recherche Avancée** s'ouvre dans une **fenêtre surgissante** qu'un agent
  ne peut pas déclencher — les popups n'obéissent qu'à un clic humain. Elle est
  en revanche accessible directement par son adresse,
  `…/interface/root#/popout/email-search`, et de là pilotable ;
- ⛔ **la Recherche Avancée sait compter, pas déplacer.** Sur ses résultats,
  les seules actions sont *Ouvrir*, *Supprimer* et *Télécharger EML* — au
  clavier comme au clic droit. Aucun *Déplacer*. Elle sert donc à **établir un
  compte**, jamais à exécuter un tri de masse ;
- le champ de date est un `input[type=date]` segmenté qui **n'accepte pas la
  frappe simulée** : il faut écrire la valeur directement dans le formulaire.

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

## Le déplacement de masse — procédure vérifiée

La seule opération qui déplace des milliers de messages d'un coup, et la seule
façon de la contrôler.

1. **Relever les deux compteurs avant** : le dossier source et le dossier
   destination, chacun ouvert, chiffre lu en bas de la liste. Sans ces deux
   nombres, l'opération n'est pas vérifiable.
2. *Sélectionner* → *Tout Sélectionner*. L'en-tête affiche alors
   « N Sélectionné » : **c'est la confirmation que la sélection porte sur tout
   le dossier**, pas sur la page visible. Si le nombre ne correspond pas au
   compteur, on s'arrête.
3. Menu **⋮** → *Déplacer*.
4. ⛔ **Changer la destination.** Le dialogue propose par défaut le **premier
   dossier par ordre alphabétique**, jamais celui qu'on veut. Valider sans
   regarder envoie tout au mauvais endroit.
5. Relire la destination affichée, puis *Déplacer*. Une barre de progression
   suit l'opération — compter environ une minute pour 10 000 messages.
6. **Vérifier l'égalité** : `source avant − source après = destination après −
   destination avant`. Si elle ne tombe pas juste, le dire immédiatement.

⚠️ Le compteur de la source peut remonter juste après : ce sont les messages
**arrivés pendant l'opération**. C'est normal, et c'est une raison de plus de
relever les compteurs au dernier moment.

## ⛔ Le nombre affiché par la recherche n'est pas le nombre réel

Constat de terrain, contre-intuitif et coûteux si on l'ignore :

- une recherche annonce **N résultats**, « Tout Sélectionner » affiche
  « N Sélectionné » — et le déplacement en emporte **davantage que N** ;
- relancer la même recherche juste après ramène **encore des résultats**, parfois
  des centaines. Il faut répéter jusqu'à zéro, et **revérifier plus tard** :
  l'index de recherche est en retard sur la réalité de la boîte ;
- un « 0 élément » après un déplacement ne prouve donc **rien**.

> **Seuls les compteurs de dossiers font foi.** Le chiffre en bas de la liste,
> dossier par dossier, est exact. On contrôle un tri en vérifiant que la somme
> de tous les dossiers retombe sur le total de départ — pas en se fiant au
> nombre annoncé par une recherche.

Corollaire pratique : un tri par recherche se fait **jusqu'à épuisement**, et le
bilan se lit sur les dossiers.

## ⛔ Renommer un dossier : opération à ne pas enchaîner

Constat de terrain, à ne pas reproduire :

- après un premier renommage, **un second renommage du même dossier échoue** :
  le serveur répond « Could not find a part of the path … ». Le nom affiché et
  le nom du dossier sur le disque ont divergé, et plus rien ne les réconcilie
  depuis le webmail — ni un rechargement de la page ;
- un renommage **déplace le dossier dans l'ordre alphabétique** dès qu'il est
  validé. Les positions des dossiers suivants changent aussitôt.

> **Un renommage se fait par clic droit sur l'élément lui-même, jamais sur une
> position relevée dans une capture précédente.** Entre la capture et le clic,
> la liste a pu se réordonner : on renomme alors le voisin, et on ne peut plus
> revenir en arrière.

Si un dossier se retrouve avec un nom faux, **son contenu reste intact et
accessible** — seul le nom est à corriger, et cela peut demander l'hébergeur.

**Le contournement qui marche**, quand le renommage est définitivement refusé :
créer un dossier neuf au bon nom, y **déplacer tous les messages** de l'ancien,
vérifier le compte des deux côtés. Création de dossier et déplacement de
messages fonctionnent là où le renommage échoue. Il reste une coquille vide,
qui **occupe toujours son nom** — tant qu'elle existe, aucun autre dossier ne
peut le porter. Sa suppression revient à l'hébergeur.

## ⛔ L'ordre de tri décide du classement des fils croisés

Un message peut correspondre à deux critères : le laboratoire de contrôle
**et** le client. Il part dans le dossier du **premier lot exécuté**, pas dans
le plus pertinent.

Conséquence : un client dont toute la correspondance passe par des fils de
contrôle peut se retrouver **sans aucun message dans son dossier**, alors que
plusieurs dizaines le concernent — rangées ailleurs. Avant de conclure qu'un
client n'a pas de courrier, **chercher son nom dans les dossiers déjà remplis**.

Corollaire : on trie du **plus spécifique au plus général**, et on annonce
l'ordre retenu avant de commencer.

> **Arbitrage retenu — le contrôle prime sur le client.** Un message qui
> appartient à la fois à un fil de contrôle et à un client **reste dans le
> dossier thématique du contrôle**. On cherche ces documents par nature de
> pièce, pas par donneur d'ordre. Un dossier client peut donc légitimement
> paraître vide : son courrier de contrôle est ailleurs, et c'est voulu.

## ⛔ La recherche fouille le corps du message

Elle ne se limite ni à l'expéditeur ni à l'objet. Conséquence : **un terme court
ramasse tout ce qui le contient à l'intérieur d'un autre mot**.

Cas réel : le nom d'une ville de trois syllabes a ramené **861 messages** —
commandes de matériel, absences du bureau, notes informatiques — parce qu'il
se trouve dans *déci**sion***, *pres**sion***, *révi**sion***, *dimen**sion***,
*discus**sion***. Aucun ne concernait la ville.

> **Avant tout déplacement, on regarde l'échantillon, pas seulement le nombre.**
> Un compte élevé n'est pas une bonne nouvelle : c'est souvent le signe que le
> terme est trop court.

Un terme sûr est **discriminant** : un nom de société, un domaine, un nom composé.
Quand le nom d'une localité est ambigu, chercher plutôt le **nom du client** ou
son domaine. Cette règle vaut doublement pour les **règles de filtrage
automatiques** : une règle mal ciblée détourne du courrier sans que personne
s'en aperçoive.

⚠️ Piège inverse constaté : deux clients de cantons différents peuvent partager
une chaîne de caractères dans leurs noms de chantier. Le mot le plus long et le
plus spécifique gagne, et la règle la plus précise doit s'exécuter **en premier**.

## Créer une règle de filtrage — la marche à suivre

*Paramètres → Filtrage de Contenu → Nouveau.*

> ⛔ **Le piège qui bloque tout : les sections « Conditions » et « Actions »
> n'apparaissent qu'une fois la règle enregistrée une première fois.** Sur une
> règle neuve, le sélecteur de section ne répond pas — ce n'est pas un bug de
> l'affichage, c'est l'ordre imposé par l'outil.

Séquence qui fonctionne :

1. **Options** — donner un nom, puis **décocher « Activer »**. Une règle sans
   condition ni action est inerte, mais on ne laisse jamais une règle à moitié
   écrite en position active.
2. **Sauvegarder.** Les sections Conditions et Actions deviennent accessibles.
3. **Conditions → Nouveau.** Choisir *Adresse d'Expéditeur*, puis le champ
   **« Depuis des domaines spécifiques »**, comparaison *Correspond*, et saisir
   le domaine (un par ligne).
4. **Actions → Nouveau.** Choisir *Déplacer le message*, puis le dossier de
   destination. ⚠️ Le dossier proposé par défaut est **Boîte de Réception**.
5. Revenir à **Options**, **recocher « Activer »**, enregistrer.

> **Filtrer sur le domaine de l'expéditeur, jamais sur le corps du message.**
> C'est ce qui supprime d'un coup la classe d'erreurs la plus dangereuse — celle
> des termes courts trouvés à l'intérieur d'un mot.

Actions disponibles : supprimer, rebond, **déplacer**, ajouter une en-tête,
ajouter un texte au sujet. Conditions disponibles : adresse d'expéditeur,
mots ou phrases, adresse de destination, pièces jointes.

## Appliquer les règles au courrier déjà reçu

Clic droit sur un dossier → **« Exécuter le filtre de contenu »**. Cette entrée
reste grisée tant qu'aucune règle n'existe. Une fois les règles écrites, elle
range un dossier entier d'un coup : c'est **la bonne façon de traiter un stock**,
bien plus sûre que des dizaines de tris manuels.

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
2. **mesurer le stock** — quels expéditeurs font le volume ;
5. **trier le stock**, lot par lot, chaque lot annoncé avec son compte ;
6. **poser les règles de filtrage** pour que le flux futur se range seul ;
7. **vérifier** les comptes avant/après.

Points ouverts :
- un chantier reste à la racine, sans client rattaché ;
- la boîte occupe **82 % de son quota** — à surveiller avant que le serveur
  refuse le courrier entrant ;
- aucune règle de filtrage n'a été vue dans le compte ; à confirmer.
