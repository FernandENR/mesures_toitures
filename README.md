# Extraction des Surfaces de Toitures

[![Python](https://img.shields.io/badge/Python-3.7%2B-blue)](https://www.python.org/) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Cette application Streamlit extrait et analyse les surfaces de toitures à partir de données cadastrales, puis génère un rapport détaillé au format CSV.

---

## Table des Matières

1. [Prérequis](#prérequis)
2. [Installation](#installation)
3. [Utilisation](#utilisation)
4. [Fonctionnalités](#fonctionnalités)
5. [Structure du Projet](#structure-du-projet)
6. [Configuration](#configuration)
7. [Contribution](#contribution)
8. [Auteurs](#auteurs)
9. [Licence](#licence)

---

## Prérequis

* **Python 3.7+**
* Bibliothèques :

  * `streamlit`, `pandas`, `geopandas`, `shapely`, `pyproj`,
    `requests` et `requests-cache` (optionnel)

> **Astuce** : un environnement virtuel (venv, conda, pipenv) est recommandé.

---

## Installation

```bash
git clone [https://github.com/FernandENR/mesures_toitures](https://github.com/FernandENR/mesures_toitures)
cd Extraction-Toitures
pip install -r requirements.txt
```

---

## Utilisation

1. Préparez un fichier CSV avec au minimum :

   * `code_departement`, `code_commune`, `section`, `plan`
   * `nom_proprietaire`, `forme_juridique`
   * *Optionnel* : `adresse`, `nature_voie`, `nom_voie`, `siren`

2. Lancez l’application :

   ```bash
   streamlit run app.py
   ```

3. Dans l’interface :

   * Téléchargez le CSV d’entrée.
   * Cliquez sur **Démarrer** pour lancer le traitement.

4. Téléchargez le CSV de sortie contenant : forme juridique, propriétaire, SIREN,
   parcelle, nombre de bâtiments, surfaces (min/max/totale), adresse,
   code postal, ville.

---

## Fonctionnalités

* **Chargement** : CSV d’entrée + API cadastrale
* **Géométrie** : transformation WGS84 → Lambert-93 et calcul de surfaces
* **Cache HTTP** : via `requests-cache` pour accélérer les requêtes
* **Normalisation** : standardisation des chaînes et calcul d’ETA
* **Export** : CSV structuré pour analyses ultérieures

---

## Structure du Projet

```
Extraction-Toitures/
├─ app.py                 # Interface Streamlit
├─ requirements.txt       # Dépendances
├─ src/                   # Modules principaux
│  ├─ geo_loader.py      # Chargement géospatial
│  ├─ transform.py       # Projection des coordonnées
│  ├─ surface_calc.py    # Calcul des surfaces
│  └─ utils.py           # Utilitaires (normalisation, ETA)
├─ tests/                 # Tests unitaires
│  └─ test_surface.py
├─ data/                  # Exemples de données
│  └─ sample_input.csv
└─ LICENSE
```

---

## Configuration

Les paramètres (cache, URL/API, clés) se trouvent dans `src/config.py`.

---

## Contribution

Les contributions sont les bienvenues ! Une simple Pull Request suffit.

---

## Auteurs

* **Votre Nom** – Développeur principal

---

## Licence

Ce projet est sous licence MIT. Voir [LICENSE](LICENSE).
