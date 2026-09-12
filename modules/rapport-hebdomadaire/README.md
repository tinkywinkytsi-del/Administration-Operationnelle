# Module Rapport hebdomadaire

Saisie des **fiches hebdomadaires** remplies à la main par les collaborateurs
(heures et frais), scannées en PDF, et consolidation dans le **rapport mensuel**.

> Le module s'appelle « hebdomadaire » parce que la **matière** est hebdomadaire :
> 1 fiche = 1 collaborateur × 1 semaine. Le **livrable**, lui, est mensuel —
> `rapport_<mois>_<année>_vN.xlsx`, un onglet de suivi par semaine.

## Conversation source
- [`conversations/rapport-mensuel.md`](conversations/rapport-mensuel.md) — ⚠️ **caviardée**.

## Dossiers sources (iCloud — hors repo)
```
TSI-new/09 Dossier personnel/Thomas/rapport hebdo/
    prompt_claude_code_septembre_2026_v2.md   ← le prompt INTÉGRAL, non caviardé
    Claude/rapport_septembre_2026_v2.xlsx     ← fichier de travail courant
    <jjmmaaaa>_<nnn>.pdf                      ← fiches scannées
collaborateur.xlsx                            ← onglet « en-service » : noms et fonctions
```

## Ce qui n'est pas dans le repo
Le dépôt étant public, la **table onglet ↔ nom complet ↔ fonction** des 36
collaborateurs n'y figure pas, ni les situations individuelles. L'agent lit ces
éléments dans `collaborateur.xlsx` et dans le prompt original, à chaque fois.
Détail de ce qui a été retiré : fin du fichier de conversation.

## Règles dures
- **Ne jamais repartir d'un template vierge** ni recréer le mois : ouvrir la
  version `vN` la plus haute, compléter, sauver en `vN+1`. **Une version = une
  sauvegarde**, jamais d'écrasement.
- **`D` = le total d'heures NOTÉ sur la fiche**, jamais le calcul des horaires de
  présence. Ne « corriger » jamais un total noté.
- Nom imprimé **barré** sur une fiche → prendre le **manuscrit non barré**.
- **Férié ≠ congé.** Férié : `C=0`, `D=0`, **pas** de `H=1`. Congé/vacances/
  maladie : `C=8.5` ou `7.5`, `D=0`, **`H=1`**.
- **Ne jamais deviner une donnée illisible** : la lister et demander.
- **Ne jamais remettre `H12` à 20** en clôture : les 20 jours sont un droit annuel
  qui se consomme.
- Contrôle de référence : `C44 = 174.5 h` pour un mois de septembre 2026 sans absence.

## Contraintes techniques de la machine
- `pdftoppm` **n'est pas installé** → utiliser **PyMuPDF** (`fitz`),
  `page.get_pixmap(dpi=140)`.
- **LibreOffice n'est pas installé** → `recalc.py` ne tourne pas. Les formules
  écrites par openpyxl n'ont pas de valeur en cache : **recalculer soi-même en
  Python** et dire ce qui a été contrôlé.
- Lire un classeur existant demande **deux chargements** (`data_only=True` pour
  les valeurs, défaut pour les formules). Ne jamais sauver un classeur ouvert en
  `data_only=True` : ça détruit les formules.
