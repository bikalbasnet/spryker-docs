---
title: Reference informaton- AvailabilityStorage module overview
originalLink: https://documentation.spryker.com/2021080/docs/reference-informaton-availabilitystorage-module-overview
originalArticleId: 08a8917b-a04c-4f9f-8a7c-582d89e76243
redirect_from:
  - /2021080/docs/reference-informaton-availabilitystorage-module-overview
  - /2021080/docs/en/reference-informaton-availabilitystorage-module-overview
  - /docs/reference-informaton-availabilitystorage-module-overview
  - /docs/en/reference-informaton-availabilitystorage-module-overview
---

The [AvailabilityStorage](https://github.com/spryker/availability-storage) module publishes all the availability information for abstract and concrete products. Items are grouped by abstract product, and the process is handled by [Publish and Synchronize](/docs/scos/dev/developer-guides/{{page.version}}/development-guide/back-end/data-manipulation/data-publishing/publish-and-synchronization.html).

Published data example:

```json
{
    "id_availability_abstract": 1,
    "fk_store": 1,
    "abstract_sku": "001",
    "quantity": 10,
    "SpyAvailabilities": [
        {
            "id_availability": 1,
            "fk_availability_abstract": 1,
            "fk_store": 1,
            "is_never_out_of_stock": false,
            "quantity": 10,
            "sku": "001_25904006"
        }
    ],
    "Store": {
        "id_store": 1,
        "name": "DE"
    },
    "id_product_abstract": 1,
    "_timestamp": 1554886713.989162
}
```

{% info_block infoBox %}

This information is used on the product details page when **Add to cart** is rendered.

{% endinfo_block %}

The events are triggered in these two cases:

* Availability amount was 0, and now it’s more than 0.
* Availability amount was more than 0, and now it’s 0.

By default, the product quantity does not affect the *available* or *unavailable* product state. Even though the events are triggered when the product quantity changes from 0 to N or from N to 0, it's not the quantity change that triggers events, but the change of product status. You can change the default behavior for the events to be triggered whenever the quantity is changed. See [HowTo - Change the default behavior of event triggering in the AvailabilityStorage module](/docs/scos/dev/tutorials-and-howtos/{{page.version}}/howtos/howto-change-the-default-behavior-of-event-triggering-in-the-availabilitystorage-module.html) for details on how to do that.