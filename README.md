# dubai-wealth-radar
A behavioral detection engine that identifies high net worth individuals using time-decayed transactional vectors and gradient boosted decision trees.

***
### README.md

# Dubai Wealth Radar

## Overview
Traditional banking models identify wealthy clients using static data such as account balances. This approach is reactive. The Dubai Wealth Radar is a predictive system that identifies wealth formation by analyzing the momentum of financial transactions. 

The system separates stable wealth indicators from temporary liquidity. It allows financial institutions to identify high net worth individuals before they reach traditional balance-based thresholds.

## Architecture
The system operates across five functional layers:

1. **Data Simulation:** A generator modeled on the Dubai financial ecosystem. It creates synthetic histories for five distinct user states: normal, emerging wealth, active whale, anchored whale, and exit risk. 
2. **Event Generation:** This layer translates user states into financial events including property commitments, cryptocurrency transfers, and institutional payments.
3. **Vector Scoring:** Transactions are sorted into five independent buckets: crypto, property, anchor, lifestyle, and exit. 
4. **Time-Decay Radar:** The engine applies exponential decay to each bucket. The decay rate varies by category. Property assets decay slowly while lifestyle spending fades rapidly. This prevents temporary high spenders from being misclassified as long-term wealth.
5. **Classification Layer:** An XGBoost model analyzes the maximum, mean, and volatility of these vectors. It uses class-weighting to account for the rarity of high net worth individuals in a general population.



## Operating Modes
The model provides a tunable interface for banking operations. The threshold for detection can be adjusted based on the capacity of the relationship management team.

| Operating Mode | Strategy | Recall (Catch Rate) | Precision (Accuracy) |
| :--- | :--- | :--- | :--- |
| Aggressive | Maximum capture of all potential wealth | ~95% | ~28% |
| Balanced | Optimized efficiency for outreach teams | ~80% | ~29% |
| Conservative | High certainty alerts only | ~60% | ~31% |

Note: Precision is limited by the use of transaction-only metadata. Integration with internal bank data is required to increase accuracy.

## Predictive Features
The model prioritizes features based on their statistical significance in identifying wealth:
1. **Exit Signal:** The magnitude of outbound capital transfers.
2. **Property Consistency:** The average value of recurring real estate commitments.
3. **Anchor Signal:** The frequency of institutional payments such as school fees or government fees.
4. **Crypto Signal:** The peak value of liquidity off-ramps.



## Technical Requirements
The engine is written in Python and requires the following libraries:
* pandas
* numpy
* xgboost
* scikit-learn
* matplotlib

## Implementation Roadmap
This prototype serves as a behavioral heuristic engine. For production deployment, the following steps are necessary:
* **Graph Integration:** Mapping counterparties to identify the destination of funds.
* **AUM Anchoring:** Incorporating actual assets under management to stabilize the decay math.
* **Probability Tuning:** Calibrating the detection threshold against real-world customer acquisition costs.

***
