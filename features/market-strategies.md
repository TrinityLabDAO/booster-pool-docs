# Market strategies

In BoosterPool's active liquidity management strategies, there are two main components involved.&#x20;

The first part is about deciding where to put our money in relation to the market price when we start investing. We have different strategies based on our expectations for the price movement and can be categorized into four types:&#x20;

### **Bull strategy**

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption><p>Bull strategy</p></figcaption></figure>

The base is the assumption that the price of an asset will increase in the future. Most of liquidity is on the **higher side** of the price range. We follow the **¾ rule**, which means **75%** of liquidity is on the higher side and **25%** on the lower one.

### **Bear strategy**

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption><p>Bear strategy</p></figcaption></figure>

The assumption is that the price of an asset will decrease in the future. Most of liquidity is on the **lower side** of the price range. We follow the **¾ rule**, which means **75%** of liquidity is on the lower side and **25%** on the higher one.

### **Neutral strategy**

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption><p>Netural strategy</p></figcaption></figure>

The assumption is that the price will stay stable. The liquidity is on both sides of the price range. We aim to capture profits if the price stays stable as predicted.

### Stable strategy

This strategy is a modified version of neutral strategy. It is similar to the neutral strategy but specifically designed for stablecoin pairs. In this strategy the liquidity kept centered around the normal price for stablecoin pairs.

Overall, BoosterPool's active liquidity management strategies incorporate rules for positioning liquidity based on market price and employ a criterion of price range crossing for position closure. By considering additional information about price movement and employing the ¾ rule, users can align their liquidity with anticipated price directions, potentially maximizing profits. The selection of position width based on market levels further refines the strategies, providing a comprehensive approach to active liquidity management in BoosterPool.

Read more in:

{% content-ref url="../inside-the-pool/boosterpool-v1.2/strategies-types.md" %}
[strategies-types.md](../inside-the-pool/boosterpool-v1.2/strategies-types.md)
{% endcontent-ref %}
