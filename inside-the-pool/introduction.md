# Introduction

Uniswap V3 is an automated market maker with several advantages \[10], the most important of which is concentrated liquidity: liquidity that is allocated within a custom price range. Using that feature, liquidity providers can provide liquidity with up to 4000x capital efficiency relative to Uniswap V2, earning higher returns on their capital\[10]. This approach makes Uniswap V3 much more profitable, but managing concentrated liquidity can be tricky. **Uniswap V3 evaluator** for boo$terpool strategies is a software tool, developed in Trinity Lab, that assists liquidity providers in selecting optimal liquidity management strategy, and achieving maximum capital efficiency.

### Problem statement

Each liquidity management strategy has a set of parameters, that should be chosen, such as:&#x20;

* Amount of input liquidity.&#x20;
* Number of positions.&#x20;
* Distribution of concentrated liquidity between positions.&#x20;
* Criteria of position rebalancing, etc.&#x20;

Selection of optimal values for all parameters is a challenging task. One of widely used approaches for solving it is a backtesting approach, i.e. evaluation of a given set of parameters on historical data. Such evaluation can be done, using Uniswap V3 evaluator that uses math, described in Uniswap whitepaper\[9] for evaluating strategy's profits.

### **Key Features**

1. Assessment of each strategy profits on for each position and overall profit for all positions, including rebalancing.
2. Support for arbitrary tokens, and concentrated liquidity amounts.
3. Calculation of earnings and fees and other strategies parameters according to uniswap math and price information, arrived directly from blockchain.&#x20;
4. Support for calculation for arbitrary data parts using built-in SQL engine.&#x20;
5. Allows to set independent parameters for each position, including rebalancing criteria.&#x20;
6. Taking into account resistance and support levels.
