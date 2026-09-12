---
description: Reprendre le travail là où il s'est arrêté en lisant SEULEMENT le journal — sans relire tout le projet ni les autres modules, pour ne pas brûler de contexte.
---

# /on-reprend — reprendre sans tout relire

La continuité entre sessions vit **sur le disque**, pas dans une conversation
éternelle. Une conversation unique relit tout son historique à chaque tour ;
c'est ce qui la rend chère et oublieuse. `/on-reprend` est le déclencheur
explicite du mécanisme qui remplace ça.

## Portée : UN module à la fois

`/on-reprend soudure` · `/on-reprend controle-chantier` ·
`/on-reprend rapport-hebdomadaire`

Sans argument, reprendre le module dont le journal parle en dernier. **On n'entre
pas dans les autres modules**, sauf si le journal dit explicitement qu'un point
en attente ailleurs bloque celui-ci.

## Quoi lire, et dans CET ordre — rien de plus pour démarrer

1. **`JOURNAL.md`** — la source principale, filtrée sur le module concerné.
   Il est court exprès (40 lignes max).
2. **La mémoire persistante**, si la session en a une — la consulter par
   pertinence, pas la déverser entière.
3. **NE PAS relire** `CLAUDE.md` en entier ni les `contexte-partage/*.md` :
   ils sont déjà chargés par `@import`. C'est du contexte de fond, pas l'état
   du moment.
4. Si le journal renvoie à un fichier précis, lire **seulement** celui-là —
   ne pas parcourir l'arborescence « pour se situer ».
5. **Vérifier l'état réel avant de rien supposer.** Si le journal et le disque
   divergent, **c'est le disque qui a raison**.

## Quoi faire de ce qu'on a trouvé

- Une piste avec une étape suivante **claire et déjà autorisée** : la continuer
  directement, sans reposer une question à laquelle le journal répond.
- Quelque chose bloqué sur une décision humaine : le dire en trois lignes et
  attendre.
- Rien en attente : le dire simplement. Ne pas inventer du travail, ne pas
  aller regarder les autres modules.

## Rendre compte, court

Un paragraphe : où en était le module, ce qui a été fait pendant cette reprise,
ce qui suit.

## Avant de refermer

Si la reprise a fait avancer quelque chose, mettre `JOURNAL.md` à jour en
élaguant — pour que la PROCHAINE reprise reste bon marché.
