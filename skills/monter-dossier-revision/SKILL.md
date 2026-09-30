---
name: monter-dossier-revision
description: Monter le dossier de révision (DOE) d'un chantier — relever l'arborescence attendue, inventorier, copier les pièces, dépouiller les courriels, recouper, et dresser la liste de ce qui manque. À utiliser dès qu'il faut constituer, compléter ou vérifier un dossier de révision, un DOE ou un dossier des ouvrages exécutés.
---

# Monter un dossier de révision

**Inventorier d'abord, copier ensuite, recouper toujours.** Le montage ne consiste
pas à rassembler des fichiers : il consiste à vérifier que chaque pièce
correspond à ce qui a été exécuté.

## ⛔ Les cinq règles qui coûtent le plus cher

**1. Copier, jamais déplacer.** Le dossier de révision est une vue, pas un
déménagement. Vérifier les originaux après chaque lot :
```bash
cp -n "$SRC" "$DEST/"        # -n : ne jamais écraser en silence
```

**2. Sauvegarde horodatée avant toute correction** d'un document de production,
et **hors du dossier remis** :
```bash
cp -n "cahier.xlsx" "cahier_AVANT-CORRECTION_$(date +%Y-%m-%d).xlsx"
```

**3. Ne jamais modifier un enregistrement pour le faire coller à une pièce.**
Si le cahier et un certificat divergent, c'est la réalité du chantier qui
tranche. Une correction n'est légitime que si elle rétablit ce qui s'est
réellement passé — et si le document est déjà parti chez le client, elle se
signale.

**4. Une pièce en trop est un point de recoupement offert.** Pas de certificat
« au cas où », pas de mode opératoire de la bonne famille mais de la mauvaise
configuration.

**5. Le bordereau de travail ne part pas avec le dossier.**

---

## 1. Relever l'arborescence attendue

Le destinataire demande souvent « la même arborescence que le dossier
précédent ». **Le lui demander, ou la relever sur le dernier dossier remis au
même client** — ne pas inventer une structure.

```bash
find "<dernier dossier remis>" -type d | sort
```

Chercher aussi la demande explicite dans les courriels du chantier : c'est
souvent là qu'elle est écrite.

## 2. Inventorier avant de copier

```bash
find "<chantier>" -not -path "*/.*" | sed 's|^\./||' | sort
```

Puis, pour chaque rubrique de la structure cible, noter : présent / absent / à
vérifier. **Ne rien copier tant que l'inventaire n'est pas fait** — sinon on
copie ce qui traîne plutôt que ce qui est dû.

## 3. Dépouiller les courriels du chantier

**C'est une étape du montage, pas une finition.** On y trouve :
- la validation du maître d'ouvrage sur l'essai de pression, qui n'existe
  souvent que là ;
- des certificats arrivés par mail et jamais classés ;
- **quelle version d'un fichier est la bonne** quand plusieurs ont été envoyées ;
- ce qui a **déjà été transmis**, et à quelle date — décisif si on corrige ensuite
  un document ;
- les réserves à solder.

Comparer les **pièces jointes** des courriels d'envoi avec ce qui est classé :
c'est le recoupement qui attrape les certificats oubliés.

## 4. Les recoupements, dans cet ordre

1. **N° de série des instruments** du rapport d'essai contre les certificats
   d'étalonnage joints. Un rapport produit avec un autre instrument rend les
   certificats sans objet.
2. **Poinçons du cahier** contre les certificats disponibles, **aux dates de
   soudage** — pas à la date du jour.
3. **Épaisseurs et matériaux** des certificats matière contre la plage du mode
   opératoire. C'est là qu'on découvre qu'un mode opératoire écrit pour une
   épaisseur nominale unique ne décrit pas la moitié des joints.
4. **Nombre de pièces spéciales** au cahier contre le nombre de lignes aux
   rapports CND. Un écart = des soudures contrôlées et absentes du registre.
5. **Les deux numérotations du cahier** entre elles et contre les rapports CND :
   doublons, transpositions.

Toute question de **plage de qualification ou de mode opératoire** part chez
l'agent `soudure`. Ne jamais trancher une lecture de norme soi-même.

## 5. Imprimer un courriel au dossier

Extraire le contenu réel, puis rendre en PDF — ne pas retaper de mémoire.
Reprendre **l'en-tête complet** : expéditeur, destinataires, copie, date, objet,
nombre de pièces jointes, et le fil antérieur s'il porte le contexte.

```javascript
// depuis le webmail : le corps est dans une iframe
const f = document.querySelector('iframe');
const corps = f.contentDocument.body.innerText.trim();
```
Puis composer un HTML sobre et :
```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless \
  --disable-gpu --no-pdf-header-footer --print-to-pdf="sortie.pdf" "file://source.html"
```
Titrer la pièce « **copie du message** » : c'est ce qu'elle est.

## 6. Corriger un classeur de production

**⛔ Ne pas utiliser openpyxl en écriture sur un classeur formaté** : il perd les
zones d'impression et les objets graphiques. Il est parfait en **lecture** pour
repérer les cellules.

Patcher le XML du `.xlsx` à la place — tout le reste du fichier est préservé
octet pour octet :

```python
import zipfile, re, os
z = zipfile.ZipFile(SRC)
ss = z.read('xl/sharedStrings.xml').decode('utf8')
items = re.findall(r'<si>.*?</si>', ss, re.S)
def idx(t):                                   # index d'une chaîne partagée
    for i, it in enumerate(items):
        if re.sub(r'<[^>]+>', '', it) == t: return i
# ajouter une chaîne absente : l'insérer avant </sst> ET incrémenter
# count et uniqueCount, sinon Excel refuse d'ouvrir le fichier
```

Points d'attention :
- **Ne jamais remplacer une chaîne partagée globalement** : la même valeur sert
  souvent dans plusieurs colonnes (un poinçon de soudeur est aussi une initiale
  d'inspecteur). Cibler **la cellule**, colonne par colonne.
- **Conserver l'attribut de style `s="…"`** de la cellule remplacée.
- Une ligne peut exister sans les cellules visées : insérer la cellule **dans
  l'ordre des colonnes**, sinon Excel la rejette.
- Relire ensuite avec openpyxl pour vérifier.

## 7. Régénérer le PDF depuis Excel ou Word

> ⛔ **Excel et Word refusent d'écrire un PDF dans un dossier iCloud** — erreur de
> paramètre (-50) à chaque tentative, alors que l'ouverture du fichier source
> fonctionne. Écrire dans un dossier local, puis déplacer.

```bash
osascript -e 'tell application "Microsoft Excel" to quit saving no'; sleep 2
osascript -e "tell application \"Microsoft Excel\" to open workbook workbook file name \"$X\""
sleep 4
osascript -e "tell application \"Microsoft Excel\" to save workbook as active workbook \
  filename \"$HOME/Downloads/sortie.pdf\" file format PDF file format with overwrite"
```
Le verbe est **`save workbook as`**, pas `save as` — ce dernier renvoie une
erreur de paramètre.

L'export emporte **tous les onglets**, y compris les onglets de calcul internes.
Retirer les pages en trop et vérifier que le nombre de pages correspond à la
version d'origine :
```python
import fitz
d = fitz.open(src)
if d.page_count == N+1: d.delete_page(N)
```

Si l'automatisation bloque, **rendre la pièce en HTML puis PDF avec Chrome
headless**, en réutilisant le logo extrait du document d'origine
(`unzip -j doc.docx "word/media/image1.jpg"`).

## 8. Avant de remettre

- [ ] Chaque pièce correspond à ce qui a été exécuté, et **rien de plus**
- [ ] Les recoupements du §4 sont faits et notés
- [ ] Les sauvegardes `_AVANT-CORRECTION_*` sont **hors** du dossier remis
- [ ] Le bordereau de travail interne est supprimé
- [ ] Les documents corrigés qui avaient déjà été transmis sont signalés comme
      remplaçant les précédents
- [ ] `relecteur` et `gardien-confidentialite` sont passés
- [ ] Le rapport de fin de travaux est daté et **relu par celui qui le signe** —
      c'est une attestation, elle ne se délègue pas
