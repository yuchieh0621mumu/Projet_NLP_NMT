
# Projet d'alignement de corpus bilingue avec BERTalign

## Description
Ce projet utilise BERTalign pour effectuer l'alignement automatique entre deux corpus bilingues. BERTalign exploite les embeddings contextuels de BERT pour établir des correspondances précises entre les phrases de différentes langues.

## Prérequis
- Python 3.8+
- PyTorch
- Transformers (Hugging Face)
- BERTalign
- Autres dépendances spécifiques

## Installation
```bash
# Création de l'environnement virtuel
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
.\venv\Scripts\activate  # Windows

# Installation des dépendances
pip install -r requirements.txt
```

## Structure du projet
```
projet/
├── data/
│   ├── corpus_source/
│   ├── corpus_cible/
│   └── aligned_output/
├── scripts/
│   ├── preprocess.py
│   ├── align.py
│   └── evaluate.py
├── config/
│   └── config.yaml
├── requirements.txt
└── README.md
```

## Utilisation
1. Préparation des données :
   ```bash
   python scripts/preprocess.py --source data/corpus_source --target data/corpus_cible
   ```

2. Lancement de l'alignement :
   ```bash
   python scripts/align.py --config config/config.yaml
   ```

3. Évaluation des résultats :
   ```bash
   python scripts/evaluate.py --aligned data/aligned_output
   ```

## Configuration
Le fichier `config/config.yaml` permet de personnaliser les paramètres suivants :
- Langues source et cible
- Modèle BERT à utiliser
- Seuils d'alignement
- Paramètres de prétraitement
- Options d'export

## Résultats
Les résultats de l'alignement sont stockés dans le dossier `data/aligned_output` sous format :
- Fichiers alignés au format TSV
- Métriques d'alignement
- Logs détaillés

## Dépannage
Solutions aux problèmes courants :
- Erreurs de mémoire
- Problèmes d'encodage
- Incompatibilités de versions
- Erreurs courantes de BERTalign

