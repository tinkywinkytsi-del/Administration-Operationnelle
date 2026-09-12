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

## L'organisation en agents

**On parle au [`coordinateur`](agents/coordinateur.md).** Il reformule la demande,
la découpe, l'assigne aux spécialistes, déclenche les contrôles obligatoires et
rend la synthèse. Il ne fait jamais le travail lui-même — c'est ce qui l'empêche
de devenir un fourre-tout.

La répartition des rôles, les **déclencheurs de blocage obligatoires** et le
cycle de vie d'une demande sont fixés dans [`docs/ORGANISATION.md`](docs/ORGANISATION.md),
qui fait foi en cas de contradiction.

Derrière le coordinateur, 13 agents à périmètre unique : **6 métier** (par processus),
**5 transverses** (par verbe — lire, ranger, remplir, surveiller) et **2 de
contrôle**, déclenchés par règle et non au jugé. Détail et justification dans
[`docs/convention-agents.md`](docs/convention-agents.md).

## Structure

| dossier | contenu |
|---|---|
| `modules/` | **un module par sujet** — son README, ses règles, ses conversations sources |
| `agents/` | définitions d'agents — un fichier `.md` par module, un périmètre chacun |
| `skills/` | savoir-faire réutilisables (procédures, scripts) |
| `commands/` | slash-commands (`/nom`) |
| `contexte-partage/` | ce que **tous** les agents doivent savoir sur TSI |
| `conversations/` | les prompts d'origine, une conversation = un fichier |
| `JOURNAL.md` | l'état du fil entre deux sessions — 40 lignes max, élagué à chaque clôture |
| `docs/` | **[`ORGANISATION.md`](docs/ORGANISATION.md) — fait foi** · [agents](docs/convention-agents.md) · [commandes](docs/commandes.md) · [skills](docs/skills.md) |

`agents/`, `commands/` et `skills/` sont aussi exposés sous `.claude/` par liens
symboliques : une seule copie physique, deux chemins valides. Le module est donc
utilisable **installé comme plugin** et **ouvert directement comme dossier**.

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

## Continuité entre sessions

Le fil de travail vit dans [`JOURNAL.md`](JOURNAL.md), **pas dans une
conversation éternelle**. Séquence : **`/synchronise`** → **`/clear`** →
**`/releve`**, et **`/on-reprend <module>`** pour repartir en cours de route.
Une reprise bien faite coûte 5 lectures, contre des ordres de grandeur de plus
pour reconstruire le contexte en relisant le projet.

## Human-in-the-loop

Comme dans `TSI-Automatizacion` : on **prépare** et on **propose**, l'écriture
(mail envoyé, CRM, dossier modifié) attend une validation humaine explicite.
