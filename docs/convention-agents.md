> Règlement de coordination : [`ORGANISATION.md`](ORGANISATION.md) — il fait foi.

# Agents du module Administration Opérationnelle

Un agent = **un périmètre et un seul**. C'est la mécanique qui empêche les
conversations TSI de tout mélanger.

## Convention

Un fichier `.md` par agent, avec ce frontmatter :

```markdown
---
name: nom-en-kebab-case
description: Quand utiliser cet agent. Doit suffire, seul, à décider de l'invoquer.
tools: Read, Grep, Glob, Bash   # optionnel — par défaut, tous
---

# <Nom de l'agent>

## Périmètre
Ce que cet agent couvre — et surtout ce qu'il NE couvre PAS.

## Contexte à lire
Les fichiers de `contexte-partage/` et les autres sources dont il a besoin.

## Procédure
Les étapes, dans l'ordre.

## Règles dures
Ce qu'il ne doit jamais faire sans validation.
```

## Les 14 agents

**Le coordinateur — celui à qui on parle**

| agent | rôle |
|---|---|
| [`coordinateur`](../agents/coordinateur.md) | point d'entrée quotidien : reformule, découpe, assigne, arbitre, synthétise. **Ne fait jamais le travail lui-même** |

**Agents métier — par processus**

| agent | périmètre | module |
|---|---|---|
| [`soudure`](../agents/soudure.md) | certificats de qualification, DMOS/QMOS | [soudure](../modules/soudure/README.md) |
| [`controle-chantier`](../agents/controle-chantier.md) | procès-verbal de contrôle de chantier | [controle-chantier](../modules/controle-chantier/README.md) |
| [`rapport-hebdomadaire`](../agents/rapport-hebdomadaire.md) | fiches d'heures et de frais, rapport mensuel | [rapport-hebdomadaire](../modules/rapport-hebdomadaire/README.md) |
| [`appels-offres`](../agents/appels-offres.md) | offres, soumissions, PV d'ouverture, taux de réussite | — |
| [`attestations`](../agents/attestations.md) | justificatifs légaux et sociaux, TSI et prestataires | — |
| [`radiographies`](../agents/radiographies.md) | rapports RT, conformité, laboratoires et tarifs | — |

**Agents transverses — par verbe**

| agent | ce qu'il sait faire |
|---|---|
| [`lecteur-scan`](../agents/lecteur-scan.md) | extraire d'un PDF sans couche texte — transcrit, n'interprète pas |
| [`lecteur-tableur`](../agents/lecteur-tableur.md) | lire et écrire Excel sans casser formules ni mise en page |
| [`classeur`](../agents/classeur.md) | proposer destination et nom normalisé — ne déplace jamais |
| [`remplisseur`](../agents/remplisseur.md) | poser des données validées dans un formulaire |
| [`veille-echeances`](../agents/veille-echeances.md) | échéances, validités, attestations — vérifiées sur pièce |

**Agents de contrôle — déclenchés par règle, pas au jugé**

| agent | déclencheur |
|---|---|
| [`relecteur`](../agents/relecteur.md) | **avant toute livraison**, sans exception |
| [`gardien-confidentialite`](../agents/gardien-confidentialite.md) | **avant que quoi que ce soit sorte** — commit, envoi, partage |

## Pourquoi par verbe, et non par dossier

L'arborescence documentaire compte 23 dossiers racine. Un agent par dossier
donnerait 23 périmètres qui se chevauchent, entre lesquels personne ne saurait
choisir, et qui rediraient tous la même chose sur la lecture d'un scan.

Les agents transverses sont donc organisés par **verbe** — lire, ranger, remplir,
surveiller, contrôler — le dossier n'étant qu'un paramètre. Seuls les agents
métier sont organisés par processus, parce que leurs règles, elles, diffèrent
réellement.

## Les deux agents de contrôle ne sont pas optionnels

`relecteur` applique la règle du projet : *personne ne valide seul son propre
travail*. Il n'a ni `Write` ni `Edit` — il constate, l'agent producteur corrige,
et la revue repasse jusqu'à approbation.

`gardien-confidentialite` existe parce que le coût d'un défaut est
disproportionné : le 12.09.2026, des données RH nominatives poussées sur ce dépôt
public ont survécu à un `push --force` et n'ont disparu qu'après suppression et
recréation du dépôt.

Le coordinateur **ne peut pas lever** un blocage posé par l'un des deux.
