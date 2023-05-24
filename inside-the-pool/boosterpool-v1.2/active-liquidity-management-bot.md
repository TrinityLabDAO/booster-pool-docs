# 1⃣ Active liquidity management bot

Active liquidity bot can rebalance position on Uniswap V3, Algebra Finance (and any other AMM, that uses concentrated liquidity approach and Uniswap tick math) according to different criterias. Bot uses two sources of information for taking the decision about rebalancing:

1. Statical information about the market, which is set in the config file for each pool.
2. Dynamical information about current market situation, passed to bot in input json file for each block.

By “rebalancing” we mean the process of:

1. Withdraw all liquidity from the current position and get all fees for it.
2. Closing the current position.
3. Calculate parameters (upper and lower tick) of the new position.
4. Open a new position and transfer all liquidity to it, including fees.

Statical information about market includes:

1. Criteria of position closing.
2. Parameters of new position opening.
3. Market support and resistance levels.
4. Technical parameters about tokens and pool (decimals and pool commission).

Dynamical information about market consist of:

1. Block number.
2. Start price - on position opening.
3. Current price.
4. Lower and upper tick of currently opened position, if any.
5. Id of pool at hand.

Roughly speaking bot has the following steps of computation:

1. Assess the current market situation.
2. If the current position should not be rebalanced, do nothing.
3. If the current position should be rebalanced, initiate rebalancing.

So each liquidity management strategy consists of the following two parts:

1. Position closing criteria (should we close the current position now or not?)
2. Rule, for calculating new position ranges (where we should place new position?).

Both parts of the strategy can be set independently from the set of currently supported variants.

## Supported position closing criterias

Currently, bot support the following position closing criterias:

1. “NEVER”. Current position will never be closed, under any circumstances it will stay at the same ranges (ticks). Useful, for example, for a pair of stablecoins.
2. “AUTO”. Rebalancing will be initiated if price is outside of the position.

## Supported rules of position placing



\
