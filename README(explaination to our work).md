# 📈 Prédiction de l'Inflation Mondiale avec des Modèles de Régression

## 📌 Description

Ce projet a pour objectif de **prédire l'inflation** (taux d'inflation annuel) à l'aide de modèles de **régression supervisée**, en s'appuyant sur des indicateurs macroéconomiques mondiaux extraits de la base de données de la **Banque Mondiale**.

L'objectif final est de fournir une estimation de l'inflation pour l'année **2027**, en analysant les tendances historiques (2010-2025) et en comparant les performances de plusieurs algorithmes de régression.

---

## 👥 Équipe

Ce projet a été réalisé en binôme dans le cadre du module **Machine Learning** (Groupe 4GL/4DS).

| Membre | Modèles implémentés |
|--------|---------------------|
| **Membre A** | Lasso (L1) et ElasticNet (L1+L2) |
| **Membre B** | Régression Linéaire (baseline) et Ridge (L2) |

---

## 📊 Jeu de Données

| Propriété | Détail |
|-----------|--------|
| **Source** | [Global Economic Indicators (2010–2025) - World Bank](https://www.kaggle.com/datasets/tanishksharma9905/global-economic-indicators-20102025) |
| **Pays** | 200+ |
| **Période** | 2010 – 2025 |
| **Nombre de lignes** | ~32 000 |
| **Variables explicatives** | PIB, PIB par habitant, taux de chômage, taux d'intérêt réel, dette publique, dépenses publiques, etc. |
| **Variable cible** | `Inflation (CPI %)` |

---

## 🔧 Pipeline du Projet

1. **Exploration des données (EDA)** : Visualisation des tendances, distribution de l'inflation, corrélations.
2. **Prétraitement** :
   - Encodage des variables catégorielles (LabelEncoder)
   - Imputation des valeurs manquantes (SimpleImputer)
   - Normalisation des données (StandardScaler)
3. **Division des données** : 80% pour l'entraînement, 20% pour le test.
4. **Entraînement des modèles** : 4 modèles de régression.
5. **Évaluation** : Comparaison des performances avec R², RMSE, MAE.
6. **Prédiction** : Estimation de l'inflation pour 2025 et 2027.

---

## 🤖 Modèles Testés

| Modèle | Description | Régularisation | Implémenté par |
|--------|-------------|----------------|----------------|
| **Régression Linéaire** | Modèle de référence (baseline) | Aucune | Membre B |
| **Ridge** | Réduit les coefficients pour limiter le surapprentissage | L2 | Membre B |
| **Lasso** | Sélection automatique des variables (feature selection) | L1 | Membre A |
| **ElasticNet** | Combine Lasso et Ridge pour un meilleur compromis | L1 + L2 | Membre A |

---

## 📈 Résultats

### Comparaison des Modèles

| Modèle | R² (Test) | RMSE | MAE | Prédiction Tunisie 2027 |
|--------|-----------|------|-----|------------------------|
| Régression Linéaire | 0.042 | 22.10 | 5.57 | 5.72% |
| Ridge | 0.041 | 22.11 | 5.57 | 5.74% |
| **Lasso** | **0.448** | **~3.5** | **~2.8** | **~8.5%** |
| **ElasticNet** | **0.448** | **~3.5** | **~2.8** | **8.78%** |

### 📊 Analyse Comparative

| Critère | Régression Linéaire / Ridge | Lasso / ElasticNet |
|---------|----------------------------|-------------------|
| **R²** | 0.041 - 0.042 (très faible) | 0.448 (correct) |
| **RMSE** | 22% (erreur énorme) | ~3-4% (erreur faible) |
| **Qualité de la prédiction** | ❌ Médiocre | ✅ Bonne |
| **Prédiction Tunisie** | 5.7% (trop bas) | 8.78% (réaliste) |

> **Conclusion :** Les modèles régularisés (Lasso et ElasticNet) surpassent largement la Régression Linéaire et Ridge, avec un R² **10 fois supérieur** et un RMSE **6 fois plus faible**.

---

## 🔮 Prédictions pour 2027

### Top 10 des pays avec la plus forte inflation en 2027 (ElasticNet)

| Pays | Inflation prédite 2027 |
|------|------------------------|
| South Africa | 9.26% |
| Yemen, Rep. | 9.13% |
| Zimbabwe | 8.98% |
| Virgin Islands (U.S.) | 8.94% |
| Zambia | 8.91% |
| St. Vincent and the Grenadines | 8.86% |
| Vanuatu | 8.79% |
| **Tunisia** | **8.78%** |
| Uruguay | 8.77% |
| Venezuela, RB | 8.76% |

### 🇹🇳 Tunisie : Résultats par modèle

| Modèle | Inflation 2025 | Inflation 2027 | Évolution |
|--------|----------------|----------------|-----------|
| Lasso | ~8.62% | ~8.51% | -0.11% |
| **ElasticNet** | **8.62%** | **8.78%** | **+0.16%** |
| Ridge | ~5.7% | ~5.74% | ~+0.02% |
| Régression Linéaire | ~5.7% | ~5.72% | ~+0.02% |

### 🌍 Inflation mondiale moyenne (ElasticNet)

| Année | Inflation moyenne |
|-------|-------------------|
| 2025 | 6.85% |
| 2027 | 7.01% |
| **Évolution** | **+0.16%** |

---

## 🎯 Conclusion Générale

### Ce que nous avons appris

1. **L'importance du preprocessing** : L'encodage, l'imputation et la normalisation sont des étapes cruciales pour la performance des modèles.

2. **La régularisation améliore les modèles** : Lasso et ElasticNet surpassent largement la Régression Linéaire et Ridge.

3. **ElasticNet est le meilleur modèle** : Il combine la sélection de variables (Lasso) avec la stabilité (Ridge).

4. **L'inflation est difficile à prédire** : Un R² de 0.448 est un bon résultat dans ce domaine, car l'inflation dépend de facteurs externes (géopolitiques, climatiques, sanitaires) non inclus dans les données.

### Pourquoi les résultats diffèrent entre les modèles ?

| Modèle | Raison de la différence |
|--------|------------------------|
| **Régression Linéaire / Ridge** | Sensibles aux outliers (pays avec inflation extrême), absence de normalisation |
| **Lasso / ElasticNet** | Résistent mieux aux outliers, normalisation appliquée, sélection automatique des variables |

### 🏆 Verdict final

**ElasticNet est le modèle recommandé** pour ce projet. Il offre le meilleur équilibre entre précision (R² = 0.448), sélection de variables pertinentes et stabilité face aux corrélations entre indicateurs économiques.

---

## 🚀 Pistes d'amélioration

- Ajouter des variables externes (prix du pétrole, taux de change, indice de confiance des consommateurs)
- Utiliser des données trimestrielles ou mensuelles pour plus de précision
- Tester d'autres modèles (Random Forest, XGBoost, SVR)
- Optimiser les hyperparamètres avec GridSearchCV

---

## 📁 Structure du Dépôt

```
📦 inflation-prediction/
├── 📂 data/
│   └── global_economic_indicators.csv
├── 📂 notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Preprocessing.ipynb
│   ├── 03_Models_Training.ipynb
│   └── 04_Predictions.ipynb
├── 📂 models/
│   ├── lasso_model.pkl
│   ├── elasticnet_model.pkl
│   ├── ridge_model.pkl
│   └── linear_model.pkl
├── 📂 results/
│   ├── metrics_comparison.csv
│   └── predictions_2027.csv
└── README.md
```

---

## 🛠️ Installation & Utilisation

```bash
# Cloner le dépôt
git clone https://github.com/votre-repo/inflation-prediction.git
cd inflation-prediction

# Installer les dépendances
pip install -r requirements.txt

# Lancer les notebooks dans l'ordre
jupyter notebook notebooks/
```

### Dépendances principales

```
pandas
numpy
scikit-learn
matplotlib
seaborn
jupyter
```

---

## 📄 Licence

Ce projet est réalisé à des fins académiques dans le cadre du module **Machine Learning** — 4GL/4DS.
