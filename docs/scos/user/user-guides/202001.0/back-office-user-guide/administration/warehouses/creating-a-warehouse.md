---
title: Creating a Warehouse
description: Use the procedure to create warehouses and define warehouses per specific stores in the Back Office.
originalLink: https://documentation.spryker.com/v4/docs/creating-a-warehouse
originalArticleId: 6b3ee14f-6e6e-4b58-a7c2-c9ce6fc8322d
redirect_from:
  - /v4/docs/creating-a-warehouse
  - /v4/docs/en/creating-a-warehouse
---

The topic provides steps on how to create a warehouse in the Back Office.
***
To start working with the Warehouses, navigate to the **Administration > Warehouses** section.
***
To create a warehouse:

1. On the **Warehouses** page, click **Create Warehouse** in the top right corner.
The **Create warehouse** page with two tabs opens - **Configuration** and **Store relation**. See [Warehouses: Reference information](/docs/scos/user/user-guides/202001.0/back-office-user-guide/administration/warehouses/references/warehouses-reference-information.html) for more details.
2. In the **Configuration** tab, do the following:
    * **Name**: Enter the name of the warehouse you want to create. 
    * **Is this warehouse available?**: Select *Yes* if you want to make your warehouse available (active) or *No* if you want to make your warehouse unavailable (inactive).
3. (optional) Switch to the **Store relation** tab. By default, the warehouse you are creating will be available for all the stores you have.
To make your warehouse unavailable for a specific store(s), clear the checkbox for that(those) store(s).

{% info_block warningBox "Note" %}
Keep in mind that if you clear all checkboxes for stores assigned to a specific warehouse, this warehouse won't appear on the **Edit Stock** page.
{% endinfo_block %}

4. To keep the changes, click **Save**. This will redirect you to the **Warehouses** page where you can see the new warehouse in the table and the following message: '*Warehouse has been successfully saved*'.

***
**What's next?**

The warehouse has been created. You can start working with it when creating or editing a concrete product. For more details, see [Creating a Product Variant](/docs/scos/user/user-guides/202001.0/back-office-user-guide/products/products/concrete-products/creating-a-product-variant.html). 

Additionally, you can edit any warehouse if needed. For more details, see the [Editing Warehouse Details](/docs/scos/user/user-guides/202001.0/back-office-user-guide/administration/warehouses/managing-warehouses.html#editing-warehouse-details) section in *Managing Warehouses*.

To learn more about the attributes you view or edit while creating or managing the warehouses, see [Warehouses: Reference Information](/docs/scos/user/user-guides/202001.0/back-office-user-guide/administration/warehouses/references/warehouses-reference-information.html).

To learn how to manage stock per specific warehouse, see [Managing Product Availability](/docs/scos/user/user-guides/202001.0/back-office-user-guide/products/availability/managing-products-availability.html).