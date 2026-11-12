## 1. Project Overview

The goal of this project was to forecast hourly electricity generation for the next 48 hours and provide 95% prediction intervals.

I used historical electricity generation data, weather information and time-based features to build and evaluate different forecasting models.

## 2. How I Used LLM

I used ChatGPT throughout the project as an assistant for coding, model selection, experimentation and result analysis.

My work with the LLM was iterative. I described the task and shared the data, code and evaluation results. Based on this information, ChatGPT suggested possible approaches and helped me improve the models.

The main steps were:

**1. Exploring models**

ChatGPT suggested several models, including XGBoost, LightGBM and CatBoost. I tested these approaches and compared their performance. I decided to reject CatBoost because I was not satisfied with its results.

**2. Selecting the main model**

I chose XGBoost as my main model. The first submission achieved 7th place out of 31 participants on the public leaderboard.

**3. Testing different approaches**

After the first submission, I continued experimenting with:
- LightGBM as an alternative model.
- XGBoost + LightGBM ensemble.
- Shallower Trees.
- More Trees.
- More Regularization.

Not all suggestions improved the results. For example, LightGBM performed worse than the first XGBoost model, and the ensemble did not provide a significant improvement.

**4. Improving XGBoost**

ChatGPT suggested experimenting with regularization parameters. I tested the `More_Regularization` configuration by increasing `min_child_weight` and `reg_lambda` from 5 to 10.

This version improved RMSE by 2.6% and Winkler score by 12.4% in local validation, although MAPE became slightly worse.

**5. Analysing results**

After each experiment, I shared the evaluation metrics with ChatGPT. Together, we analysed RMSE, MAPE, Winkler score and coverage, discussed why some models performed better than others and decided which experiments were worth keeping.

I also used ChatGPT to understand prediction intervals, rolling validation and the differences between local validation results and public leaderboard results.

Importantly, I did not accept every LLM suggestion. I tested the proposed solutions and made the final decisions based on the actual results.

## 3. How to Run the Project

The project was developed in Python using Jupyter Notebook.

**Step 1. Install Python dependencies**

Run the following command in the terminal:

```bash
pip install pandas numpy scikit-learn xgboost lightgbm catboost matplotlib jupyter
```

**Step 2. Prepare the project files**

Place the notebook, training data and required weather forecast files in the project directory. Make sure the file paths in the notebook match their actual locations.

**Step 3. Start Jupyter Notebook**

```bash
jupyter notebook
```

Open the main project notebook in your browser.

**Step 4. Run the notebook**

Run the cells sequentially, starting with data loading and preprocessing, followed by feature engineering, model training, validation and prediction.

**Step 5. Generate the submission**

The final output should be saved as:

```text
BONDAR_project.csv
```

The file contains 48 hourly forecasts and four columns:

- `ds` – forecast timestamp.
- `forecast` – predicted electricity generation.
- `lower_95` – lower prediction interval.
- `upper_95` – upper prediction interval.

Overall, LLM assistance helped me explore different approaches, improve the code, understand evaluation metrics and analyse the results. However, model selection and final decisions were based on my own experiments and evaluation.
