# 🧬 De Novo Molecular Generation

**AI-Driven Drug Candidate Discovery with Explainable Toxicity Prediction**
Article accepté et présenté à **IANLP 2026**.

**Auteures :** Hiba Mhada & Wijdane Bassiry
**Encadrement :** Oumaima Guendoul & Pr. El Habib Ben Lahmar
**Formation :** Master Data Science & Big Data, FSBM, Université Hassan II de Casablanca (2025-2026)

🔗 [Application en ligne](https://lnkd.in/ejSWAU8t) · 💻 [Dépôt de Wijdane](https://lnkd.in/enqpv4mr) · 📄 [Rapport](Rapport/rapportML.pdf) · 🖼️ [Poster](poster/POSTERFINAL.pdf)

## Pipeline
- Génération de molécules drug-like avec **NVIDIA MolMIM** + optimisation **CMA-ES**
- Filtrage : règle de Lipinski, PAINS, SA Score
- Prédiction de toxicité : Random Forest et XGBoost (**98,8 % d'exactitude, AUC-ROC 0,991**)
- Explicabilité : **SHAP** et modifications contrefactuelles pour réduire la toxicité
- Application interactive **Streamlit**

## Résultats
Validité 100 %, nouveauté 100 %, QED moyen 0,823, soit environ +65 % par rapport aux VAE de référence.

## Structure
```
code/    projet_ML_p1.ipynb · projet_ML_p2.ipynb
Data/    ZINC 250k · generated_molecules.csv
Rapport/ rapportML.pdf
poster/  POSTERFINAL.pdf
```

## Utilisation
La génération demande une clé API NVIDIA (build.nvidia.com), à définir dans la variable `NVIDIA_API_KEY`.
Données sources : [ZINC 250k (Kaggle)](https://www.kaggle.com/datasets/basu369victor/zinc250k)
