# ↔ ETH <-> wETH swap

Uniswap V3 pools use wrapped ETH. To get it, you need to swap ETH for WETH.

{% hint style="info" %}
Wrapped Ether (wETH) is a token pegged to Ether (ETH). wETH is used by several platforms and DApps that support ERC-20 tokens. While ETH is used to pay for network transaction fees, it doesn't have the same functionality as ERC-20 tokens.

You can easily convert ETH into wETH through a process known as _wrapping_. You can also convert WETH back into ETH at any time. Both wrapping and unwrapping follow a 1:1 ratio, meaning there are no extra costs apart from the transaction fees.
{% endhint %}

You can wrap your ETH using a booster pool wrapping smart contract, which will store your ETH and give you back exactly the same amount of wETH. Use **Wrap ETH** tab on the pool's page:

![ETH<->wETH](<../.gitbook/assets/image (23).png>)

Enter the amount of ETH you want to "wrap" into the input box and click **Wrap ETH**. After that, the MetaMask confirmation window will appear. Click **Confirm** to proceed.

{% hint style="info" %}
Note that you need to leave a small amount of ETH to pay the transaction fees.
{% endhint %}

![wrap confirmation](<../.gitbook/assets/image (13).png>)

If you want to get ETH in exchange for wETH, click on the arrows, and the direction of the exchange will change:

![change the direction of wrap](../.gitbook/assets/image.png)

Now you can unwrap your wETH and receive ETH:

![unwrap wETH](<../.gitbook/assets/image (2).png>)

Let's unwrap some wETH. You need to enter the desired amount of wETH and click **Unwrap wETH**. After that, the MetaMask confirmation window appears. Click **Confirm** to proceed:

![unwrap confirmation](<../.gitbook/assets/image (12).png>)

Congratulations, you have successfully performed the wrap - unwrap operation for ETH. 

![your balance](<../.gitbook/assets/image (18).png>)
