# 4⃣ Tested strategies

Using our software, a vast number of strategies has been assessed. We perform in-deep investigation of the following pools:

* USDC/wETH
* wBTC/USDC
* wBTC/wETH

### **Result of the strategies' assessment**

The main results of the strategy assessment can be summarized as follows:

* Frequent position rebalancing leads to severe impermanent loss[\[8\]](information-sources.md), so most profits are generated when a strategy minimizes the number of rebalancing.
* A sizeable amount of profits can be generated even when the price is not inside the position for a significant part of the time.
* Very narrow positions generate high amounts of commissions while the price is in the position but lead to even more impermanent losses, so they do not maximize the profits.
* Very frequently, a very broad position without active rebalancing is the best strategy.
