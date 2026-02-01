
# Call Delta-Hedging

Welcome to the Call Delta-Hedging ! This initiative aims at backtesting a trading strategy called: **Incremental Mean Reversion**. The project encompasses data collection, backtesting and evaluation of results.


# 📄 Product: Call OTM

📈 Underlying Asset: **Euro Stoxx 50 ETF (EXSA.DE)**<br>
🎯 Strike:  **K = 55 €**<br>
⏳ Maturity: **T = 0.9 years (2025/01/02 – 2025/12/30)**<br>


# Working Conditions 

📉 Volatility: **Realized Volatility - no implied volatility calibration**<br>
💶 Risk-free Interest Rate: **r = 3%**<br>



<img width="841" height="470" alt="image" src="https://github.com/user-attachments/assets/817fcaff-1cd4-4eb1-852f-5fd571a8fee0" />


# 🎯 Goal

On the morning of **January 2, 2025**, while the **SX5E** is trading at **€49.3**, we sell **100,000 out-of-the-money call options**, with a **maturity of 0.9 years** and a **strike price of €55**, written on this underlying asset.

The objective of this strategy is to **dynamically delta-hedge the option position** until **December 30, 2025**, with the aim of generating a **positive P&L at maturity**.



# 🧠 What is the Incremental Mean Reversion strategy ?

The strategy consists of constantly adjusting our position depending on the recent sentiment of the markets.<br>

In order to do so, we rely on the Z-score. 

$$
Z = \frac{X - \mu}{\sigma}
$$

Where

$X$ is the current return   
$\mu$ is the 20-day rolling average of returns<br>
$\sigma$ is the 20-day rolling volatility

<br>

It measures how far our daily return is from the rolling average. 
Especially if the gap is greater than 1, it means that the market is following a trend of buying or selling the asset. 
If the market is selling, then our strategy consists of buying the asset with an appropriate share of our available cash. 
If the market is buying, then our srategy consists of selling an appropriate share of our assets. 


We will not consider transaction fees and we will compare our strategy's return to the return of simply buying and holding the position over the year. 

# 📊 Results and Performance Summary

<img width="857" height="470" alt="image" src="https://github.com/user-attachments/assets/bc4fd497-0a12-43e9-991d-99646dee0e93" />






| Metric | 02/01/2025 | 30/12/2025 |
|-------|-----------|-----------|
| 💰 **P&L** | €0.00 | €999,863.74 |
| 📦 **Number of Assets Held** | 21,393.62 | 39,821.51 |
| 📊 **Asset Price** | €49.29 | €58.60 |
| Δ  **Delta** | 0.21 | 1.00 |
| 📄 **Call Value** | €0.57 | €3.29 |




## ⚙️ Prerequisites

To successfully run this project, ensure you have the following installed:
- 🐍 **Python**
- 📓 **Jupyter Notebook**
- 📦 **Required libraries:**
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `yfinance`
  - `scipy.stats`


You can find all dependencies listed in `requirements.txt`. 

## 📌 Installation
 
1. Create and activate a Python virtual environment.
2. Install dependencies:
 
```bash
pip install -r requirements.txt 
```
## 💻 Usage
 
Open the notebooks in order to reproduce the pipeline:
 
```bash
jupyter notebook notebooks/Delta-hedging.ipynb
```

