# Mettre à jour le site

Le site est généré par **Jekyll**, que GitHub Pages compile automatiquement à chaque `git push`.
Le contenu est séparé de la mise en page : pour l'alimenter, on ne touche **que** les fichiers ci-dessous.

| Je veux…                                   | Fichier à modifier            |
|--------------------------------------------|-------------------------------|
| Ajouter une actualité                      | `_data/news.yml`              |
| Ajouter une publication                    | `_data/publications.yml`      |
| Ajouter / mettre à jour un projet (page Research) | `_data/projects.yml`   |
| Doctorants, stages de recherche, offres de stage/thèse | `_data/supervision.yml` |
| Cours, formations, supports de cours       | `_data/teaching.yml` (+ fichiers dans `files/teaching/`) |
| Expérience, prix, talks, service           | `_data/cv.yml`                |
| Publications mises en avant (accueil)      | `featured: true` dans `_data/publications.yml` |
| Texte de présentation (bio, responsabilités) | `index.md`                  |
| Nom, fonctions sous le nom, email, liens   | `_config.yml`                 |
| CV PDF (optionnel)                         | déposer `files/CV_HakimSMH.pdf` et décommenter `cv_pdf` dans `_config.yml` (version publique, sans coordonnées personnelles) |

Images : `img/pubs/` (vignettes de publications) et `img/projects/`. Largeur ~900 px suffit.

## Exemples

Nouvelle actualité (en haut de `_data/news.yml`) :

```yaml
- date: Feb 2027
  title: Paper accepted at IEEE VR 2027
  where: Saint-Malo, France
  text: Joint work with [Gaël Van der Lee](https://...) on EEG markers of presence.
```

Nouvelle publication (en haut de `_data/publications.yml`, la liste est triée de la plus récente à la plus ancienne) :

```yaml
- title: "Titre de l'article"
  authors: A. Auteur, H. Si-Mohammed, B. Auteur
  venue: IEEE Transactions on Visualization and Computer Graphics
  year: 2027
  type: journal          # journal | conference | other
  doi: 10.1109/XXXX
  pdf: https://hal.science/hal-XXXXXXX/document
```

Ouvrir une offre de stage/thèse : dans `_data/supervision.yml`, passer `positions.open` à `true` et remplir `offers`.

Publier un support de cours : déposer le fichier dans `files/teaching/`, puis ajouter un bloc à `resources:` en bas de `_data/teaching.yml` (un exemple commenté y figure ; enlever les `[]` après `resources:`). La section « Course materials & resources » de la page Teaching apparaît automatiquement dès qu'il y a au moins une ressource. Pour lier un cours du tableau à ses supports, ajouter `materials: /files/teaching/...` (ou `/teaching.html#resources`) au cours concerné.

## Règles YAML à connaître

- L'indentation compte (2 espaces, pas de tabulation).
- Mettre le texte entre guillemets `"…"` s'il contient `:` ou commence par `*`, `[` ou `“`.
- `text`, `value` et les listes du CV acceptent le Markdown : `**gras**`, `*italique*`, `[lien](https://…)`.

## Prévisualiser en local

```bash
jekyll serve --livereload
```

Puis ouvrir http://localhost:4000. Après modification de `_config.yml`, relancer la commande.
