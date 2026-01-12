# 🛡️ Système de Détection d'Intrusions (IDS) basé sur le Deep Learning

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10+-orange.svg)](https://www.tensorflow.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Projet académique** - Ingénierie des Réseaux Intelligents et Cybersécurité  
> **Module**: Machine Learning/Deep Learning  
> **Année**: 2025-2026  
> **Encadré par**: Pr. EL Bannay

## 👤 Auteur

- **Hammouch Laïla**

## 📋 Présentation du projet

Ce projet implémente un système de détection d'intrusions (IDS) moderne utilisant une architecture hybride **CNN + BiLSTM + Attention** avec **Focal Loss pondérée** pour détecter 5 types d'attaques réseau sur le dataset NSL-KDD.

### 🎯 Objectifs

- ✅ Détection multiclasse d'attaques réseau (Normal, DoS, Probe, R2L, U2R)
- ✅ Amélioration de la détection des classes rares
- ✅ Gestion du déséquilibre de classes
- ✅ Pipeline automatisé end-to-end
- ✅ Dashboard de surveillance temps réel

## 🏗️ Architecture du modèle
```
Input (n_features, 1)
    ↓
CNN Block 1 (128 filters)
    → Extraction de patterns locaux
    ↓
CNN Block 2 (256 filters)
    → Réduction du bruit
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
2. **Architecture hybride** : CNN + BiLSTM + Multi-Head Attention
3. **SMOTE intelligent** : Oversampling des classes minoritaires
4. **Pipeline automatisé** : De la donnée brute au dashboard

## 📊 Résultats

### Performances globales

| Métrique | Score |
|----------|-------|
| **Accuracy** | **75.17%** |
| Macro F1-Score | 0.5215 |
| Weighted F1 | 0.7187 |
| Matthews Correlation | 0.6284 |

### Performances par classe

| Classe | Precision | Recall | F1-Score | Support |
|--------|-----------|--------|----------|---------|
| Normal | 68.90% | 92.52% | 0.7898 | 9,711 |
| DoS | 88.49% | 81.98% | 0.8511 | 7,458 |
| Probe | 80.40% | 65.22% | 0.7202 | 2,421 |
| R2L | 41.88% | 9.37% | 0.1531 | 2,754 |
| U2R | 71.43% | 5.00% | 0.0935 | 200 |

### 📈 Interprétation des résultats

- ✅ **Excellente détection** des classes majoritaires (Normal, DoS)
- ✅ **Performance cohérente** avec le dataset NSL-KDD
- ✅ **MCC élevé (0.6284)** indique une bonne corrélation entre prédictions et labels
- ⚠️ **Classes rares (R2L, U2R)** fortement impactées par le déséquilibre
- 📊 **Amélioration significative** par rapport aux modèles de base

## 🎨 Dashboard de Surveillance

**Fonctionnalités du dashboard** :
- 📊 **Statistiques en temps réel** : Trafic total, attaques détectées, taux de détection
- 🚨 **Alertes critiques** : Avec IP source, niveau de confiance et sévérité
- 📈 **Timeline 24h** : Distribution temporelle des attaques
- 🎯 **Performance détaillée** : Métriques par classe d'attaque
- 🗺️ **Géolocalisation** : Sources des attaques par pays

## 📖 Dataset

**NSL-KDD** : Version améliorée du dataset KDD Cup 1999

| Caractéristique | Valeur |
|----------------|--------|
| Train | 125,973 échantillons |
| Test | 22,544 échantillons |
| Features | 41 + 1 label |
| Classes | 5 (Normal, DoS, Probe, R2L, U2R) |

### Distribution des classes

| Classe | Train | Test | Déséquilibre |
|--------|-------|------|--------------|
| Normal | 67,343 | 9,711 | ✅ Majoritaire |
| DoS | 45,927 | 7,458 | ✅ Fréquent |
| Probe | 11,656 | 2,421 | ⚠️ Moyen |
| R2L | 995 | 2,754 | ❌ Rare |
| U2R | 52 | 200 | ❌ Très rare (0.04%) |

### Prétraitement appliqué

1. **Feature Engineering** : Création de 10+ features dérivées
2. **One-Hot Encoding** : Variables catégorielles (protocol_type, service, flag)
3. **RobustScaler** : Normalisation résistante aux outliers
4. **SMOTE** : Équilibrage des classes minoritaires (R2L, U2R)

## 🛠️ Technologies utilisées

- **Deep Learning** : TensorFlow/Keras
- **ML Classique** : Scikit-learn, Imbalanced-learn (SMOTE)
- **Visualisation** : Matplotlib, Seaborn, Chart.js
- **Dashboard** : React, Recharts, Tailwind CSS
- **Automatisation** : Python, Bash

## 📚 Documentation

- [📄 Présentation de soutenance](Présentation de soutenance.pdf)

*Toutes les visualisations (matrice de confusion, courbes ROC, courbes d'entraînement, dashboard) sont disponibles dans la présentation.*

## 🔬 Comparaison avec l'état de l'art

| Modèle | Architecture | Accuracy | F1 (U2R) |
|--------|--------------|----------|----------|
| **Notre modèle** | CNN+BiLSTM+Attention | **75.17%** | **0.093** |
| Baseline CNN | CNN simple | 72.4% | 0.061 |
| LSTM seul | LSTM | 73.1% | 0.074 |
| Random Forest | Ensemble | 71.8% | 0.052 |
| SVM | Classique | 69.5% | 0.049 |

### 📊 Analyse comparative

- ✅ **Amélioration globale** de +2-5% par rapport aux modèles de base
- ✅ **Gain relatif sur U2R** : +52% par rapport à CNN simple
- ✅ **Architecture hybride** plus expressive que les approches simples
- ✅ **Pipeline automatisé** et reproductible

## 🚀 Perspectives d'amélioration

1. **Datasets récents** : Test sur CIC-IDS2017/2018, UNSW-NB15
2. **Modèles avancés** : Transformers, Graph Neural Networks
3. **Explainability** : SHAP/LIME pour interpréter les décisions
4. **Déploiement** : Production temps réel avec monitoring
5. **AutoML** : Hyperparameter tuning automatique (Optuna, Keras Tuner)
6. **Augmentation de données** : Techniques avancées pour classes rares

## 📝 Citation

Si vous utilisez ce travail, merci de citer :
```bibtex
@project{ids_deep_learning_2025,
  title={Système de Détection d'Intrusions basé sur le Deep Learning},
  author={Hammouch, Laïla},
  year={2025},
  institution={Ingénierie des Réseaux Intelligents et Cybersécurité},
  supervisor={Pr. EL Bannay},
  note={CNN + BiLSTM + Attention avec Focal Loss}
}
```

## 📄 License

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 🤝 Remerciements

- **Pr. EL Bannay** pour son encadrement et ses conseils
- **NSL-KDD Dataset** pour les données de recherche
- Communauté **TensorFlow** et **Scikit-learn**
- **Canadian Institute for Cybersecurity** pour NSL-KDD

## 🔒 Note sur le code source

Ce dépôt contient uniquement les **résultats** et la **documentation** du projet.

**Le code source complet est disponible sur demande pour** :
- Collaboration académique
- Reproduction des résultats
- Validation scientifique
- Recherche en cybersécurité

## 📧 Contact

**Hammouch Laïla**  
📧 Email : lailahammouch38@gmail.com  
🎓 Ingénierie des Réseaux Intelligents et Cybersécurité  
📅 Année universitaire 2025-2026

---

<div align="center">

**IDS Deep Learning** : Une solution moderne pour la cybersécurité

*Développé avec ❤️ en utilisant TensorFlow, React et Python*

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Deep Learning](https://img.shields.io/badge/Deep%20Learning-CNN%2BBiLSTM-orange)
![Accuracy](https://img.shields.io/badge/Accuracy-75.17%25-blue)

</div>
