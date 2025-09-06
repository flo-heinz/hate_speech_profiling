# Stance Detection Approaches for Between-Document Analysis

This repository provides tools and data for analyzing **stance** in scientific abstracts on environmental sustainability.  
It includes both a **supervised regression baseline** with SciBERT and **prompt-based inference** with Mistral-7B (via [Ollama](https://ollama.ai)), covering zero-shot, few-shot, and Chain-of-Stance prompting strategies.

---

## Repository Structure

### Key Components

#### `codes/`
- **Description**: Python scripts for training models, prompting Mistral, and evaluating outputs.  
- **Contents**:
  - `model_train.py` — Fine-tunes SciBERT for stance regression.  
  - `zero_shot_approach.py` — Zero-shot prompting with Mistral-7B.  
  - `few_shot_approach_10_stances.py` — Few-shot prompting with 10 examples.  
  - `few_shot_approach_30_stances.py` — Few-shot prompting with 30 examples.  
  - `few_shot_approach_50_stances.py` — Few-shot prompting with 50 examples.  
  - `chain_of_stance_approach.py` — Chain-of-Stance reasoning with structured steps.  
  - `make_predictions.py` — Batch helper for generating predictions.  
  - `evaluation.py` — Computes metrics (F1, MAE, MSE, correlations) and generates plots.  

#### `data/`
- **Description**: Contains annotated data, JSON abstracts, and experimental results.  

##### `training_part.json` / `evaluation_part.json`
- **Purpose**: Training and evaluation splits of annotated abstracts.  
- **Details**:
  - Each entry includes:
    ```json
    {
      "title": "Paper title",
      "abstract": "Abstract text...",
      "stance": 0.5
    }
    ```

##### `data/json/`
- **Description**: Individual annotated abstracts in JSON format.  
- **Use**: Basis for training, evaluation, and few-shot demonstrations.  

##### `data/outputs/`
- **Description**: Stores model predictions and evaluation summaries.  
- **Files**:
  - `NLP-Predictions_mistral_zero_shot.json`  
  - `NLP-Predictions_mistral_few_shot_10.json`  
  - `NLP-Predictions_mistral_few_shot_30.json`  
  - `NLP-Predictions_mistral_few_shot_50.json`  
  - `NLP-Predictions_mistral_chain_of_stance.json`  
  - `NLP-Predictions_SciBERT-regression.json`  
  - `evaluation_results.txt` — Evaluation summary.  
  - `all_json_in_one.json` — Combined predictions.  

##### `data/outputs/figures/`
- **Description**: Visualizations of model performance.  
- **Plots**:
  - `accuracy_comparison.png`  
  - `f1_macro_comparison.png`  
  - `f1_micro_comparison.png`  
  - `f1_weighted_comparison.png`  
  - `per_class_f1_grouped.png`  
  - `regression_metrics_all_in_one.png`  

---

## How to Use

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
2. **Set Up Environment**:
   ```bash
   python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
3. **Pull Mistral with Ollama**:
   ```bash
   ollama pull mistral
   ollama serve

4. **Run Experiments**

- Train SciBERT:
  ```
  python codes/model_train.py \
    --train data/training_part.json \
    --test data/evaluation_part.json \
    --out data/outputs/NLP-Predictions_SciBERT-regression.json
  ```

- Zero-Shot Prompting:
  ```
  python codes/zero_shot_approach.py \
    --input data/evaluation_part.json \
    --output data/outputs/NLP-Predictions_mistral_zero_shot.json
  ```

- Few-Shot Prompting (30 examples):
  ```
  python codes/few_shot_approach_30_stances.py \
    --input data/evaluation_part.json \
    --output data/outputs/NLP-Predictions_mistral_few_shot_30.json
  ```

- Chain-of-Stance Prompting:
  ```
  python codes/chain_of_stance_approach.py \
    --input data/evaluation_part.json \
    --output data/outputs/NLP-Predictions_mistral_chain_of_stance.json
  ```

- Evaluation:
  ```
  python codes/evaluation.py \
    --predictions_dir data/outputs \
    --gold data/evaluation_part.json \
    --out_dir data/outputs
  ```

---

## Sample Output

All predictions follow a standardized JSON schema:
{
  "title": "Example Paper Title",
  "abstract": "This study explores a renewable energy process...",
  "gold_stance": 1.0,
  "predicted_stance_score": 0.8,
  "predicted_stance_category": "Pro"
}

---

## Figures Preview

Plots available in `data/outputs/figures/`:

![Accuracy Comparison](data/outputs/figures/accuracy_comparison.png)  
![Weighted F1 Comparison](data/outputs/figures/f1_weighted_comparison.png)  
![Per-Class F1](data/outputs/figures/per_class_f1_grouped.png)  
![Regression Metrics](data/outputs/figures/regression_metrics_all_in_one.png)  

---











