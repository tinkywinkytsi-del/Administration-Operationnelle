# Règles TSI

Règles dures, valables pour **tous** les agents du module.

## 0. Human-in-the-loop total
Les agents **préparent** et **proposent**. Toute écriture qui sort du repo —
envoi de mail, écriture CRM, création/modification de dossier client, message
WhatsApp — attend une **validation humaine explicite**. Une exécution
automatique/programmée ne fait que préparer.

## 1. Une seule source de vérité
Ce module, et lui seul. Aucun agent, aucune convention, aucune donnée importée
d'un autre projet, d'un autre dépôt ou d'une autre entreprise. Voir `CLAUDE.md`.

## 2. Pas de données clients ni RH dans le repo
⚠️ **Ce dépôt est PUBLIC.** Le repo contient des prompts, des agents et des règles.
Les données (plans, dossiers, PDF, tableurs) restent à leur emplacement et sont
référencées par chemin. Voir `.gitignore`.

N'entrent jamais dans le repo : **noms complets de collaborateurs**, données de
santé (arrêt maladie, chômage technique), dates d'entrée/sortie, échecs d'examen,
numéros de certificat rattachés à une personne nommée, coordonnées.
Un prompt qui en contient est **archivé caviardé**, avec un tableau de ce qui a
été retiré et où le retrouver. Les noms d'onglet courts sont tolérés ; les noms
complets ne le sont pas.

## 3. Un agent = un périmètre
Pas d'agent fourre-tout. Si un sujet nouveau apparaît, on crée un agent.

<!-- TODO: ajouter les règles métier issues des conversations sources. -->
