
# Call Delta-Hedging

Welcome to the Call Delta-Hedging project ! This initiative aims to backtest a **Dynamic Delta-Hedging Strategy** applied to a short call option position. The project encompasses data collection, backtesting, and performance evaluation.


# 📄 Product : Call Out of The Money (OTM)

📈 Underlying Asset: **Euro Stoxx 50 ETF (EXSA.DE)**<br>
🎯 Strike:  **K = 55 €**<br>
⏳ Maturity: **T = 0.9 years (2025/01/02 – 2025/12/30)**<br>


# Working Conditions 

📉 Volatility: **Realized Volatility - No Implied Volatility Calibration**<br>
💶 Risk-free Interest Rate: **r = 3%**<br>



<img width="841" height="470" alt="image" src="https://github.com/user-attachments/assets/817fcaff-1cd4-4eb1-852f-5fd571a8fee0" />


# 🎯 Goal

On the morning of **January 2, 2025**, while the **SX5E** is trading at **€49.3**, we sell **100,000 out-of-the-money call options**, with a **maturity of 0.9 years** and a **strike price of €55**, written on this underlying asset.

The objective of this strategy is to **dynamically delta-hedge the option position** until **December 30, 2025**, with the aim of generating a **positive P&L at maturity**.



# 🧠 Delta-Hedging Methodology

The strategy consists of **continuously adjusting our position on a daily basis** in response to movements in the underlying asset.

At the beginning of the backtest, we sell the call options and delta-hedge the position.


### At time $t = 0$
$$
\mathbf{PL}_0 = \mathbf{-C_0 + \Delta_0 S_0}
$$

Where
- $C_0$ : Call Option Price at time $t = 0$  
- $\Delta_0$ : Call Option Delta at time $t = 0$  
- $S_0$ : Underlying Asset Price at time $t = 0$  

Then, we dynamically adjust our hedge each day depending on whether the underlying asset moves up or down.


<br>

### At time $t = i+1$

$$
\mathrm{PL}_{i+1} = -C_{i+1} + (\Delta_{i+1} - \Delta_i) S_{i+1}
$$

Where
- $C_{i+1}$ : Call Option Price at time $t = i+1$  
- $\Delta_i$ : Call Option Delta at time $t = i$  
- $\Delta_{i+1}$ : Call Option Delta at time $t = i+1$  
- $S_{i+1}$ : Underlying Asset Price at time $t = i+1$  
<br>


### Important Assumptions:

- We do not consider **transaction fees**.
- We use **realized volatility** instead of implied volatility.
- We assume the **risk-free interest rate** is constant.

# 📊 Results and Performance Summary

<img width="833" height="470" alt="image" src="https://github.com/user-attachments/assets/6d555773-a478-4e54-88eb-d606d9f03370" />


<img width="990" height="490" alt="image" src="https://github.com/user-attachments/assets/9aaca735-c9b1-45f8-aa89-e3f11211fbec" />







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

