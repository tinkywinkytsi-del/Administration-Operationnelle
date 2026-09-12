---
description: La clôture sûre, en un mot. Vérifier, écrire le journal, committer, pousser. Premier des trois temps de la relève — /synchronise → /clear → /releve.
---

# /synchronise — la clôture sûre

> **Premier des trois temps de la relève :**
> **`/synchronise`** → **`/clear`** → **`/releve`**
>
> Fonctionne aussi bien tapé comme mot seul (« synchronise ») que comme commande.

## Ce que ça fait, dans l'ordre

1. **Lire l'état réel** — `git status`, `git diff`, la branche courante et le
   journal. Séparer ce qui est à soi de ce qui ne l'est pas.
2. **Vérifier** proportionnellement au changement, et qu'aucun secret,
   identifiant, session, log ni fichier généré n'entre dans le dépôt.
   ⛔ **Ce dépôt est public** : vérifier aussi qu'aucune donnée nominative,
   aucun nom complet de collaborateur, aucune donnée de santé n'y figure.
3. **Écrire le journal** (`JOURNAL.md`) — la seule étape qu'aucun script ne peut
   faire, parce que c'est celle qui demande du jugement. Voir plus bas.
4. **Commit + push** de son propre travail, sur sa propre branche.
5. **Rendre compte** : branche, commit, et ce qui a été laissé de côté exprès.

Ne jamais forcer une fusion, sauter une vérification, ni embarquer le travail
d'un autre. En cas de conflit, de test rouge, de secret détecté ou de décision
humaine en attente : on s'arrête et on déclare le blocage exact.

## ⛔ Ce que le journal DOIT répondre — le test de cette commande

Le seul but de `/synchronise` est que la session suivante, après `/clear` +
`/releve`, puisse répondre à **deux questions** sans relire le projet :

| | |
|---|---|
| **Où en est-on ?** | ce qui est clos, ce qui est poussé, dans quel état |
| **Que reste-t-il ?** | et surtout **CE QUI EST CASSÉ** — avec ce qu'on sait déjà du diagnostic, et **comment NE PAS le vérifier** |

**Ce qui est cassé passe en PREMIER, avec son propre titre.** Pas noyé dans un
paragraphe. Sinon la relève « fonctionne » et la session suivante ne sait
toujours rien — exactement ce qu'on cherche à éviter.

**Et on ÉLAGUE** — 40 lignes maximum. Un journal de 115 lignes renchérit la
relève précisément là où elle doit être bon marché. Ce qui est fini et
fonctionne se comprime à une ligne ; ce qui est cassé et ce qui est en attente
restent entiers.

## Comment vérifier que la commande a servi

Il ne suffit pas que les commits soient poussés. On contrôle que le journal
**répond aux deux questions**, en y cherchant chaque point en attente par son
nom. Si un point soulevé aujourd'hui n'apparaît pas dans le texte,
`/synchronise` n'est pas terminé. On vérifie l'artefact, pas le code de retour
du `git push`.

## Pour finir

Dire en quelques lignes : ce qui a été poussé, ce qui a été laissé de côté, et
que `/clear` peut se faire sans rien perdre.
