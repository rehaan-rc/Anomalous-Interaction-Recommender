# Anomalous-Interaction-Recommender
An AI201 Machine Learning project investigating whether detecting anomalous user interactions and reducing their influence can improve product recommendation quality.

## Project Overview

Recommender systems use user–item interactions to identify products that users may be interested in. However, unusual or noisy user activity can influence recommendations and potentially reduce their quality.

This project investigates whether removing anomalous users or down-weighting their interactions improves recommendation performance compared with a baseline popularity-based recommender.

## Research Question

**Does removing or down-weighting anomalous user interactions improve product recommendation quality?**

## Dataset

We use the [RetailRocket Recommender System Dataset](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset), which contains real-world e-commerce interaction data.

The dataset includes:

- `events.csv` — timestamped user–item interactions.
- `item_properties_part1.csv` — item properties.
- `item_properties_part2.csv` — additional item properties.
- `category_tree.csv` — product category relationships.

The main event types are:

- **View:** A user views a product.
- **Add-to-cart:** A user adds a product to their cart.
- **Transaction:** A user purchases a product.

**Note:** The dataset files are not included in this repository. Download them from the source above and place them in the locations expected by the notebook.

## Methodology

The project follows these main steps:

1. **Data preprocessing:** Load and clean the interaction data.
2. **Feature engineering:** Construct user-level behavioral features, including interaction counts, unique items, activity patterns, event-type ratios, and time gaps between interactions.
3. **Feature transformation:** Apply logarithmic transformations to appropriate skewed features and standardize the features.
4. **Anomaly detection:** Use Isolation Forest to identify users with unusual interaction patterns.
5. **Recommendation strategies:** Compare a baseline popularity-based recommender with two anomaly-handling approaches:
   - **Removal:** Exclude detected anomalous users from the relevant training data.
   - **Down-weighting:** Reduce the influence of detected anomalous users.
6. **Model selection:** Evaluate candidate anomaly-detection settings using validation data.
7. **Evaluation:** Compare recommendation quality on held-out test data.

## Experimental Setup

- **Anomaly detection algorithm:** Isolation Forest.
- **Contamination candidates:** 1%, 3%, 5%, and 10%.
- **Random seed:** 42.
- **Recommendation baseline:** Popularity-based recommendation.
- **Candidate pool:** Up to 1,000 candidate items.
- **Evaluation metrics:** Precision@K, Recall@K, and NDCG@K, with K = 5 and K = 10.

The notebook contains the implementation and experimental results. Refer to it for the exact preprocessing, data-splitting, model-selection, and evaluation procedures.

## Repository Structure

```text
anomalous-interactions-recommender/
├── README.md
├── requirements.txt
├── .gitignore
├── anomaly_code.ipynb
└── data/
    └── .gitkeep
```

The notebook filename and directory structure above are examples. Update them to match the files actually committed to this repository.

## Requirements

- Python 3
- Jupyter Notebook/Google collab
- NumPy
- pandas
- Matplotlib
- scikit-learn

Install the dependencies by running:

```bash
pip install -r requirements.txt
```

For reproducible experiments, it is recommended to run the notebook in a clean virtual environment and record the tested package versions.

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/rehaan-rc/Anomalous-Interaction-Recommender.git
cd anomalous-interactions-recommender
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Download the dataset

Download the RetailRocket dataset from [Kaggle](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset).

The dataset files are **not included in this repository** and must be downloaded separately.

### Required Files

Download the dataset and place the following files inside the `data/` folder in the repository root:

- `events.csv`
- `item_properties_part1.csv`
- `item_properties_part2.csv`
- `category_tree.csv`

### Directory Structure

After downloading the dataset, your project should have the following structure:

```text
anomalous-interaction-recommender/
├── README.md
├── requirements.txt
├── .gitignore
├── anomaly_code.ipynb
└── data/
    ├── .gitkeep
    ├── events.csv
    ├── item_properties_part1.csv
    ├── item_properties_part2.csv
    └── category_tree.csv
```

**Note:** The `data/` folder is included in the repository using a `.gitkeep` placeholder. The CSV files are excluded from GitHub and must be downloaded separately.

### Run the Project

1. **Clone the repository:**

   ```bash
   git clone https://github.com/rehaan-rc/Anomalous-Interaction-Recommender.git
   cd Anomalous-Interaction-Recommender
   ```

2. **Install the required dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

3. **Download the dataset** from the [RetailRocket dataset page on Kaggle](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset).

4. **Place the CSV files** inside the `data/` folder in the repository root.

5. **Launch Jupyter Notebook:**

   ```bash
   jupyter notebook
   ```

6. **Run the notebook** from top to bottom.

### Important Notes

- Ensure all four CSV files are present in the `data/` folder before running the notebook.
- The notebook expects the dataset paths to be configured as `data/events.csv`, `data/item_properties_part1.csv`, `data/item_properties_part2.csv`, and `data/category_tree.csv`.
- Run the notebook from the repository root to ensure the relative paths work correctly.
- Install all required dependencies before executing the experiments.

### 4. Run the notebook

Start Jupyter:

```bash
jupyter notebook
```

Open the project notebook and execute the cells from top to bottom.

### 5. Inspect the results

Review the evaluation metrics, generated plots, and experimental comparisons produced by the notebook. Ensure that the output directory exists and that the data paths are configured correctly before running the experiments.

## Reproducibility

The project uses a fixed random seed (`42`) for supported randomized operations. Reproducing the results also requires:

- Using the same dataset and preprocessing procedure.
- Maintaining the same training, validation, and test splits.
- Keeping the anomaly-detection and recommendation settings consistent.
- Using compatible package versions.
- Executing the notebook in the intended order.

Exact reproducibility should be verified by running the notebook in a clean environment. Differences in package versions, execution settings, or data files may affect results.

## Team

- Rehaan Chanana
- Ashnoor Wadhera
- Anushka Dutta
- Paavani Sethia


*This repository contains the code and experimental workflow for studying the effect of anomalous user interactions on product recommendation quality.*
