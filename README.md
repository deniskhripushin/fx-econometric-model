# USD/RUB Econometric Model

An econometric study of the USD/RUB exchange rate using market and
macroeconomic factors. The project compares classical time-series and
regression approaches with Bayesian models.

## Objective

Model the USD/RUB exchange rate and examine its relationship with:

- Brent crude oil price;
- Russian 5-year CDS spread;
- Central Bank of Russia currency interventions.

## Data

| File | Contents |
|---|---|
| `currency.xlsx` | USD/RUB exchange-rate observations |
| `brent.xlsx` | Brent crude oil prices |
| `CDS_Daily.csv` | Russian 5-year CDS observations |
| `intervention.xlsx` | Currency intervention data |

The series are converted to a common date index and combined into one modeling
dataset. The analysis uses a chronological train/test split.

## Methods

The notebook includes:

- exploratory analysis of the exchange rate and explanatory variables;
- Ordinary Least Squares regression;
- Generalized Least Squares regression;
- ARIMA(1, 1, 0) with exogenous variables;
- Bayesian single-factor regressions with PyMC3;
- multivariate Bayesian Ridge regression;
- out-of-sample comparison using RMSE.

## Results

Recorded notebook results:

| Model | Test RMSE |
|---|---:|
| GLS | 8.691 |
| Bayesian Ridge | 8.794 |
| OLS | 8.812 |
| ARIMA | 71.355 |

The OLS model has an in-sample `R^2` of approximately `0.542`. Among the
reported out-of-sample results, GLS produces the lowest RMSE. The unusually
large ARIMA error indicates that its forecast construction or index alignment
should be reviewed before treating that result as a reliable model comparison.

## Repository Contents

```text
fx-econometric-model/
|-- multibayes_final-Copy4 (1).ipynb  # main analysis with outputs
|-- currency.xlsx
|-- brent.xlsx
|-- CDS_Daily.csv
|-- intervention.xlsx
|-- environment.yml
`-- README.md
```

## Running the Analysis

Create the Python 3.8 environment:

```bash
conda env create -f environment.yml -n fx-econometrics
conda activate fx-econometrics
```

Install the analysis dependencies:

```bash
python -m pip install pandas numpy scipy scikit-learn statsmodels matplotlib seaborn pymc3 arviz openpyxl xlrd
```

Start Jupyter Notebook from the repository root and open the analysis notebook:

```bash
jupyter notebook
```

## Technology Stack

- Python 3.8
- pandas and NumPy
- statsmodels
- scikit-learn
- PyMC3 and ArviZ
- Matplotlib and Seaborn

## Reproducibility Note

The analysis was developed with legacy versions of PyMC3 and related
scientific packages. Reproducing the original output may require pinning the
dependency versions recorded in the notebook.

