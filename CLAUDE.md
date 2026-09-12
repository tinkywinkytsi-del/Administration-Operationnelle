# Administration Opérationnelle — module commun de toutes les conversations TSI

Ce repo est **le** module de référence pour le projet TSI. Il contient les
**agents**, les **skills**, les **commandes** et le **contexte partagé** utilisés
par toutes les conversations TSI, quel que soit l'outil (Claude Code, Codex, …).

## Règle mère — une seule source de vérité

⛔ **Les conversations du projet TSI utilisent CE module, et lui seul.**

Ne jamais importer dans une conversation TSI un agent, une convention, une règle
ou des données venant d'un autre projet, d'un autre dépôt ou d'une autre
entreprise : les contextes, les clients et les règles métier sont différents, et
les mélanger produit des réponses fausses.

Si une conversation TSI a besoin de quelque chose qui n'existe pas encore ici, on
ne va pas le chercher ailleurs : **on le crée ici**, dans `agents/`, `skills/` ou
`contexte-partage/`, et on l'utilise depuis ici.

## À quoi sert la séparation en agents

Chaque agent couvre **un périmètre et un seul**. C'est ce qui empêche une
conversation de tout mélanger : on invoque l'agent du sujet, il lit son propre
contexte, il rend son résultat. Voir `agents/README.md` pour la convention.

## Structure

| dossier | contenu |
|---|---|
| `modules/` | **un module par sujet** — son README, ses règles, ses conversations sources |
| `agents/` | définitions d'agents — un fichier `.md` par module, un périmètre chacun |
| `skills/` | savoir-faire réutilisables (procédures, scripts) |
| `commands/` | slash-commands (`/nom`) |
| `contexte-partage/` | ce que **tous** les agents doivent savoir sur TSI |
| `conversations/` | les prompts d'origine, une conversation = un fichier |

## Contexte partagé (à lire systématiquement)

@contexte-partage/objectif-general.md
@contexte-partage/regles-tsi.md
@contexte-partage/vocabulaire.md

## Les trois modules

| module | agent | couvre |
|---|---|---|
| [`modules/soudure`](modules/soudure/README.md) | `soudure` | qualification des soudeurs (ISO 9606-1, dossier QS) **et** modes opératoires DMOS/QMOS |
| [`modules/controle-chantier`](modules/controle-chantier/README.md) | `controle-chantier` | procès-verbal des 3 contrôles de chantier annuels |
| [`modules/rapport-hebdomadaire`](modules/rapport-hebdomadaire/README.md) | `rapport-hebdomadaire` | fiches hebdomadaires d'heures et de frais → rapport mensuel |

`soudure` **produit** le référentiel des qualifications ; `controle-chantier` le
**consomme**. Fiabiliser avant de câbler.

## D'où vient le contenu

Le module se construit à partir de conversations réelles. Chaque conversation
source est archivée telle quelle dans `conversations/`, puis ce qui est
réutilisable en est extrait vers `agents/` ou `skills/`. L'archive reste : elle
explique *pourquoi* une règle existe. Voir `conversations/INDEX.md`.

## Human-in-the-loop

Comme dans `TSI-Automatizacion` : on **prépare** et on **propose**, l'écriture
(mail envoyé, CRM, dossier modifié) attend une validation humaine explicite.
