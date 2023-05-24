---
description: Active Liquidity Management Strategies
---

# 4⃣ Strategies types

Each active liquidity management strategy consist of two main parts:

* Rules that describe how the position should be positioned in relation to market price at the moment when the position is opened.
* Rule, which describes when the position should be closed.

As the second rule Boosterpool always uses the following criteria: position should be closed when the price crosses its ranges.&#x20;

For the first rule the situation is more complicated. For fixed position width strategy, optimal active liquidity management strategy can be created if the user takes into account additional information about price movement. Rough assumption of future price movement can be done by dividing it into 3 types, corresponding to different types of strategy:

* Price will go up (“bull strategy”)
* Price will go down (“bear strategy”)
* Price will stay at the same level (“neutral strategy”)

If we have that additional information from the user it can be incorporated into strategy by changing the relative position of liquidity from market price. Namely, if we assume that price will go in some direction, then the main part of liquidity should be positioned at that part of the price. In Boosterpool we use the ¾ rule: if the price will go in some direction, then 75% of the liquidity should be positioned in the same direction. This can be achieved by selecting the position ranges in that way, that current price divides it in 75% to 25% ratio (or vice-versa). If we assume that the price will stay at the same level then the 50%-to-50% ratio will be selected. Each strategy provides more profit, if the price will go in the corresponding direction, but the user will suffer losses if his prediction of price movement is wrong.

Another important question is selection of position width. If we assume that we have market levels, which describe ranges of price movement, then we use the width of levels pair, that are nearest to current price value, as reference levels. Distance between such pairs of levels will be the width of the position. Visualization of different strategies is presented on figure 3.

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption><p>fig 3</p></figcaption></figure>

Fig. 3. Bull, bear and neutral strategies visualization. Blue horizontal lines denote market levels. Dark green line denotes historical price. Brown line denotes width between reference market levels, used as width of all 3 positions, that corresponds to different strategies. Pink, red and light green positions represent first positions for neutral (pink), bull (red) and bear (green) strategies. Positions are shifted by block number (horizontally) just for sake of readability. Light blue line shows the value of the current price.
