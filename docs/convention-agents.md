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

## Agents existants

Un agent par module. Le tableau suit `modules/`.

| agent | périmètre | module |
|---|---|---|
| [`soudure`](../agents/soudure.md) | certificats de qualification soudeur, DMOS/QMOS | [`modules/soudure`](../modules/soudure/README.md) |
| [`controle-chantier`](../agents/controle-chantier.md) | procès-verbal de contrôle de chantier | [`modules/controle-chantier`](../modules/controle-chantier/README.md) |
| [`rapport-hebdomadaire`](../agents/rapport-hebdomadaire.md) | fiches hebdo d'heures et frais, rapport mensuel | [`modules/rapport-hebdomadaire`](../modules/rapport-hebdomadaire/README.md) |
