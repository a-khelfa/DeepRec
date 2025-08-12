# DeepRec : Moteur de Recommandation de Contenu par Réseaux Neuronaux
## Présentation du Projet
Ce projet est un moteur de recommandation de films basé sur le jeu de données MovieLens. L'objectif principal est de concevoir, d'entraîner et de comparer plusieurs modèles de systèmes de recommandation, allant des algorithmes classiques (filtrage collaboratif) aux architectures plus modernes basées sur le Deep Learning.

L'analyse comparative des performances (RMSE et MAE) de ces modèles permet d'identifier l'approche la plus performante pour générer des recommandations personnalisées et précises pour les utilisateurs.

## Structure du Projet
Le dépôt est organisé de manière à rendre le code modulaire et les analyses reproductibles.

DeepRec/
├── data/                       # Contient les données brutes et prétraitées
│   ├── movies.csv              # Le dataset des films
│   ├── ratings.csv             # Le dataset des notes
│   ├── deeprec_model.keras     # Le modèle Keras entraîné
│   ├── svd_model.pkl           # Le modèle SVD entraîné
│   └── ... (fichiers de mappings et de prédictions)
├── notebooks/                  # Contient les notebooks Jupyter pour l'analyse
│   ├── 1_EDA_Preprocessing.ipynb
│   ├── 2_Baseline_Models.ipynb
│   ├── 3_DeepLearning_Model_Training.ipynb
│   └── 4_Evaluation_Comparison.ipynb
├── src/                        # Code Python modulaire et réutilisable
│   ├── models/                 # Code pour les architectures de modèles
│   │   └── deep_recommender.py
│   └── utils/                  # Fonctions utilitaires
│       └── data_loader.py
├── .gitattributes              # Fichier pour la gestion des fichiers volumineux avec Git LFS
├── .gitignore
└── README.md                   # Ce fichier

## Installation et Exécution
### Prérequis
- Python 3.11 ou 3.12 (versions supportées par la plupart des bibliothèques)

- Git LFS pour le téléchargement des fichiers de données volumineux.

### Étapes
1. Clonez le dépôt :
```bash
git clone https://github.com/votre_utilisateur/DeepRec.git
cd DeepRec
```

2. Installez Git LFS et assurez-vous qu'il est activé :
```bash
git lfs install
git lfs pull
```

3. Créez et activez un environnement virtuel :
```bash
python -m venv venv
# Sur Windows
venv\Scripts\activate
# Sur macOS/Linux
source venv/bin/activate
```

4. Installez les dépendances :
```bash
pip install -r requirements.txt
```

5. Lancez les notebooks :
```bash
jupyter notebook
```

## Méthodologie et Résultats
### Datasets
Le projet utilise le jeu de données MovieLens, qui contient des notes d'utilisateurs sur des films. Le dataset est divisé en ensembles d'entraînement, de validation et de test.

### Modèles
Trois types de modèles ont été implémentés et comparés :

1. Filtrage Collaboratif Basé sur la Similarité : Une approche classique utilisant les similarités entre utilisateurs ou films pour générer des recommandations.

2. Factorisation Matricielle (SVD) : Un modèle plus performant qui décompose la matrice de notes en matrices latentes d'utilisateurs et de films.

3. Deep Learning (NCF simplifié) : Une approche moderne utilisant des embeddings et un réseau de neurones multicouches pour apprendre des interactions non linéaires entre les utilisateurs et les films.

### Performances
Les performances des modèles sont évaluées en utilisant le RMSE (Root Mean Square Error) et le MAE (Mean Absolute Error). Le tableau ci-dessous résume les résultats :

```markdown
| Modèle | RMSE | MAE |
|-----------|:----------|:----------|
| Filtrage Collaboratif | 1.05 | 0.82 |
| SVD | 0.77 | 0.58 |
| Deep learning | 0.79 | 0.59
```

Note : Les valeurs exactes peuvent varier en fonction de l'entraînement et du dataset.

## Recommandations
Le notebook 4_Evaluation_Comparison.ipynb démontre comment utiliser le modèle de Deep Learning entraîné pour générer une liste de films recommandés pour un utilisateur spécifique, basée sur les notes prédites les plus élevées.

## Améliorations Futures
- Intégrer les métadonnées des films (genres, tags) dans le modèle de Deep Learning pour un système de recommandation hybride.

- Explorer des architectures de Deep Learning plus complexes (par exemple, un auto-encodeur variationnel).

- Déployer le modèle en tant qu'API pour des recommandations en temps réel.