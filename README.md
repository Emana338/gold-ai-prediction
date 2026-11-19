# Gold AI — Gold Price Direction Prediction

Machine learning project predicting whether the next **trading-session closing price** of gold futures (`GC=F`) will increase (`1`) or not (`0`). Includes a Gradio question-and-answer interface in Google Colab.

## Project overview

- **Data:** Yahoo Finance gold futures daily OHLCV data (`GC=F`, starting 2015).
- **Features:** historical returns, moving-average ratios, volatility, price range, and volume-derived indicators.
- **Models:** XGBoost baseline and tuned XGBoost with `TimeSeriesSplit` + `GridSearchCV`.
- **Evaluation:** chronological holdout, Accuracy, Balanced Accuracy, Precision, Recall, F1, confusion matrix; comparisons with Always UP and Same-as-today baselines.
- **Monitoring:** historical quarterly performance simulation, not live monitoring.
- **Chat:** Gradio interface using the trained model's saved predictions and evaluation metrics; keyword-based Q&A, not a generative LLM.

## Run in Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Upload `Gold_Price_Direction_Prediction.ipynb`.
3. Select **Runtime → Run all**. Internet is needed to download market data and packages.
4. The notebook saves CSV files, model and metadata under `/content/gold_project/`.
5. At the end, launch the Gradio interface. A public `gradio.live` link may be generated if `share=True` works.

> The project is designed for Colab; it has not been verified against live Yahoo Finance responses in this package-building environment.

## Results

Earlier user-reported results for the **original** model (not a verified run of this repository):

| Model | Accuracy | F1 (UP) |
|---|---:|---:|
| Same-as-today baseline | 0.482 | 0.530 |
| XGBoost | 0.525 | 0.589 |

The actual tuned model scores are printed when you run the notebook. Do not report these older scores as tuned-model performance.

## Repository structure

```text
gold-ai-prediction/
├── Gold_Price_Direction_Prediction.ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE
```

## Limitations and responsible use

- This predicts direction, **not the next price** or guaranteed profit.
- Gold futures prices are not Saudi retail gold prices per gram.
- A prediction for the next *trading session* is not necessarily for tomorrow's calendar date.
- Probabilities are not necessarily calibrated. Results may be worse than simple baselines.
- The Gradio chatbot uses a snapshot computed when the notebook runs; it does not auto-refresh prices.
- Educational demonstration only, not investment advice.

## Suggested presentation

Five slides: project overview; dataset/workflow; XGBoost model; evaluation and limitations; Gradio chatbot, MLOps simulation and future work.
