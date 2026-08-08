# Fashion Forward Forecasting — StyleSense Recommendation Pipeline

Predicts whether a customer recommends a product (`Recommended IND`) from a mix of
numerical, categorical, and free-text review data, using a single scikit-learn `Pipeline`.
## This Project is Done By Fahad Masood Reda to Pass Udacity Data Scientist Nanodegree
## Project Structure

```
.
├── StyleSense_Recommendation_Pipeline.ipynb   # main notebook (all project code)
├── data/
│   └── reviews.csv                            # <-- put the provided dataset here
├── models/
│   └── stylesense_recommendation_pipeline.pkl # saved trained pipeline (created after running the notebook)
├── requirements.txt
└── README.md
```

## Getting Started

### 1. Install dependencies

```bash
python -m pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

> **Environment note:** spaCy's underlying engine (`thinc`) ships compiled extensions built
> against NumPy 1.x. If you already have NumPy 2.x installed, spaCy can crash with cryptic
> errors deep inside `thinc` (e.g. failures inside `chain`/`with_array` during `nlp.pipe`).
> `requirements.txt` pins `numpy<2.0` to avoid this — if you still hit it, run:
> ```bash
> python -m pip uninstall -y numpy spacy thinc
> python -m pip install "numpy<2.0" "spacy>=3.7,<3.8"
> python -m spacy download en_core_web_sm
> ```
> then **restart the Jupyter kernel** before re-running the notebook.

If you're on an Apple Silicon (M1/M2/M3) Mac and spaCy install fails, use:

```bash
python -m pip install 'spacy[apple]'
python -m pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

### 2. Data

`data/reviews.csv` is already included in this package.

### 3. Run the notebook

```bash
jupyter notebook StyleSense_Recommendation_Pipeline.ipynb
```

Run all cells top to bottom. The notebook will:

1. Load and explore the data
2. Split into train/test sets
3. Build a single pipeline that preprocesses numerical, categorical, and text data,
   engineers additional features from the review text (via spaCy), and feeds
   everything into a `RandomForestClassifier`
4. Tune hyperparameters with `GridSearchCV` (cross-validated)
5. Refit on the full training set and evaluate once on the held-out test set
   (accuracy, precision, recall, F1, ROC-AUC, confusion matrix, feature importances)
6. Save the trained pipeline to `models/stylesense_recommendation_pipeline.pkl`

## Notes

- All preprocessing (imputation, scaling, one-hot encoding, text cleaning, TF-IDF,
  text feature engineering) lives **inside** the pipeline — nothing is done to the
  data outside of `fit`/`transform`, so the exact same pipeline can be handed a new,
  raw review DataFrame at inference time.
- The saved `.pkl` pipeline is ready to plug into a small dashboard/app if you want
  to go beyond the base requirements (see the "Suggestions to Make Your Project
  Stand Out" section of the rubric).
