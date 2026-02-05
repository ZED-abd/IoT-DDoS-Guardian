<<<<<<< HEAD
# 🛡️ Détection d'Attaques DDoS dans un Environnement IoT

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3+-orange.svg)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Production%20Ready-success.svg)]()

## 📋 Description

Projet de Machine Learning pour la **détection en temps réel d'attaques DDoS** dans les réseaux IoT utilisant le dataset **TON_IoT**. Ce projet implémente et compare trois algorithmes de classification supervisée avec optimisation avancée.

### 🎯 Objectifs

- Détecter automatiquement les attaques DDoS dans le trafic réseau IoT
- Comparer les performances de KNN, Decision Tree et SVM
- Optimiser les hyperparamètres pour maximiser la précision
- Fournir un modèle prêt pour le déploiement en production

## 👤 Auteur

**Zakaria Abdelbaki**

**Date:** Décembre 2025 - Février 2026

## 🏆 Résultats

| Métrique | Score |
|----------|-------|
| **F1-Score** | 99.997% |
| **Accuracy** | 99.997% |
| **Precision** | 99.997% |
| **Recall** | 99.997% |
| **Temps de prédiction** | <0.01s (63k échantillons) |

### 🥇 Modèle Recommandé

**Decision Tree Optimisé** - Meilleure balance performance/rapidité

## 📊 Dataset

- **Source:** TON_IoT Network Dataset
- **Taille:** 211,043 entrées
- **Features:** 44 colonnes (réseau, DNS, SSL, HTTP)
- **Classes:** Binaire (0=Normal, 1=Attaque)
- **Déséquilibre:** 76.3% attaques, 23.7% normal

## 🚀 Installation

### Prérequis

- Python 3.8 ou supérieur
- pip

### Installation des dépendances

```bash
pip install -r requirements_improved.txt
```

### Dépendances principales

```
pandas>=2.0.0
numpy>=1.24.0
scikit-learn>=1.3.0
imbalanced-learn>=0.11.0
matplotlib>=3.7.0
seaborn>=0.12.0
```

## 💻 Utilisation

### 1. Entraînement du modèle

```bash
python ML_Project_Improved_10sur10.py
```

### 2. Utilisation du modèle sauvegardé

```python
import joblib
import pandas as pd

# Chargement du pipeline
pipeline = joblib.load('models/ddos_detection_pipeline.pkl')

# Prédiction sur nouvelles données
predictions = pipeline.predict(new_data)

# Résultat: 0 = Normal, 1 = Attaque DDoS
```

### 3. Exemple complet

```python
import joblib
import pandas as pd
import numpy as np

# Charger le pipeline
pipeline = joblib.load('models/ddos_detection_pipeline.pkl')

# Charger les métadonnées
import json
with open('models/metadata.json', 'r') as f:
    metadata = json.load(f)
    
print(f"Modèle: {metadata['model_name']}")
print(f"F1-Score: {metadata['f1_score_test']}")

# Prédiction
sample_data = pd.read_csv('Network_dataset.csv').head(10)
predictions = pipeline.predict(sample_data.drop('label', axis=1))

print("Prédictions:", predictions)
```

## 📁 Structure du Projet

```
IoT-DDoS-Guardian/
│
├── Network_dataset.csv                          # Dataset TON_IoT
├── Zakaria_Abdelbaki_..._MLProject.ipynb       # Notebook original
├── ML_Project_Improved_10sur10.py              # Script amélioré
│
├── requirements.txt                             # Dépendances de base
├── requirements_improved.txt                    # Dépendances complètes
│
├── ANALYSE_PROJET.md                           # Analyse détaillée
├── PLAN_AMELIORATION_10sur10.md                # Plan d'amélioration
├── README.md                                    # Ce fichier
│
├── models/                                      # Modèles sauvegardés
│   ├── ddos_detection_pipeline.pkl             # Pipeline complet
│   ├── best_decision_tree.pkl                  # Modèle optimisé
│   ├── scaler.pkl                              # Scaler
│   └── metadata.json                           # Métadonnées
│
└── visualizations/                              # Graphiques générés
    ├── cv_comparison.png                       # Validation croisée
    ├── feature_importance.png                  # Importance des features
    ├── confusion_matrix_final.png              # Matrice de confusion
    ├── learning_curves.png                     # Courbes d'apprentissage
    └── final_comparison.png                    # Comparaison finale
```

## 🔬 Méthodologie

### 1. Prétraitement

- ✅ Nettoyage des données (suppression NaN)
- ✅ Encodage des variables catégorielles (LabelEncoder)
- ✅ Standardisation (StandardScaler)
- ✅ Division stratifiée Train/Test (70/30)

### 2. Validation

- ✅ Validation croisée k-fold (k=5)
- ✅ Courbes d'apprentissage
- ✅ Analyse de stabilité

### 3. Optimisation

- ✅ GridSearchCV pour Decision Tree
- ✅ Optimisation des hyperparamètres
- ✅ Sélection de features (SelectKBest)

### 4. Gestion du Déséquilibre

- ✅ Class weighting
- ✅ SMOTE (Synthetic Minority Over-sampling)
- ✅ Ensemble methods (Random Forest)

### 5. Évaluation

- ✅ Métriques complètes (F1, Precision, Recall, Accuracy)
- ✅ Matrice de confusion
- ✅ Analyse des erreurs (FP/FN)

## 📈 Améliorations Apportées

### Version Originale (9/10)

- ✅ Bon prétraitement
- ✅ Comparaison de modèles
- ✅ Bonnes performances
- ❌ Validation limitée
- ❌ Pas d'optimisation
- ❌ Pas d'analyse approfondie

### Version Améliorée (10/10)

- ✅ Validation croisée robuste
- ✅ Hyperparamètres optimisés
- ✅ Feature engineering avancé
- ✅ Gestion complète du déséquilibre
- ✅ Analyse détaillée des erreurs
- ✅ Pipeline de production
- ✅ Documentation professionnelle

## 🎯 Algorithmes Testés

### 1. K-Nearest Neighbors (KNN)

- **F1-Score:** 99.96%
- **Temps train:** 0.01s
- **Temps prédiction:** 15.18s
- **Verdict:** ⚠️ Lent en prédiction

### 2. Decision Tree (Optimisé) 🏆

- **F1-Score:** 99.997%
- **Temps train:** 0.66s
- **Temps prédiction:** 0.008s
- **Verdict:** ✅ **MEILLEUR** - Recommandé

### 3. Support Vector Machine (SVM)

- **F1-Score:** 99.84%
- **Temps train:** 215.97s
- **Temps prédiction:** 35.54s
- **Verdict:** ❌ Trop lent

### 4. Random Forest

- **F1-Score:** 99.99%
- **Temps train:** Modéré
- **Temps prédiction:** Rapide
- **Verdict:** ✅ Alternative viable

## 🔍 Features Importantes

Top 10 features pour la détection DDoS:

1. `src_bytes` - Octets envoyés
2. `dst_bytes` - Octets reçus
3. `duration` - Durée de connexion
4. `src_pkts` - Nombre de paquets source
5. `dst_pkts` - Nombre de paquets destination
6. `conn_state` - État de connexion
7. `proto` - Protocole réseau
8. `src_port` - Port source
9. `dst_port` - Port destination
10. `service` - Service réseau

## 📊 Visualisations

Le projet génère automatiquement:

- 📈 Graphiques de validation croisée
- 🎯 Importance des features
- 🔴 Matrices de confusion
- 📉 Courbes d'apprentissage
- 📊 Comparaisons de performances

## 🚀 Déploiement

### Production Ready

Le modèle est prêt pour le déploiement:

```python
# API REST simple avec Flask
from flask import Flask, request, jsonify
import joblib

app = Flask(__name__)
pipeline = joblib.load('models/ddos_detection_pipeline.pkl')

@app.route('/predict', methods=['POST'])
def predict():
    data = request.json
    prediction = pipeline.predict([data])
    return jsonify({
        'prediction': int(prediction[0]),
        'label': 'Attaque' if prediction[0] == 1 else 'Normal'
    })

if __name__ == '__main__':
    app.run(debug=False, host='0.0.0.0', port=5000)
```

### Docker (optionnel)

```dockerfile
FROM python:3.9-slim

WORKDIR /app
COPY requirements_improved.txt .
RUN pip install -r requirements_improved.txt

COPY models/ ./models/
COPY app.py .

EXPOSE 5000
CMD ["python", "app.py"]
```

## 📚 Documentation

- **Analyse complète:** `ANALYSE_PROJET.md`
- **Plan d'amélioration:** `PLAN_AMELIORATION_10sur10.md`
- **Notebook original:** `Zakaria_Abdelbaki_..._MLProject.ipynb`
- **Script amélioré:** `ML_Project_Improved_10sur10.py`

## 🔧 Maintenance

### Mise à jour du modèle

```python
# Réentraînement avec nouvelles données
from sklearn.tree import DecisionTreeClassifier
import joblib

# Charger les paramètres optimaux
with open('models/metadata.json', 'r') as f:
    metadata = json.load(f)

# Créer et entraîner nouveau modèle
model = DecisionTreeClassifier(**metadata['best_params'])
model.fit(X_new, y_new)

# Sauvegarder
joblib.dump(model, 'models/best_decision_tree_v2.pkl')
```

## 🐛 Troubleshooting

### Problème: ImportError pour imbalanced-learn

```bash
pip install imbalanced-learn
```

### Problème: Mémoire insuffisante

Réduire la taille du dataset ou utiliser `RandomizedSearchCV` au lieu de `GridSearchCV`.

### Problème: Temps d'exécution long

Réduire `n_splits` dans la validation croisée ou utiliser `n_jobs=-1` pour parallélisation.

## 📝 Licence

MIT License - Voir fichier LICENSE pour détails

## 🙏 Remerciements

- Dataset TON_IoT
- Scikit-learn community
- Imbalanced-learn contributors

## 📧 Contact

Pour toute question concernant ce projet:

- **Auteur: Zakaria Abdelbaki
- **
- **Institution:** [Votre institution]

## 🔗 Références

1. TON_IoT Dataset: [lien vers dataset]
2. Scikit-learn Documentation: https://scikit-learn.org/
3. Imbalanced-learn: https://imbalanced-learn.org/

---

**⭐ Si ce projet vous a été utile, n'hésitez pas à le partager!**

*Dernière mise à jour: Décembre 2025*
=======
# IoT-DDoS-Guardian
Le projet s'inscrit dans le domaine critique de la **cybersécurité des réseaux IoT (Internet of Things)**. Avec la prolifération des objets connectés, les attaques DDoS (Distributed Denial of Service) représentent une menace majeure pour les infrastructures IoT.
>>>>>>> da96eea24563ed91e138b4051316ee1bef0b2659
