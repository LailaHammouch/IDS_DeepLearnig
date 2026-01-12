# 🛡️ Système de Détection d'Intrusions (IDS) basé sur le Deep Learning

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10+-orange.svg)](https://www.tensorflow.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Projet académique** - Ingénierie des Réseaux Intelligents et Cybersécurité  
> **Module**: Machine Learning/Deep Learning  
> **Année**: 2025-2026  
> **Encadré par**: Pr. EL Bannay

##  Auteur

- **Hammouch Laïla**


## 📋 Présentation du projet

Ce projet implémente un système de détection d'intrusions (IDS) moderne utilisant une architecture hybride **CNN + BiLSTM + Attention** avec **Focal Loss pondérée** pour détecter 5 types d'attaques réseau sur le dataset NSL-KDD.

### 🎯 Objectifs

- ✅ Détection multiclasse d'attaques réseau (Normal, DoS, Probe, R2L, U2R)
- ✅ Accuracy > 95%
- ✅ Gestion du déséquilibre de classes
- ✅ Pipeline automatisé end-to-end
- ✅ Dashboard de surveillance temps réel

## 🏗️ Architecture du modèle
```
Input (n_features, 1)
    ↓
CNN Blocks (128, 256 filters)
    → Extraction de patterns locaux
    ↓
BiLSTM (128 units)
    → Modélisation temporelle bidirectionnelle
    ↓
Multi-Head Attention
    → Focus sur features importantes
    ↓
Dense Layers (256, 128)
    ↓
Output (5 classes) + Focal Loss
```

### 🔑 Innovations techniques

1. **Focal Loss pondérée** : Gestion optimale du déséquilibre de classes
2. **Architecture hybride** : CNN + BiLSTM + Attention
3. **SMOTE intelligent** : Oversampling des classes minoritaires
4. **Pipeline automatisé** : De la donnée brute au dashboard

## 📊 Résultats

### Performances globales

| Métrique | Score |
|----------|-------|
| **Accuracy** | **95.24%** |
| Macro F1-Score | 0.928 |
| Weighted F1 | 0.952 |
| Matthews Correlation | 0.915 |

### Performances par classe

| Classe | Precision | Recall | F1-Score | Support |
|--------|-----------|--------|----------|---------|
| Normal | 97.8% | 98.1% | 0.980 | 9,711 |
| DoS | 95.9% | 94.0% | 0.950 | 7,458 |
| Probe | 88.6% | 87.0% | 0.878 | 2,421 |
| R2L | 82.3% | 78.9% | 0.806 | 2,754 |
| U2R | 75.1% | 71.5% | 0.733 | 200 |

### 📈 Visualisations

#### Matrice de Confusion
![Matrice de Confusion](resultats/confusion_matrix.png)

#### Courbes d'Entraînement
![Training Curves](resultats/training_curves.png)

#### Courbes ROC
![ROC Curves](resultats/roc_curves.png)



## 🎨 Dashboard de Surveillance

![Dashboard Screenshot](dashboard/dashboard_screenshot.png)

**Fonctionnalités du dashboard** :
- 📊 Statistiques en temps réel (trafic, attaques détectées)
- 🚨 Alertes critiques avec niveau de confiance
- 📈 Timeline des attaques sur 24h
- 🎯 Performance détaillée par classe d'attaque

## 📖 Dataset

**NSL-KDD** : Version améliorée du dataset KDD Cup 1999
- Train : 125,973 échantillons
- Test : 22,544 échantillons
- 41 features + 1 label
- 5 classes d'attaques

### Prétraitement appliqué

1. **Feature Engineering** : Création de 10+ features dérivées
2. **One-Hot Encoding** : Variables catégorielles
3. **RobustScaler** : Normalisation résistante aux outliers
4. **SMOTE** : Équilibrage des classes minoritaires (R2L, U2R)

## 🛠️ Technologies utilisées

- **Deep Learning** : TensorFlow/Keras
- **ML Classique** : Scikit-learn, Imbalanced-learn
- **Visualisation** : Matplotlib, Seaborn, Chart.js
- **Dashboard** : React, Recharts, Tailwind CSS
- **Automatisation** : Python, Bash

## 📚 Documentation


- [Présentation de soutenance](rapport/Présentation de soutenance.pdf)
  

## 🔬 Comparaison avec l'état de l'art

| Modèle | Architecture | Accuracy | F1 (U2R) |
|--------|--------------|----------|----------|
| **Notre modèle** | CNN+BiLSTM+Attention | **95.24%** | **0.733** |
| Baseline CNN | CNN simple | 92.3% | 0.621 |
| LSTM seul | LSTM | 93.1% | 0.658 |
| Random Forest | Ensemble | 91.8% | 0.542 |

## 🚀 Perspectives d'amélioration

1. **Datasets récents** : Test sur CIC-IDS2017/2018
2. **Déploiement** : Production temps réel
3. **AutoML** : Hyperparameter tuning automatique
4. **Explainability** : SHAP/LIME pour interpréter les décisions
5. **Transfer Learning** : Adaptation à d'autres domaines

## 📝 Citation

Si vous utilisez ce travail, merci de citer :
```bibtex
@project{ids_deep_learning_2025,
  title={Système de Détection d'Intrusions basé sur le Deep Learning},
  author={Hammouch, Laïla a},
  year={2025},
  institution={Ingénierie des Réseaux Intelligents et Cybersécurité},
  supervisor={Pr. EL Bannay}
}
```

## 📄 License

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 🤝 Remerciements

- **Pr. EL Bannay** pour son encadrement
- **NSL-KDD Dataset** pour les données
- Communauté TensorFlow et Scikit-learn

---

**Note** : Ce dépôt contient uniquement les résultats et la documentation du projet.  
Le code source est disponible sur demande pour des raisons académiques.

**Contact** : lailahammouch38@gmail.com
