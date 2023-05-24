---
description: How single asset deposit works
---

# Zap V3

In order to use a deposit in one asset, you need to select the appropriate tab in the field of adding liquidity.

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption><p>Switching to single asset mode</p></figcaption></figure>

Select "Single asset" and choose the token you want to add liquidity.

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption><p>Choosing the asset</p></figcaption></figure>

Approve the chosen asset

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Approving</p></figcaption></figure>

Enter amount, click "Add liquidity" and confirm the action.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Adding liquidity</p></figcaption></figure>

Congratulations! You successfully added a liquidity in one asset.

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
In BoosterPool's single asset algorithm, if there is a change in the asset proportions within the liquidity pool during the script operation, the user will receive the left asset. Let's take the USDC/WETH pair as an example: if the user adds USDC and there is a shift in the proportions, they will be returned WETH. This ensures that users are appropriately compensated in the event of changing asset ratios within the pool.
{% endhint %}
