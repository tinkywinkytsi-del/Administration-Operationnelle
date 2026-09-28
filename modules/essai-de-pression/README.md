# Module Essai de pression

L'**épreuve hydraulique** d'un réseau enterré de chauffage ou de froid à
distance : le protocole remis au maître d'ouvrage avant l'essai, les valeurs
qu'imposent ses **Conditions Techniques Générales (CTG)**, et les pièces à
produire après.

> ⛔ **Aucune valeur de CTG n'est recopiée ici.** Les CTG sont les documents
> contractuels d'un maître d'ouvrage : elles restent à leur emplacement et sont
> référencées par chemin, comme le prescrit `contexte-partage/regles-tsi.md` §2.
> Ce README porte la **méthode** — comment lire une CTG, quoi y chercher, quels
> pièges elle tend. Les chiffres se lisent dans la CTG classée dans la
> soumission du chantier.

## Skill
- [`skills/essai-pression`](../../skills/essai-pression/SKILL.md) — le geste :
  calcul du volume, lecture d'un rapport de manomètre enregistreur,
  recoupements, transmission au maître d'ouvrage.

## Conversation source
- [`conversations/protocole-essai-pression.md`](conversations/protocole-essai-pression.md)

## Où vivent les données (hors repo)
```
TSI-new/01 Chantier/Client/<client>/<dossier CTG commun>/
    CTG « réseaux », « fouilles », « regards », fiches de point d'arrêt

TSI-new/01 Chantier/Client/<client>/<région>/<chantier>/Essai de pression/
    protocole · enregistrements manomètres · certificats d'étalonnage · PV
```
Les CTG « réseaux » ne sont pas dans le dossier commun : elles arrivent **avec
chaque appel d'offres** et vivent dans le dossier du chantier. C'est voulu —
elles diffèrent d'un réseau à l'autre.

---

## 1. La pression d'épreuve — la seule chose à ne pas se tromper

> ⛔ **La pression d'épreuve se calcule sur PS, jamais sur PN.**
> `Pression d'épreuve = 1,5 × PS`, où PS est la **pression maximale admissible**
> du réseau. Le PN des tubes et des vannes est une caractéristique de composant :
> il ne donne pas la pression d'essai. Cette confusion est la première source
> d'erreur, et elle donne toujours un chiffre trop élevé.

Attention : « pression de service » et « PS » ne sont pas la même grandeur. La
pression de service est la pression d'exploitation, généralement inférieure.
C'est **PS** qui sert de base, à l'épreuve comme au test des vannes.

### Où lire le bon chiffre, dans cet ordre
1. **La CTG classée dans la soumission du chantier** — pas une copie trouvée
   ailleurs, pas une autre version.
2. **Le plan d'exécution du chantier**, quand il porte ses propres paramètres de
   conception (norme, températures, pression interne maximale). C'est la source
   la plus spécifique : c'est elle qui donne le PS à retenir.
3. Et **écrire la filiation du chiffre dans le protocole** — « 1,5 × <PS>,
   pression interne maximale du plan d'exécution » — pour que la Direction des
   Travaux puisse la vérifier sans discussion.

### Vérifier l'arithmétique, pas seulement la source
Un protocole a longtemps porté une pression d'épreuve et une base de calcul qui
ne concordaient pas : le produit annoncé n'était pas `1,5 ×` la base citée.
Selon le chiffre retenu, une même courbe d'enregistrement passe ou ne passe pas.
Recalculer la multiplication **et** vérifier que la base citée est bien le PS
retenu, avant d'écrire au client que le critère est tenu.

### Toutes les valeurs ne se calculent pas
Certaines CTG **imposent en dur** une pression d'épreuve par classe de réseau,
qui ne vaut pas `1,5 × PN` ni toujours `1,5 × PS`. Ne jamais recalculer une
valeur que la CTG donne explicitement : la lire, et citer le paragraphe.

### Trois pièges de numérotation et de rédaction
1. **Deux documents différents peuvent porter le même numéro de CTG** — un même
   numéro couvrant deux classes de réseau distinctes. Le numéro seul n'identifie
   pas le document.
2. **Une CTG peut se contredire d'un paragraphe à l'autre** : le chapitre
   « dimensionnement » et le chapitre « épreuves » ne donnent pas toujours la
   même valeur, par reliquat d'une variante non corrigée. Signaler la divergence
   à la Direction des Travaux plutôt que trancher en silence.
3. **Plusieurs versions d'une même CTG circulent** selon l'appel d'offres, avec
   des valeurs différentes. Vérifier la version, pas seulement le numéro.

---

## 2. Ce que le chapitre « épreuves hydrauliques et rinçage » exige

Ce chapitre est le même dans toutes les CTG réseaux, aux valeurs près. Il
impose, dans l'ordre :

**Avant l'essai**
- Avertir la Direction des Travaux et lui **remettre le dossier de soudage**.
- **Constat d'achèvement des travaux** en commun MO / DT / entreprise.
- **Contrôle visuel contradictoire** de toutes les soudures et équipements, avec
  procès-verbal signé des deux parties.
- **Contrôle de la boucle de détection d'humidité, conduites vides**, en présence
  du MO : continuité des fils, résistance, longueur de boucle et **taux
  d'humidité** enregistrés.
- Une **température extérieure minimale** est exigée — sinon l'essai ne démarre
  pas.
- **Manomètres contrôlés contradictoirement** entre l'entreprise et la DT.

**Pendant**
- Mise en pression, **vannes ouvertes**, pendant la durée minimale imposée, à
  l'abri des variations de température.
- **Test d'étanchéité des vannes** en présence de l'exploitant, **à PS** : on
  redescend, on ferme les vannes, on vidange en aval, on contrôle 2 heures. Le
  réseau étant remblayé, la validation se fait par contrôle dans une chambre, à
  une extrémité de réseau ou en sous-station.

**Après**
- **Second contrôle de la boucle de détection d'humidité, conduites pleines.**
- **Rinçage** : premier remplissage à 100 % du volume, puis rinçage d'environ
  **deux fois ce volume**. La nature de l'eau — potable ou brute — **diffère
  selon la CTG**, ce n'est pas un détail.
- Sur réseau **structurant** : pompe et filtre à barreaux magnétiques en
  sous-station, surveillance et nettoyage journalier du filtre.
- **Remplissage définitif en eau traitée** : par le maître d'ouvrage pour
  l'antenne d'une sous-station, par l'entreprise avec un poste de traitement
  mobile pour un réseau structurant. Le protocole doit dire **lequel des deux cas
  s'applique**, sinon il n'engage personne.

> Les CTG ne nomment **aucun produit** de traitement d'eau — vérifié par balayage
> de l'ensemble des CTG de l'arborescence. Si une marque est exigée sur un
> chantier, l'exigence vient d'ailleurs : mémoire descriptif, série de prix,
> conditions particulières, ou consigne de l'exploitant.

### Aucune tolérance chiffrée de chute de pression
Les CTG **ne fixent pas** de chute de pression maximale, et la fiche de point
d'arrêt de mise en service dit seulement « conformité aux pressions et à la durée
d'épreuve des CTG ». Écrire une tolérance inventée dans un protocole, c'est
s'engager sur un critère qu'on ne peut pas défendre. Formulation tenable :

> La pression d'épreuve est maintenue pendant toute la durée de l'essai, sans
> fuite ni défaut constaté. L'étanchéité est validée contradictoirement au vu des
> enregistrements des manomètres, qui sont contrôlés en commun.

> ⚠️ **Vérifier l'étendue de mesure du manomètre avant d'écrire un critère.**
> Un enregistreur 0–300 bar à ± 0,05 %FS a une incertitude de **± 0,15 bar**. Un
> critère « chute ≤ 0,1 bar » est alors inférieur à l'erreur de l'instrument :
> indémontrable, et perdu d'avance en cas de litige. Pour une épreuve sous
> quelques dizaines de bar, un manomètre à l'étendue resserrée rend
> l'enregistrement exploitable.
> Distinguer aussi, sur un certificat d'étalonnage, le **numéro de commande** du
> fournisseur et le **numéro de série** de l'appareil : c'est le n° de série qui
> identifie le manomètre, et la **date de mesure** peut être bien antérieure à la
> date d'émission du certificat.

---

## 3. Trame du protocole

Le protocole est un mode opératoire remis avant l'essai. Trame éprouvée :

1. **Introduction et objectifs**
2. **Caractéristiques du tronçon** — tableau : chantier, MO/exploitant, type de
   réseau, CTG applicable, bases de dimensionnement, conduites, linéaire en eau,
   volume, vannes, pression d'épreuve, pression du test des vannes, durée,
   température extérieure, manomètres et certificats, fluide d'essai
3. **Extrait du plan** + **repérage des points** (points hauts / purges, point
   bas / remplissage-vidange, emplacement des manomètres)
4. **Préalables et points d'arrêt**
5. **Manipulations avant essai** — nettoyage mécanique, nettoyage hydraulique,
   contrôle visuel ou vidéo
6. **Étapes de l'essai** — schéma, remplissage et purge d'air, imprégnation, mise
   en pression, test pression, test d'étanchéité des vannes, contrôle de la
   boucle après épreuve, rinçage final, fin d'essai
7. **Documents établis à l'issue de l'essai**

Les étapes de la procédure sont **numérotées en continu**, de bout en bout : sur
le terrain on s'y réfère par leur numéro.

### Calcul du volume d'eau
Volume = section intérieure du **tube de service** × **linéaire en eau**.
L'enveloppe est l'isolation : elle ne contient pas d'eau. Le linéaire en eau,
ce n'est pas le métré du chantier : c'est **la somme des barres droites et des
développés de coudes et pièces spéciales**, recoupée sur les **bons de
livraison** et non sur une quantité annoncée de mémoire. Un réseau aller-retour
compte deux fois la longueur de tranchée. Le rinçage demande ensuite environ
**trois fois** ce volume — un remplissage plus deux volumes de rinçage.

Ne jamais mesurer une longueur au pixel sur un plan : la demander, ou la lire
sur les bons de livraison. Le détail du calcul est dans le skill.

---

## 4. Ce que l'essai doit produire

| pièce | établie par | va où |
|---|---|---|
| PV de contrôle visuel | entreprise, signé des 2 parties | dossier |
| **PV d'étanchéité** | **le mandataire**, en commun MO / DT / entreprise | dossier |
| PV d'épreuve hydraulique | entreprise, signé des 2 parties | dossier |
| Enregistrements des manomètres + certificats d'étalonnage | entreprise | annexes du PV |
| PV de rinçage | entreprise, signé des 2 parties | dossier |
| PV de détection d'humidité (avant **et** après) | entreprise, signé des 2 parties | dossier |
| Dossier des Ouvrages Exécutés | entreprise | dossier |
| **Fiche de point d'arrêt de mise en service** | en commun | conditionne la mise en service |

Le « PV d'étanchéité » et le « PV d'épreuve hydraulique » sont **deux documents
distincts** — le premier est établi par le mandataire, le second par
l'entreprise. Les CTG les citent l'un après l'autre et on les confond facilement.

### Les fiches de point d'arrêt
Quatre fiches jalonnent le chantier. Celles qui touchent à l'essai :

| fiche | autorise | ce qui touche à l'essai |
|---|---|---|
| n° 1 | le démarrage des travaux | **schéma de montage des fils de détection d'humidité** |
| n° 2 | le sablage des conduites | boucle de détection **conduites vides** |
| n° 4 | **la mise en service et la réception** | épreuve hydraulique, boucle **conduites pleines**, rinçage, remplissage, DOE |

> ⚠️ La mesure **conduites vides** du point d'arrêt n° 2 n'est plus réalisable une
> fois la mise en eau faite. Si elle a été oubliée, le dire à la DT plutôt
> qu'attendre qu'elle le découvre à la levée du point d'arrêt n° 4.

---

## 5. Règles dures
- ⛔ **Pression d'épreuve = 1,5 × PS.** Jamais 1,5 × PN. Jamais sur la pression
  de service.
- ⛔ **Aucune valeur qui ne soit pas sourçable** dans une CTG, un plan
  d'exécution, un bon de livraison ou un certificat. Un protocole est un
  engagement contractuel : une phrase inventée engage l'entreprise.
- ⛔ **Aucune valeur de CTG ni aucune référence de document client dans ce
  dépôt** : il est public. Les chiffres se lisent dans la CTG du chantier.
- Travailler sur la **CTG classée dans la soumission du chantier**, et vérifier
  sa version.
- **Recouper les quantités sur les pièces**, pas sur une valeur annoncée de
  mémoire.
- Vérifier que le **critère d'acceptation est mesurable** avec les instruments
  prévus.
- Relire par un agent **relecteur distinct** avant toute remise, et faire passer
  le **gardien-confidentialité** avant toute sortie du poste.
- L'écriture dans un dossier client attend une **validation humaine explicite**.

## Dépendances
- Le contrôle visuel des soudures et le dossier de soudage viennent du
  [module Soudure](../soudure/README.md).
- Les contrôles non destructifs relèvent de l'agent `radiographies`.
- La mesure de bouclage et le plan de détection des fils sont sous-traités : la
  convocation du prestataire doit rappeler qu'il n'y a parfois **qu'un seul point
  de mesure accessible** une fois le réseau remblayé, et lui donner les contacts
  du chantier (MO, exploitant, génie civil).
