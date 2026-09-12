# Organisation des agents — Administration-Operationnelle

Ce fichier **fait foi** sur la répartition des rôles, les contrôles obligatoires
et le cycle de vie d'une demande. Le [`coordinateur`](../agents/coordinateur.md)
s'y réfère ; les agents s'y conforment. En cas de contradiction avec un fichier
d'agent, c'est ce document qui tranche.

---

## 1. Principe

**On parle au coordinateur, pas aux spécialistes.** Il reformule, découpe,
assigne, déclenche les contrôles et rend la synthèse. Il ne produit rien lui-même.

**Un agent = un périmètre, et un seul.** Chaque définition d'agent énonce ce
qu'elle couvre *et ce qu'elle ne couvre pas*. Un agent sollicité hors périmètre
le dit et renvoie vers le bon.

**Les contre-pouvoirs bloquent indépendamment.** Ni le coordinateur ni l'agent
bloqué ne peuvent lever un blocage. Seul Thomas arbitre.

**Les pièces originales font foi.** Un tableau, un registre ou une base qui
contredit le document source a tort — jamais l'inverse.

**Human-in-the-loop total.** Les agents préparent et proposent. Toute écriture
hors du dépôt attend un accord explicite, point par point.

---

## 2. Les 14 agents et leur maturité

Ne pas invoquer un agent dont la matière n'existe pas encore : c'est du temps et
du contexte dépensés pour rien.

| agent | famille | maturité au 12.09.2026 |
|---|---|---|
| `coordinateur` | entrée | défini — jamais invoqué comme agent |
| `soudure` | métier | **exercé** — dépouillement de 44 certificats |
| `controle-chantier` | métier | défini, jamais exercé |
| `rapport-hebdomadaire` | métier | défini, jamais exercé |
| `appels-offres` | métier | défini, jamais exercé — pas de conversation source |
| `attestations` | métier | défini, jamais exercé — pas de conversation source |
| `radiographies` | métier | défini, jamais exercé — pas de conversation source |
| `lecteur-scan` | transverse | **exercé** — procédure appliquée, agent non invoqué |
| `lecteur-tableur` | transverse | **exercé** — procédure appliquée, agent non invoqué |
| `classeur` | transverse | défini, jamais exercé |
| `remplisseur` | transverse | défini, jamais exercé |
| `veille-echeances` | transverse | défini, jamais exercé |
| `relecteur` | contre-pouvoir | **exercé** — a trouvé 3 défauts réels |
| `gardien-confidentialite` | contre-pouvoir | défini ; sa fonction a servi manuellement |

« Procédure appliquée, agent non invoqué » signifie que la définition a servi de
consigne écrite sans passer par le mécanisme d'agent. C'est utile, mais ce n'est
pas un test de l'agent.

---

## 3. Matrice de correction croisée

Qui contrôle quoi. **Personne ne se relit soi-même.**

| production | contrôlé par |
|---|---|
| tout livrable, sans exception | `relecteur` |
| tout ce qui sort du poste ou entre dans ce dépôt public | `gardien-confidentialite` |
| une valeur transcrite d'un scan | recoupée avec la pièce originale, jamais avec un tableau |
| un calcul d'échéance | recalculé indépendamment, jamais relu |
| une donnée métier soudage | `soudure` — lui seul connaît les plages de qualification |
| une échéance, quelle qu'elle soit | `veille-echeances` — toujours vérifiée sur pièce |

---

## 4. Déclencheurs de blocage obligatoires

Pour que les contre-pouvoirs ne soient pas invoqués au hasard, voici les
situations où leur intervention est **obligatoire** et conditionne la livraison.

**`relecteur` doit intervenir si :**
- un fichier de production est modifié — classeur maître, PV, registre ;
- des fichiers sont déplacés, renommés, archivés ou supprimés ;
- un script écrit dans un fichier qu'il n'a pas lui-même créé ;
- un livrable part chez un tiers — organisme certificateur, client, autorité ;
- une donnée est reportée d'une source vers une autre.

**`gardien-confidentialite` doit intervenir si :**
- quoi que ce soit est commité dans ce dépôt, qui est **public** ;
- un document, un extrait ou une capture sort du poste ;
- une donnée de collaborateur apparaît dans un livrable destiné à un tiers ;
- un prompt ou une conversation est archivé dans `modules/*/conversations/`.

**Règle d'escalade.** Si l'un des deux bloque, seul Thomas arbitre le déblocage —
jamais l'agent dont le travail est bloqué, jamais le coordinateur de sa propre
initiative. Le déblocage est consigné dans `JOURNAL.md` avec sa justification.

---

## 5. Cycle de vie d'une demande

1. **Demande** — Thomas formule un besoin en français courant au `coordinateur`.
2. **Cadrage** — le coordinateur reformule en une phrase et la lui renvoie si
   l'ambiguïté changerait matériellement le travail. Sinon il décide et **dit
   sous quelle hypothèse** il travaille.
3. **Vérification préalable** — *avant de produire quoi que ce soit*, contrôler
   que le travail n'a pas déjà été fait. Étape ajoutée le 12.09.2026 : un dossier
   entier allait être refait alors qu'il était à jour depuis trois jours.
4. **Lecture des sources** — `lecteur-scan`, `lecteur-tableur`. On transcrit, on
   n'interprète pas ; ce qui est douteux est signalé, pas tranché.
5. **Production** — l'agent métier ou transverse concerné. Sur copie, jamais sur
   l'original, avec sauvegarde préalable.
6. **Contrôles** — `relecteur` systématiquement, `gardien-confidentialite` selon
   les déclencheurs du §4. Chacun bloque indépendamment.
7. **Correction et re-revue** — jusqu'à approbation. Une revue ne se solde pas
   par « c'est bon quand même ».
8. **Livraison** — le coordinateur rend la synthèse au format du §6.
9. **Journal** — `JOURNAL.md` mis à jour, élagué à 40 lignes. Ce qui est en
   attente passe en premier.

---

## 6. Forme de la synthèse

```
Demande      : <reformulation en une phrase>
Fait         : <ce qui a été livré, et par quel agent>
Bloqué       : <par qui, pourquoi, ce qu'il faut pour débloquer>
Ouvert       : <les décisions qui reviennent à Thomas>
Prochaine étape : <une seule>
```

Français courant. Ce qui est incertain est annoncé comme incertain. Ce qui n'a
pas pu être vérifié est déclaré non vérifié — une revue qui tait ses angles morts
donne une fausse assurance, et c'est pire que pas de revue.

---

## 7. Mode d'emploi au quotidien

| situation | quoi taper |
|---|---|
| reprendre un sujet | `/on-reprend <module>` |
| clore une session proprement | `/synchronise`, puis `/clear` |
| repartir dans une session neuve | `/releve` |
| une demande quelconque | l'énoncer en français au `coordinateur` |

Le fil de travail vit dans [`JOURNAL.md`](../JOURNAL.md), **pas dans une
conversation éternelle**. C'est ce qui rend une reprise bon marché : cinq
lectures, contre des ordres de grandeur de plus pour reconstruire le contexte.
