---
description: Reprendre le travail depuis une autre session ou un autre compte, sur la même machine, sans brûler du contexte et sans rien casser. Troisième temps de la relève.
---

# /releve — changer de session sans perdre le fil

## Ce qu'il faut comprendre une fois pour toutes

**Le travail ne vit PAS dans la conversation** — il vit sur le disque et sur
GitHub. Changer de session ou de compte ne perd donc rien. La seule chose perdue
est *la discussion*, et c'est déjà réglé : le journal la remplace.

**Ce qu'il ne faut jamais faire** : se mettre à lire le projet entier « pour se
mettre à jour ». C'est ce qui brûle le contexte de la nouvelle session en dix
minutes. Cette commande existe pour l'éviter.

## Ce que fait la commande — 5 lectures maximum, pas une de plus

1. **`JOURNAL.md`** — l'état du fil. La SEULE source du « où en est-on ».
   On ne relit pas l'historique, on n'ouvre pas les modules.
2. **`git status` + `git log --oneline -5`**.
3. **Les PR ouvertes** (`gh pr list`) — le travail qui attend une décision.
4. **`MEMORY.md`** s'il existe — il se charge seul, inutile de le demander.
5. Le fichier précis que le journal désigne, s'il en désigne un.

⛔ **Et RIEN D'AUTRE.** Pas de parcours de `modules/`, pas de relecture de
`contexte-partage/` (l'`@import` l'apporte déjà). Si quelque chose manque, on le
cherche au `grep` **quand le besoin apparaît** — jamais « au cas où ».

## Avant de changer de session — 30 secondes

Lancer **`/synchronise`** dans la session qui s'achève. Ça pousse le travail en
cours et écrit 3 à 5 lignes de journal : ce qui est resté à moitié, et quelle
est l'étape suivante concrète.

Si la session s'est arrêtée brutalement sans ça : le travail poussé est
intact ; seules quelques heures de contexte de discussion sont perdues, jamais
du code.

## Ce qu'on ne touche PAS en reprenant

- **On ne change pas de branche.** C'est ce qui donne l'impression que du travail
  a disparu.
- **On ne fusionne rien** dans la première minute. D'abord regarder, ensuite décider.
- **Rien de non committé n'est jamais jeté.** C'est le travail de la session
  précédente.

## Le coût

Une relève bien faite coûte **5 lectures**, contre des ordres de grandeur de plus
pour reconstruire le contexte en lisant le projet. Tout le truc est là : **le
projet s'est déjà expliqué par écrit ; la nouvelle session le lit, elle ne le
re-déduit pas.**

## Pour finir

Dire en cinq lignes : où on en est, ce qui n'est pas intégré, ce qui attend une
décision, et l'étape suivante. Puis continuer à partir de là — sans reposer une
question dont la réponse est déjà écrite.
