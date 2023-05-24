---
description: AKA single asset deposit
---

# Zap V3

Single-asset deposit revolutionizes the process of providing liquidity to pools by allowing users to deposit just one asset. With this enhancement, getting started with BoosterPool becomes faster and simpler than ever before, setting it apart from other platforms in the market.

You can effortlessly add liquidity with a single asset, and the algorithm takes care of the rest. It automatically executes the necessary swaps to obtain the second asset, adds liquidity, and completes everything within a single transaction, all without any price slippage between actions. This streamlined process occurs seamlessly in one block, eliminating unnecessary complexities.

With this new feature, liquidity management becomes more accessible to a broader range of users. There's no need to worry about the details — let BoosterPool handle the work for you.

### How Zap v3 works

Here the scheme how BoosterPool smart contract works: Vault USDC/ETH [Neutral](market-strategies.md#neutral-strategy) ( Rate: 1 ETH = 1,800 USDC)

<figure><img src="../.gitbook/assets/zap v3 (2).png" alt=""><figcaption></figcaption></figure>

#### Mechanics:

Liquidity Provider (LP) deposeted 2 WETH to vault WETH/USDC, zap contract swaps required amount of WETH to recieve USDC. Then LP recieves BP liquidity tokens, contract adds liquidity to pool. This alghorithm exicuted in one block to exclude slippidge and reduse fees.

{% hint style="info" %}
In BoosterPool's zap v3 algorithm, if the proportions of assets in the liquidity pool changes while the script is running, the Liquidity Provider (LP) will get the remaining asset after the liquidity added.

For example (in vault USDC/WETH), if LP adds a large amount of USDC and the proportions shift during the swap, there will be surplus of WETH. So LP will receive this surplus of WETH. This makes sure that users are fairly compensated when the asset ratios in the pool change.
{% endhint %}

{% hint style="info" %}
To protect against front-running risks during the swap, a slippage parameter of 3% is set. This means that if the amount of liquidity provided by the Liquidity Provider (LP) significantly impacts the price, only a portion of the liquidity will be swapped and added to the Liquidity pool. The excess liquidity will be returned to the LP.
{% endhint %}
