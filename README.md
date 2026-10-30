# Marketing Engagement Prediction

Data Science Hackathon project (October 2025). Analyzes social media ad performance and predicts how many users will engage with an ad based on its platform, format, and target audience.

## Results

- **Model:** Random Forest Regressor with One-Hot Encoding
- **Test performance:** R² = 0.97, MAE = 5.89
- **Robustness check:** after removing the most dominant features (user gender "Other", age groups 45+), R² stayed at 0.96–0.97
- **Key insights:**
  - Users aged 18–34 and **Stories** ads drive the highest engagement
  - Facebook generates about 1.7× the engagement of Instagram (254K vs 146K events)
  - Matching the ad's target age/interests to the user barely changes purchase rate (about 0.50–0.52% either way)
  - Campaign budget has almost no correlation with engagement (r = 0.08)

## Dataset

Synthetic social media advertising data (no personal information), in `data/`:

| File | Rows | Description |
|---|---|---|
| `ad_events.csv` | 400,000 | Every user interaction with an ad (impression, click, like, share, purchase) |
| `users.csv` | 10,000 | User demographics and interests |
| `ads.csv` | 200 | Ad creatives with platform, format, and targeting |
| `campaigns.csv` | 50 | Campaign budget and duration |

See `data/README.txt` for the full schema.

## Project structure

```
├── data/                     # raw CSV files
├── notebooks/
│   ├── 01_data_table.ipynb   # merge tables, build the engagement table
│   ├── 02_eda.ipynb          # exploratory analysis and visual insights
│   └── 03_ml_model.ipynb     # model training, evaluation, feature importance
└── requirements.txt
```

## How to run

```bash
pip install -r requirements.txt
jupyter notebook
```

Open the notebooks in `notebooks/` and choose **Run All**. Each notebook loads the data itself and runs top to bottom on its own.

To execute all three at once from the terminal:

```bash
jupyter nbconvert --to notebook --execute --inplace notebooks/*.ipynb
```

**Google Colab:** run `!git clone <repo-url>` then `%cd <repo-name>`, install with `!pip install -r requirements.txt`, and open any notebook.

## Tools

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Statsmodels
