# 3⃣ Supported rules of position placing

Currently, bot support the following position placing rules:

1. “RELATIVE\_IN\_TICK\_SPACES”. In that case user need to specify in liquidity bot configuration file upper and lower distance from position start price to position bound ticks (“upper” and “lower” width respectively). When position rebalancing is initiated, new positions will always have specified distance from current price to position bounds in ticks. Another name is “fixed position width” strategy.
2. “AUTO\_BY\_LEVELS”. That option can be selected only if the user specifies at least two or more resistance or support levels in the configuration file. Bot places the new position between nearest levels at rebalancing block, skipping user selected amount of levels above or below current price.

In both cases, since Uniswap does not allow placing position on arbitrary ticks, real position will be placed on the closest ticks, allowed by Uniswap math. It means the precision of position placement will depend on pool commission (see “tickSpacing” parameter of Uni v3 pools).

More details about position placing settings are described below.

### Fixed position width

Example of position rebalancing using fixed position width strategy is presented in Fig.1.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>fig 1</p></figcaption></figure>

Fig. 1. Description of position rebalancing. Blue lines denote lower position width in ticks. Upper position width is denoted by a brown line. Lower position width is denoted by the blue line. Pink lines denote position bounds. Green line is the current price. Length of gray lines in ticks is alway the same, no matter when rebalancing is initiated and the same is true for blue lines.

Uniswap ticks width is different and depends from price, corresponding to that tick. Because of that:

1. The width of the position will be fixed in ticks, but not in price.
2. The width of the position cannot be an arbitrary value of ticks.

### Market [levels](https://www.investopedia.com/trading/support-and-resistance-basics/) rebalancing

Example of position rebalancing using market levels strategy is presented in Fig.2. Let us consider the situation in detail. Let’s assume that we have the following user settings in config file: skip 0 upper levels, skip 1 lower levels. First position was closed, when price crossed its upper range. At the time of position close levels, nearests to price position are levels 1 and 2. But in our example, according to user settings, first level downwards should be skipped, so the actual bottom range of position will be calculated using level 3.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>fog 2</p></figcaption></figure>

Fig. 2. Usage of market levels. Blue lines denote market levels position. Pink lines denote position bounds (in price and time). Green line is the current price.&#x20;

Some notes:

1. Each level is defined by start and stop points. Each point has two coordinates - block number and corresponding price.
2. If the current block number is lower than the block number in start price point, or bigger than the block number in stop price point, then corresponding level is not taken into account and considered currently invalid. If at the current block bot does not have at least two valid levels, it will close the currently opened position.
3. Calculation of levels equations and comparison of levels and price values at current block are taking place in logarithmic scale with user-specified log base.
