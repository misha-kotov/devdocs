---
layout: tutorial
group: get-started
title: Step 1. Configure the store
subtitle: Order Processing with REST APIs Tutorial
return_to:
  title: REST APIs
  url: get-started/rest_front.html
menu_order: 1
level3_subgroup: order-tutorial
version: 2.1
github_link: get-started/order-tutorial/order-config-store.md
functional_areas:
  - Integration
  - Orders
---

The default Luma store needs additional configuration to run the REST calls mentioned in this tutorial.

### Set the payment method {#set-payment}

Since the Luma store is for demonstration purposes only, it is not set up to handle credit card payments. However, it can simulate any of the following offline payment methods:

Payment type | Configuration name | Enabled by default?
--- | --- | ---
Check/Money Order | `checkmo` | Yes
Bank Transfer Payment | `banktransfer` | No
Cash on Delivery | `cashondelivery` | No
Purchase Order | `purchaseorder` | No
Zero Subtotal Checkout | `free` | Yes

In this tutorial, configure Magento to accept bank transfer payments. To allow bank transfer payments (or any other offline payment method) as a payment method, log in to {% glossarytooltip 29ddb393-ca22-4df9-a8d4-0024d75739b1 %}Admin{% endglossarytooltip %} and select **Stores** > **Configuration** > **Sales** > **Payment Methods**. Then enable the {% glossarytooltip 422b0fa8-b181-4c7c-93a2-c553abb34efd %}payment method{% endglossarytooltip %} and click **Save**.

Upon clicking **Save**, a notification message states that the {% glossarytooltip 0bc9c8bc-de1a-4a06-9c99-a89a29c30645 %}cache{% endglossarytooltip %} needs to be refreshed. Click the **System** > **Tools** > **Cache Management** link to refresh the cache.

### Deactivate a cart price rule {#price-rule}

By default, the Luma store includes a promotion where shipping is free if you spend at least $50. Since this tutorial shows shipping calculations, we need to deactivate this promotion. The promotion is defined in a cart price rule, which is also known as a sales rule. When you deactivate the cart price rule, shipping is charged at a flat rate of $5 per item.

To disable this cart price rule, select **Marketing** > **Promotions** > **Cart Price Rules**. Then edit rule ID 2 (Spend $50 or more - shipping is free!), and toggle the **Active** switch to **No**. Be sure to save the change.

### Configure supported shipping methods (optional) {#ship-method}

If an order contains one or more simple, configurable, bundle, or group products, then you must specify how the order will be shipped. Downloadable items cannot be shipped, and Magento does not calculate shipping charges for downloadable items.

Since we are not actually shipping any products in this tutorial, we do not need to set up an account with a shipping company such as UPS or Federal Express. Instead, we can use the offline shipping methods that are configured by default.

Shipping type | Configuration name | Enabled by default?
--- | --- | ---
Flat rate | `flatrate` | Yes
Table rate | `tablerate` | Yes
Free shipping | `freeshipping` | No

If you want to change which offline shipping methods are available, select **Stores** > **Configuration** > **Sales** > **Shipping Methods** in Admin. Enable or disable the shipping methods as desired, then click **Save**.

Upon clicking **Save**, a notification message states that the cache needs to be refreshed. Click the **Cache Management** link to refresh the cache.
