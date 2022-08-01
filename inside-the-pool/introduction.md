# 1⃣ Introduction

Uniswap V3 is an automated market maker (AMM) with several advantages [\[10\]](information-sources.md), the most important of which is _concentrated liquidity_, that is, liquidity that is allocated within a custom price range. Using that feature, liquidity providers can provide liquidity with up to 4000x capital efficiency relative to Uniswap V2, earning higher returns on their capital[\[10\]](information-sources.md). This approach makes Uniswap V3 much more profitable, but managing concentrated liquidity can be tricky. **Uniswap V3 evaluator** for BoosterPool strategies is a software tool, developed by Trinity Lab, that assists liquidity providers in selecting optimal liquidity management strategy and achieving maximum capital efficiency.

### Problem statement

Each liquidity management strategy has a set of parameters that must be chosen, such as:&#x20;

* Amount of input liquidity.&#x20;
* Number of positions.&#x20;
* Distribution of concentrated liquidity between positions.&#x20;
* Criteria of position rebalancing, etc.&#x20;

Selection of optimal values for all parameters is a challenging task. One of widely used approaches to solving it is _backtesting_, i.e., evaluating a given set of parameters on historical data. Such evaluation can be done using Uniswap V3 evaluator that uses math, described in the Uniswap whitepaper[\[9\]](information-sources.md) for evaluating strategy's profits.

### **Key Features**

1. Assessment of each strategy's profits on for each position and the overall profit for all positions, including rebalancing.
2. Support for arbitrary tokens and concentrated liquidity amounts.
3. Calculation of earnings, fees and other strategies' parameters according to Uniswap math and price information, derived directly from the blockchain.&#x20;
4. Support for the calculation for arbitrary data parts using the built-in SQL engine.&#x20;
5. The possibility to set independent parameters for each position, including rebalancing criteria.&#x20;
6. Taking into account resistance and support levels.
