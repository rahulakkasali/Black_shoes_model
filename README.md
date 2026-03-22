# Black_shoes_model


# 📊 Black-Scholes Model (BSM) for Trading Decisions

## 🧠 Overview

The **Black-Scholes Model (BSM)** is a mathematical model used to calculate the **fair price of options**.
It helps traders identify whether an option is **overpriced or underpriced**, which is useful for making trading decisions.

---

## 📐 BSM Formula

Call Option Price:

C = S * N(d1) - K * e^(-rT) * N(d2)

Where:

d1 = [ln(S/K) + (r + σ²/2) * T] / (σ * sqrt(T))
d2 = d1 - σ * sqrt(T)

---

## 📥 Input Parameters

| Parameter | Description                     |
| --------- | ------------------------------- |
| S         | Current stock price             |
| K         | Strike price                    |
| T         | Time to expiry (in years)       |
| σ         | Volatility (Implied Volatility) |
| r         | Risk-free interest rate         |

---

## 📤 Outputs (Used in Trading)

| Output    | Meaning                       |
| --------- | ----------------------------- |
| BSM Price | Fair value of option          |
| Delta     | Sensitivity to price movement |
| Gamma     | Rate of change of delta       |
| Theta     | Time decay                    |
| Vega      | Sensitivity to volatility     |
| Rho       | Sensitivity to interest rate  |

---

## ⚡ How It Helps in Trading

### 1. Mispricing Detection

* If Market Price > BSM Price → Option is overpriced → SELL
* If Market Price < BSM Price → Option is underpriced → BUY

---

### 2. Volatility-Based Trading

* High IV → Options expensive → Prefer selling
* Low IV → Options cheap → Prefer buying

---

### 3. Risk Management (Using Greeks)

* Delta → Directional exposure
* Theta → Time decay advantage
* Vega → Volatility risk

---

## 🧑‍💻 Python Implementation

```python
import numpy as np
from scipy.stats import norm

def black_scholes_call(S, K, T, r, sigma):
    d1 = (np.log(S/K) + (r + 0.5*sigma**2)*T) / (sigma*np.sqrt(T))
    d2 = d1 - sigma*np.sqrt(T)

    call_price = S * norm.cdf(d1) - K * np.exp(-r*T) * norm.cdf(d2)
    return call_price
```

---

## ⚠️ Limitations

* Assumes constant volatility (not realistic)
* Ignores sudden market jumps
* Works best for European options
* Sensitive to volatility input

---

## 🚀 Practical Insight

> BSM does not predict market direction.
> It helps identify **pricing inefficiencies**, which traders exploit.

---

## 🔥 Use Case in This Project

This project uses BSM to:

* Calculate fair option prices
* Compare with market prices
* Detect mispricing opportunities
* Support algorithmic trading decisions

---
