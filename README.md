
# Projet d'alignement de corpus bilingue avec BERTalign

## Description
Ce projet utilise BERTalign pour effectuer l'alignement automatique entre deux corpus bilingues. BERTalign exploite les embeddings contextuels de BERT pour établir des correspondances précises entre les phrases de différentes langues.

## Description des corpus
Le projet travaille sur deux corpus parallèles concernant les emprunts lexicaux non assimilés :

### Corpus source (Anglais)
Transcription d'une présentation académique sur la détection des emprunts lexicaux, incluant :
- Description du phénomène d'emprunt lexical
- Exemples d'emprunts de l'anglais vers l'espagnol (podcast, app, crowdfunding)
- Discussion sur les différences entre emprunts lexicaux et alternance codique
- Aspects linguistiques du phénomène

### Corpus cible (Français)
Traduction française de la présentation, comprenant :
- Terminologie spécialisée du TAL (Traitement Automatique du Langage)
- Adaptation des exemples d'emprunts
- Maintien des termes techniques
- Préservation du style académique


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
git clone https://github.com/bfsujason/bertalign
pip install -r requirements.txt
```

## Structure du projet
```
projet/
├── data/
│   ├── ACL.6060.dev.en-xx.en.source.txt
│   ├── ACL.6060.dev.en-xx.fr.cible.txt
│   └── aligned_output.txt
├── scripts/
│   ├── align.py
│   └── evaluate.py
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



## Résultats
Les résultats de l'alignement sont stockés dans le dossier `data/aligned_output` sous format :
- Fichiers alignés au format txt
- Métriques d'alignement
- Logs détaillés

## Dépannage
Solutions aux problèmes courants :
- Erreurs de mémoire
- Problèmes d'encodage
- Incompatibilités de versions
- Erreurs courantes de BERTalign

