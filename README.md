# Onto-GAN: A Semantic-Aware Generative Framework for Bias Mitigation  
*Version: 1.0 — Generated on 2025 - S25 semester*  

This artifact package contains all reproducible components associated with the Onto-GAN synthetic data generation pipeline, as documented in the accompanying thesis:

Enhancing Accuracy and Interpretability of Machine Learning Models through Integrating Semantic Web Technologies: Addressing Bias and Developing Tools for Ontology Interpretation (A prototype)
Diala Bitar - Diala_227466**  
Syrian Virtual University / Web scinece master degree, 2025

Onto-GAN integrates **ontology-aware generative modelling**, **SHACL-based validation**, and **post-generation fairness analysis** to produce semantically valid, bias-controlled synthetic data.

---



## 1. System Requirements

**Python:** 3.9–3.11  
**OS tested:** Windows 10  
**Hardware:**  
- GPU recommended (NVIDIA RTX 2060 or above)  
- CPU-only mode supported (slower training)  
- RAM: ≥ 8 GB  

**Dependencies:**  
```
torch >= 2.0
pandas
numpy
scikit-learn
rdflib
pyshacl
matplotlib, seaborn
tqdm
```

Install using:
```bash
pip install -r requirements.txt
```
This prototype was developed using Microsoft Visual Studio Code, within a dedicated Python virtual environment named DPv1.
All project dependencies were installed and tested exclusively inside this virtual environment.

Recommendation:
For full reproducibility and to avoid dependency conflicts, it is strongly recommended to recreate and use the same isolated virtual environment before running the pipeline.

As an example:
python -m venv DPv1
source DPv1/Scripts/activate   # Windows
pip install -r requirements.txt

---

## 2. Dataset Requirements



Expected structure:
- Columns with numerical, categorical, and date attributes.
- Categorical values must appear in the ontology or they will be flagged as SHACL violations.
- Missing values should be imputed before training.

---

## 3. Ontology & SHACL Files

The pipeline uses:

- **Ontology:** `ontology.owl`
- **SHACL Shapes:** `constraints.ttl`
- **Namespaces:** defined in `ontology_stats.json`

Ontology and shapes are version-tracked in:
```
VersionGraph.ttl
```

This file records:
- Version ID  
- Source files  
- Associated model checkpoints  
- Date/time of generation  

---

## 4. Reproducing the Pipeline

### **Step 1 — Data Preparation**
Run:
```
main.ipynb
```
Produces: everything on this prototype as a saved files on local storage

## 5. Provenance & Reproducibility

Each generated synthetic row stores:
```json
{
  "gen_id": "...",
  "seed_row": 217,
  "cond_raw": {...},
  "raw_vector": [...],
  "decoded": {...},
  "conforms": true,
  "violations": ["ex:MissingParentClass"],
  "repairs": {...}
}
```

This enables:
- full traceability  
- exact re-generation  
- debugging of semantic errors  

---

## 6. Metrics & Validation

The `reports/metrics_summary.json` includes:

### **Predictive Metrics**
- Accuracy  
- Precision/Recall/F1  
- AUROC (if applicable)  

### **Fairness Metrics**
- Statistical Parity Difference (SPD)  
- Equal Opportunity Difference (EOD)  
- Disparate Impact Ratio (DIR)  

### **Semantic Validity**
- SHACL conformance rate  
- OWL inconsistency counts  
- Ontology class coverage  

### **Distributional Similarity**
- KL divergence for categorical frequency  
- KS test for numerical variables  
- PCA and t-SNE overlap scores  

---

## 7. Limitations

- Ontology incompleteness may introduce false positives in validation.  
- SHACL shapes do not fully encode all OWL semantics.  
- GANs may generate plausible but rare combinations that were not present in training (requires checking).  
- Fairness improvements depend on the sensitive attribute availability.  

---

## 8. Citation


@mastersthesis{DialaBitar2025OntoGAN,
  title={Ontology-Aware Generative Adversarial Networks for Semantically Valid Synthetic Data},
  author={Diala Bitar},
  school={Syrian Virtual University},
  year={2025}
}
```

---

## 9. Contact

For access to intermediate checkpoints or data subsets:  
**Diala Bitar**  
Email:   dialabitar4@gmail.com
Institution: Syrian Virtual University
Year: 2025  

---

