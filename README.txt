🧬 De Novo Molecular Generation — README

Auteurs : Hiba Mhada & Wijdane Bassiry  
Formation : Master Big Data & Data Science — FSBM, Université Hassan II, Casablanca  
Année universitaire : 2025-2026



📌 Description du projet

Ce projet implémente un pipeline complet de génération de molécules de novo à l'aide de l'API NVIDIA MolMIM (NIM), combinée à des techniques de filtrage chimique, de prédiction de toxicité par Machine Learning, et d'explicabilité (XAI). L'ensemble est présenté via une interface interactive Streamlit.

L'objectif est de générer de nouvelles molécules candidates à partir du dataset ZINC 250k, de les évaluer sur leur qualité (QED, SA Score), leur absence de sous-structures problématiques (filtres PAINS), et leur toxicité potentielle.



🗂️ Structure du dossier


BassiryWijdane_MhadaHiba/
│
├── code/
│   ├── projet_ML_p1.ipynb       # Partie 1 : EDA, preprocessing, génération
│   └── projet_ML_p2.ipynb       # Partie 2 : Filtrage, UMAP, toxicité, Streamlit
│
├── Data/
│   ├── 250k_rndm_zinc_drugs_clean_3.csv   # Dataset source ZINC 250k
│   └── generated_molecules.csv            # Molécules générées par MolMIM
│
├── poster/
│   └── Poster - De Novo Molecular Generation.pdf
│
├── Rapport/
│   └── PROJET ML.pdf
│
└── README.txt  (ce fichier)




🔬 Pipeline du projet

Partie 1 — projet_ML_p1.ipynb

| Étape | Description |
|-------|-------------|
| Chargement des données | Lecture du dataset ZINC 250k (~250 000 molécules au format SMILES) |
| EDA | Calcul des propriétés physico-chimiques (MW, LogP, TPSA, HBD, HBA) via RDKit, visualisations (histogrammes, boxplots, corrélations) |
| Filtrage Lipinski | Application de la Règle des Cinq de Lipinski pour ne conserver que les molécules drug-like |
| Split Train/Test | Division 80/20, sauvegarde des sous-ensembles (train.csv, test.csv) |
| Génération MolMIM | Appel à l'API NVIDIA MolMIM avec algorithme CMA-ES sur 1 000 molécules d'entraînement (3 variantes par molécule) |
| Évaluation | Calcul des métriques Validité / Unicité / Nouveauté, comparaison avec la référence VAE |

Partie 2 — projet_ML_p2.ipynb

| Étape | Description |
|-------|-------------|
| Filtrage avancé | Filtre PAINS (sous-structures indésirables) + SA Score < 4 (synthétisabilité) |
| Visualisation UMAP | Réduction dimensionnelle des fingerprints Morgan (2048 bits) colorée par score QED |
| Prédiction de toxicité ML | Modèles Random Forest, XGBoost, SVM entraînés sur features moléculaires (fingerprints + propriétés physico-chimiques) |
| Explicabilité XAI | Analyse SHAP pour identifier les fragments responsables de la toxicité |
| Counterfactual | Suggestions de modifications chimiques (ex. Nitro → Amine, Chlore → Fluor) pour réduire la toxicité |
| Interface Streamlit | Application interactive avec 5 onglets : Vue globale, Galerie moléculaire, Espace latent UMAP, Prédicteur de toxicité, Données |



⚙️ Installation & Exécution

Prérequis

bash
pip install rdkit pandas numpy matplotlib seaborn scikit-learn umap-learn shap streamlit xgboost


Lancement des notebooks

Exécuter dans l'ordre :
1. projet_ML_p1.ipynb → génère generated_molecules.csv
2. projet_ML_p2.ipynb → entraîne les modèles et lance l'application Streamlit

Lancement de l'interface Streamlit

bash
streamlit run app.py


> L'application expose 5 onglets permettant de filtrer les molécules, visualiser l'espace chimique, prédire la toxicité en temps réel et explorer les données complètes.



📊 Résultats clés

| Métrique | Notre modèle (MolMIM) | Référence VAE |
|----------|-----------------------|---------------|
| Validité | 100 % | 97,7 % |
| Unicité | 69 % | 67,5 % |
| Nouveauté | 100 % | 100 % |
| QED moyen | 0.823 | ~0.50 |
| SA Score moyen | 2.667 | — |



🛠️ Technologies utilisées

- RDKit — Cheminformatique (calcul de propriétés, fingerprints, filtres PAINS, SA Score)
- NVIDIA MolMIM (NIM API) — Génération de molécules par optimisation CMA-ES
- scikit-learn / XGBoost — Modèles de prédiction de toxicité
- SHAP — Explicabilité des prédictions ML
- UMAP — Visualisation de l'espace chimique
- Streamlit — Interface utilisateur interactive
- Pandas / NumPy / Matplotlib / Seaborn — Analyse et visualisation des données



📄 Livrables

- Rapport/PROJET ML.pdf — Rapport académique complet
- poster/Poster - De Novo Molecular Generation.pdf — Poster de présentation
- Data/generated_molecules.csv — Molécules générées (résultats du pipeline)
-le lien du data d origine : https://www.kaggle.com/datasets/basu369victor/zinc250k
_le lien du repositorie dans git : https://github.com/Wijdanebassiry/-De-Novo-Molecular-Generation.git
