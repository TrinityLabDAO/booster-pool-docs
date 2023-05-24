# 3⃣ Position rebalancing strategies

An important part of strategy are the criteria used for trigger position rebalancing[\[2, 3\]](information-sources.md). There are several attempts to create an optimal strategy [\[4,5,7\]](information-sources.md). After rebalancing, the following chain of events occurs:

* The old position closes, and all the concentrated liquidity is extracted from it. Concentrated liquidity can be represented in one or both tokens, it depends if price was between position bounds, on closing. According to user settings, the commission obtained from a closed position can or cannot be added to the new position.
* According to current tokens' price, position width, position delta, and new position ticks are calculated.
* According to Uniswap V3 math, the new tokens ratio is calculated, and tokens are exchanged to achieve that ratio, if needed. Token exchanges are done on Uniswap V3, so the user will pay for it a pool commission ([see table 1](how-it-works.md#table-1.-tick-spaces-for-different-pool-commissions.)).
* A new position is opened, and an amount of concentrated liquidity, calculated using the previously calculated ratio, will be added to it.

Currently our software supports four types of position rebalancing strategies that will be described below in detail. In all cases, the price is converted to tick and then compared to position bound ticks.

### No rebalancing

This is the simplest case. When this mode is selected for position, the concentrated liquidity will stay in the same price range for all of the selected dataset, no matter where the price goes.

### **Basic rebalancing**

In that case, position rebalancing occurs each time the price goes outside of the position range.

### **Regular rebalancing**

Position rebalancing occurs each time the “position alive time” passes the given threshold. “Position alive time” is measured in block numbers.

### **Soft range rebalancing**

This is the most complex strategy, but, according to [\[1\]](information-sources.md), it can increase the profits. **Soft ranges** are tuples of price thresholds, used for triggering position rebalancing (see Figure 1). Another name, used in scientific literature, is _move strategy ranges_ [\[1\]](information-sources.md). Both position places and soft ranges are set relatively to position start price, but while position place is set in tick spaces, soft ranges are set in prices. The algorithm for calculating absolute value soft ranges is:

* A user sets two values: the upper and the lower relative soft range. Values can be set in direct or reverted prices. In the second case, the price is converted to direct before cessing.
* The upper soft range is added to the start price to calculate the absolute value of the upper soft range.
* The lower soft range is subtracted from the start price to calculate the absolute value of the upper soft range.

{% hint style="info" %}
Assume that the current reverse price is 100, and the user has set the relative soft ranges to 50 (upper) and 25 (lower) in reverse price. First of all, all values will be converted to direct prices: the current price will be 0.01, the upper relative soft range will be 0.02, and the lower relative soft range will be 0.04. As you can see, while in input (reverse) prices the upper relative soft range is bigger than the lower, in direct prices the lower one is bigger than upper. Then our software calculates the absolute value of soft ranges: the upper will be 0.01 + 0.02 = 0.03, and the lower will be 0.01 - 0.04 = -0.03, which practically means 0, because prices cannot be negative.
{% endhint %}

### **Resistance and support levels**

Another important part to consider are the so-called “resistance” and “support” levels. It is considered that the price behavior is not completely random. In the whole price distribution there are points where price direction changes more frequently. These points form a _resistance level_ (if they are above the price) or _support levels_ (if they are below the price). It is thus resonable to place position bounds on these levels. Our software supports arbitrary amounts of these levels. Also, the maximum allowed position shifting for the placement of a position bound on the closest level can be set. Level prices can be set in both direct and reverse prices. While our software performs position rebalancing and calculates new position location, it will place the position bound on the nearest level, if this level is closer than the maximum allowed shifting.
