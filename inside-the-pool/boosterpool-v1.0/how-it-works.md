---
description: This section provides a detailed description of how BoosterPool works.
---

# 2⃣ How it works

### **How the strategy works**

Each strategy starts with selecting a pool (tokens part and commission) used for backtesting. In addition, each strategy has a set of start parameters:

* Select a number of start positions, its width (in tick spaces) and the amount of concentrated liquidity in tokens
* Select the criteria for position rebalancing. Such criteria can include:
  * Rebalance position, if the current relative token price is outside of the position's soft or hard ranges (see below).
  * Rebalance position, if a given number of blocks has passed from last rebalancing, etc.
* Select a data range (or other data criteria) used for strategy evaluation.

Each of these parameters can be set independently for each position.\
The strategy input must also include a small set of technical parameters, such as precision of floating-point calculation. Note that real Uniswap V3 uses integer calculations.

### **Direct and reverse prices**

A price of accounts can be calculated according to Uniswap math. Basically, a price is a ratio between the amounts of two tokens, X and Y. In a real pool, X can be, for example, USDT, and Y - ETH.

An important point: while end-user results and input parameters can be expressed as both Y/X (direct price) and X/Y (reverted price), the software itself calculates all the results using only the direct price. It is important for working with soft ranges (see below). We use price information only at the end of the block's number, because our research leads to the conclusion that it is sufficient[\[6\]](information-sources.md).

### **Basic position parameters**

There are three basic position parameters: upper and lower bounds and input liquidity. The latter is obvious, and it can be set using both tokens in an arbitrary proportion. The correct proportion of tokens will be calculated automatically according to Uniswap math.

Each position has an upper and lower bound that are set in ticks. But not every tick can be used to place a position bound. According to Uniswap V3 math, a subset of ticks that can be used for this depends on the amount of fees that Uniswap V3 gives for that pool, and it is determined by so-called tick space (see table 1).

#### **Table 1. Tick spaces for different pool commissions.** <a href="#table1" id="table1"></a>

| Pool commission | Tick space |
| --------------- | ---------- |
| 0.0005          | 10         |
| 0.003           | 60         |
| \*\*\*\* 0.01   | 200        |

If the tick number can be divided without excess to the tick space, then this tick can be used to place position top or bound. Such a tick is called _base tick_ in our software. For the case of strategy assessment, the location of each position is determined according to the relative tokens' price at the block where the position is started. So each location of each position can be set using two numbers:

* Position width in tick spaces.
* Position delta (shift from tick, corresponding to the start position price).

{% hint style="info" %}
Note that ticks can be negative, and that direction of price and ticks scales can be different. Moreover, the relation between prices and ticks is not linear. Calculation of tick, corresponding to given price is done according to Uniswap v3 whitepaper. So when each part of a position is placed (upon a strategy's start or after rebalancing), its position will be set according to the given given price, width and delta (see Figure 1).
{% endhint %}

![Figure 1. Basic position parameters. Red lines show position bounds in price that are constant while position exists. Yellow lines are examples of soft ranges that can be between pool bounds or vice-versa. Price axis (Y) has non-linear interrelation to ticks axis. Green line represents price values.](<../../.gitbook/assets/Image (30).png>)
