# Commandes du module Administration Opérationnelle

Slash-commands. Un fichier `.md` par commande : `commands/ma-commande.md`
s'invoque avec `/ma-commande`.

| commande | objet |
|---|---|
| [`/synchronise`](synchronise.md) | clôture sûre : vérifier, écrire le journal, committer, pousser |
| [`/on-reprend`](on-reprend.md) | reprendre un module en lisant **seulement** le journal |
| [`/releve`](releve.md) | changer de session sans perdre le fil ni brûler du contexte |

Les trois forment une séquence : **`/synchronise` → `/clear` → `/releve`**, et
`/on-reprend` en cours de route. Elles reposent toutes sur [`JOURNAL.md`](../JOURNAL.md) —
sans lui elles tournent à vide.
