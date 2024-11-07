
# Projet d'alignement de corpus bilingue avec BERTalign

## Bertalign, un aligneur sophistiqué

Bertalign utilise BERT et Transformers, impliquant souvent des techniques d'apprentissage automatique telles que les réseaux neuronaux. 
Ils gèrent mieux le contexte, la sémantique et les structures syntaxiques, permettant une compréhension plus approfondie du langage et des alignements plus précis. Ceux-ci peuvent inclure des modèles tels que des architectures basées sur des Transformers,qui peuvent gérer efficacement la désambiguïsation du sens des mots, les expressions idiomatiques et les significations contextuelles. 

Bertalign est conçu pour faciliter la construction de corpus parallèles multilingues et de mémoires de traduction, qui ont une large gamme d'applications dans la recherche liée à la traduction, comme les études de traduction basées sur des corpus, la linguistique contrastive, la traduction assistée par ordinateur, la formation des traducteurs et la traduction automatique.
Approche : Bertalign utilise des transformers de phrases pour représenter les phrases sources et cibles, afin que les phrases sémantiquement similaires dans différentes langues soient mappées sur des espaces vectoriels similaires. Ensuite, un algorithme en deux étapes basé sur la programmation dynamique est exécuté : 
1) L'étape 1 trouve les alignements 1-1 pour les points d'ancrage approximatifs 
2) L'étape 2 limite le chemin de recherche aux points d'ancrage et extrait tous les alignements valides avec des relations 1-plusieurs, plusieurs-1 ou plusieurs-à-plusieurs entre les phrases source et cible.

Langues prises en charge : Alignement entre 25 langues (ex. chinois (zh), anglais (en), français (fr)). Importez simplement Bertalign et initialisez-le avec le texte source et cible, qui détectera automatiquement la langue source et cible et divisera les deux textes en phrases. Ensuite, imprimez le résultat avec print_sents().

Performances : Selon Thompson & Koehn (2019), Bertalign obtient des résultats plus précis sur Text+Berg.(https://aclanthology.org/D19-1136/)


## Description
Ce projet utilise BERTalign pour effectuer l'alignement automatique entre deux corpus bilingues. BERTalign exploite les embeddings contextuels de BERT pour établir des correspondances précises entre les phrases de différentes langues.

## Description des corpus
Le projet travaille sur deux corpus parallèles, déja traités, concernant les emprunts lexicaux non assimilés, proposés par nos professeur Lichao Zhu (https://cv.hal.science/lichao-zhu). 
La transcription de ces corpus pour l'alignement est basée sur un exposé portant sur cet article : https://aclanthology.org/2022.acl-long.268.pdf.

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

## Installation
```bash
# Création de l'environnement virtuel
python -m venv venv
source venv/bin/activate  
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
│   ├── align.ipynb
│   └── evaluate.ipynb
└── README.md
```

## Utilisation
1. **Lancement de l'alignement** :
   Ouvrez le notebook Jupyter `scripts/align.ipynb` dans Jupyter et exécutez chaque cellule pour effectuer le processus d'alignement.

2. **Évaluation des résultats** :
   Ouvrez le notebook Jupyter `scripts/evaluate.ipynb` dans Jupyter et exécutez chaque cellule pour évaluer les résultats d'alignement dans `data/aligned_output.txt`.




## Résultats
Les résultats de l'alignement sont stockés dans le dossier `data/aligned_output` sous format :
- Fichiers alignés au format txt
- Métriques d'alignement
- Logs détaillés

### Évaluation des résultats
Pour évaluer la qualité de l'alignement, nous avons utilisé la métrique BLEU (Bilingual Evaluation Understudy). La métrique BLEU mesure la proximité entre les phrases alignées et les références, en se basant sur le recouvrement n-grammes.

La formule BLEU est la suivante :

```
BLEU = BP * exp(Σ(wn * log(pn)))
```

Où :
- BP est le "Brevity Penalty" qui pénalise les alignements trop courts
- wn sont les poids des n-grammes (typiquement w1=0.25, w2=0.25, w3=0.25, w4=0.25)
- pn sont les précisions des n-grammes

La valeur BLEU varie entre 0 et 1, 1 indiquant une correspondance parfaite entre l'alignement et la référence.

Nous avons calculé les scores BLEU moyens pour l'ensemble du corpus aligné, ainsi que des scores par paire de phrases alignées. Ces métriques nous permettent d'évaluer la qualité globale de l'alignement et d'identifier les zones qui nécessiteraient des ajustements.

## Dépannage
Solutions aux problèmes courants :
- Erreurs de mémoire
- Problèmes d'encodage
- Incompatibilités de versions
- Erreurs courantes de BERTalign

