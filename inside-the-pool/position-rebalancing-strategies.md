# 3⃣ Position rebalancing strategies

Important part of strategy is criteria, used for trigger position rebalancing[\[2, 3\]](information-sources.md). There are several attempts to create an optimal strategy [\[4,5,7\]](information-sources.md). After rebalancing, the following sequence of action occur:

* The old position closes, and all the concentrated liquidity is extracted from it. Concentrated liquidity can be represented in one or both tokens, it depends if price was between position bounds, on closing. A commission obtained from a closed position can be added to a new position or not, according to user settings.
* According to current tokens price, position width and position delta new position ticks are calculated.
* According to Uniswap V3 math, a new tokens ratio is calculated, and tokens are exchanged to achieve that ratio, if needed. Token exchanges are done on Uniswap V3, so the user will pay for it a pool commission ([see table 1](how-it-works.md#table-1.-tick-spaces-for-different-pool-commissions.)).
* New position is opened, and a calculated amount of concentrated liquidity in calculated ratio will be added to it.

Currently our software supports 4 types of position rebalancing strategies, that will be described below in detail. For all cases price is converted to tick and and compared to position bound ticks.

### No rebalancing

This is the simplest case. When this mode is selected for position, the concentrated liquidity will stay in the same price range for all the selected dataset, no matter where the price goes.

### **Basic rebalancing**

In that case, position rebalancing will occur, each time the price goes outside the position range.

### **Regular rebalancing**

Position rebalancing will occur, each time the “position alive time” passes the given threshold. “Position alive time” is measured in block numbers.

### **Soft range rebalancing**

This is the most complex strategy, but according to [\[1\]](information-sources.md) it can increase the profits. **Soft ranges** is a tuple of price thresholds, used for triggering position rebalancing (see Figure 1). Another name, used in scientific literature, is move strategy ranges [\[1\]](information-sources.md). Both position places and soft ranges are set relatively to position start price, but while position place is set in tick spaces, soft ranges are set in prices. The algorithm for calculating absolute value soft ranges is:

* User set two values: upper and lower relative soft range. Values can be set in direct or reverted price. In the second case price is converted to direct before proceeding.
* Upper soft range is added to the start price, to calculate the absolute value of the upper soft range.
* Lower soft range is subtracted from the start price, to calculate the absolute value of the upper soft range.

{% hint style="info" %}
For example, let’s say the current reverse price is 100, and user set relative soft ranges to 50 (upper) and 25 (lower) in reverse price. First of all all values will be converted to direct prices: current price will be 0.01, upper relative soft range - 0.02 and lower relative soft range - 0.04. As you can see, while in input (reverse) prices upper relative soft range is bigger than lower, in direct prices lower is bigger than upper. Then our software calculates the absolute value of soft ranges: upper will be 0.01 + 0.02 = 0.03, and lower will be 0.01 - 0.04 = -0.03, which practically means 0, because price can not be negative.
{% endhint %}

### **Resistance and support levels**

Another important part to consider is so-called “resistance” and “support” levels. Trades considered that price behavior is not completely random. In the whole price distribution exist points, where price direction changing occurs more frequently. These points form a resistance level (if they are above price) or support levels (if they are below price), so a good idea is to place position bounds on these levels. Our software supports arbitrary amounts of these levels. Also the maximum allowed position shifting for placement of position bound on the closest level can be set. Level prices can be set in both direct and reverse prices. While our software performs position rebalancing and calculates new position location it will place the position bound on the nearest level, if this level is closer than maximum allowed shifting.
