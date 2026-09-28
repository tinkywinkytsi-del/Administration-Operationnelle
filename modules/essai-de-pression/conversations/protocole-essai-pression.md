# Conversation source — protocole d'essai de pression

**Date** : 15 au 28.09.2026
**Objet** : construire le protocole d'essai de pression d'un chantier de
chauffage à distance enterré, à partir de deux protocoles antérieurs et des CTG
du maître d'ouvrage, puis convoquer un prestataire pour la mesure de bouclage.

## Caviardage

| retiré | où le retrouver |
|---|---|
| nom du maître d'ouvrage, numéros et noms des chantiers | `TSI-new/01 Chantier/Client/<client>/` |
| noms, téléphones et adresses mail des intervenants (MO, exploitant, génie civil, prestataire, TSI) | `TSI-new/07 Communication/Base Client/Base-clients.xlsx` |
| CTG, plans d'exécution, isométriques, bons de livraison, certificats d'étalonnage | dossier du chantier, sous-dossier `Essai de pression/` |
| protocoles et PV produits | idem |

Seule la méthode est conservée ici. **Aucune valeur de CTG n'est reprise** : les
CTG sont les documents contractuels du maître d'ouvrage et restent à leur
emplacement.

---

## La demande, reformulée
1. Prendre en compte les CTG du maître d'ouvrage.
2. Analyser deux protocoles d'essai de pression déjà réalisés.
3. À partir d'un plan annoté, d'un template et des éléments du chantier,
   produire le protocole d'un nouveau chantier.
4. Puis convoquer un prestataire pour la mesure de bouclage des fils de
   détection d'humidité et le plan de détection.

## Ce que l'analyse des deux protocoles antérieurs a montré
Les deux documents partagent la même trame, mais l'un est nettement plus abouti
que l'autre. Les écarts qui comptaient :

- **Une tolérance de chute de pression incohérente** dans le plus ancien
  (0,3 bar/heure sur 24 h autorise 7 bar de perte), alors qu'aucune CTG ne fixe
  de tolérance chiffrée.
- **Aucun test d'étanchéité des vannes** dans l'un des deux, alors que les CTG
  l'imposent.
- **Aucun des deux ne traitait la boucle de détection d'humidité**, qui est
  pourtant ce qui peut faire refuser la levée du point d'arrêt n° 4.
- Aucun ne mentionnait le constat d'achèvement, le PV de contrôle visuel, la
  température extérieure minimale, ni la liste des PV à produire.

## Ce que la construction du nouveau protocole a appris
- La pression d'essai ne se déduit pas du PN — voir le README, §1. L'erreur
  `1,5 × PN` était dans la demande de départ.
- La CTG à retenir est **celle classée dans la soumission du chantier**, et son
  numéro ne suffit pas à l'identifier : deux documents différents peuvent porter
  le même numéro, et plusieurs versions circulent.
- Le **plan d'exécution** du chantier porte ses propres paramètres de
  conception, plus spécifiques que la CTG générique.
- Les quantités annoncées de mémoire étaient fausses : le recoupement sur les
  bons de livraison a donné un linéaire différent, et des coudes avaient été
  oubliés dans le volume d'eau.
- Le critère d'acceptation écrit dans les protocoles antérieurs était
  **inférieur à l'incertitude des manomètres utilisés**.

## Ce que les deux contre-pouvoirs ont trouvé
Le `relecteur` et le `gardien-confidentialite` ont tous deux **bloqué** la
première version. Prises ensemble, leurs trouvailles justifient la règle
« personne ne valide seul son propre travail » :

- une valeur de pression non établie, contredite par le plan d'exécution ;
- deux affirmations non sourçables, dont une qui engageait le client ;
- un critère d'acceptation inventé et indémontrable ;
- une contradiction interne héritée du template ;
- une annexe annoncée mais absente ;
- des quantités non recoupées ;
- **un nom complet de collaborateur dans les métadonnées du document**, hérité
  du template, avec l'historique de révisions et une date d'impression d'un
  autre chantier.

> **À retenir sur les templates Word** : un document construit à partir d'un
> template hérite de `docProps/core.xml` — auteur, dernier modificateur, nombre
> de révisions, date d'impression. Ces champs traversent l'enregistrement sans
> qu'on les voie et sortent avec le fichier. Les remettre à zéro fait partie de
> la production, pas du nettoyage optionnel.

## Reproduire la mise en forme d'un document de référence
Les documents partageaient le même `styles.xml` : toute la charte tenait en
**formatage direct**, pas dans les styles. Pour aligner un document sur un
autre, relever les runs du document de référence (taille, gras, italique,
soulignement, couleur) plutôt que les styles. Pour un élément complexe — un
titre avec filet et espacement particulier — **reprendre le paragraphe tel quel**
et n'en remplacer que le texte, plutôt que tenter de le reconstituer.

## Convocation d'un prestataire
La convocation d'un sous-traitant de mesure doit porter :
- la prestation attendue, découpée ;
- les caractéristiques du tronçon ;
- **le ou les points de mesure accessibles** — une fois le réseau remblayé, il
  n'y en a souvent **qu'un seul**, et le prestataire doit le savoir avant de se
  déplacer ;
- l'état du réseau (vide ou en eau), qui détermine le nombre de passages ;
- les contacts du chantier : MO, exploitant, génie civil, donneur d'ordre ;
- le rattachement aux fiches de point d'arrêt, qui explique l'urgence ;
- un plan annoté en annexe.

Pour annoter un plan sans rien masquer : **agrandir la toile** avec un bandeau
de titre en haut et un bandeau de légende en bas, et n'ajouter sur le plan
lui-même qu'une flèche vers le point concerné.
