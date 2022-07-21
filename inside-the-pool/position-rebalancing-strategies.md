# Position rebalancing strategies

Important part of strategy is criteria, used for trigger position rebalancing\[2, 3]. There are several attempts to create an optimal strategy \[4,5,7]. After rebalancing, the following sequence of action occur:

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

This is the most complex strategy, but according to \[1] it can increase the profits. Soft ranges is a tuple of price thresholds, used for triggering position rebalancing (see Figure 1). Another name, used in scientific literature, is move strategy ranges \[1]. Both position places and soft ranges are set relatively to position start price, but while position place is set in tick spaces, soft ranges are set in prices. The algorithm for calculating absolute value soft ranges is:
