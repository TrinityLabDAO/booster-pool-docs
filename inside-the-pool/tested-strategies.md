# 4⃣ Tested strategies

Using our software a numerous set of strategies assessment was made. We perform in-deep investigation of the following pools:

* USDC/wETH
* wBTC/USDC
* wBTC/wETH

### **Result of strategies assessment**

Main results of strategy assessment can be summarized as follows:

* Frequent position rebalancing leads to severe impermanent loss[\[8\]](information-sources.md), so most profits generated when a strategy minimizes the number of rebalancing.
* Good amount of profits can be generated even when the price is not inside the position for a significant part of the time.
* Very narrow positions generate high amounts of commissions while price is in the position, but leads to even more impermanent losses, so they do not maximize the profits.
* So frequently a very broad position without active rebalancing is the best strategy.
