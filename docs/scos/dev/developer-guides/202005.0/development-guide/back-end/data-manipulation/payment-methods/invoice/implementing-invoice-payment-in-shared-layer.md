---
title: Implementing Invoice Payment in Shared Layer
description: This procedure will help us to identify the new payment type through some unique constants.
originalLink: https://documentation.spryker.com/v5/docs/ht-invoice-payment-fe-be-shared
originalArticleId: 09d23d87-29b9-43d9-a1f7-8f33df487001
redirect_from:
  - /v5/docs/ht-invoice-payment-fe-be-shared
  - /v5/docs/en/ht-invoice-payment-fe-be-shared
---

This procedure will help us to identify the new payment type through some unique constants. We are going to define those constants under the `Shared` namespace, since they’re needed both by Yves and Zed.

1. Create the `PaymentMethodsConstants` interface under the `Shared` namespace, where you’ll define these unique constants.

<details open>
<summary>Code sample:</summary>
    
```php
<?php

namespace Pyz\Shared\PaymentMethods;

interface PaymentMethodsConstants
{

    /**
     * @const string
     */
    const PROVIDER = 'paymentmethods';

    /**
     * @const string
     */
    const PAYMENT_METHOD_INVOICE = 'invoice';

    /**
     * @const string
     */
    const PAYMENT_INVOICE_FORM_PROPERTY_PATH = static::PROVIDER . static::PAYMENT_METHOD_INVOICE;

}
```

</br>
</details>

2. Enrich the `Payment` transfer file with a new property that corresponds to the new payment method. Add `Shared/PaymentMethods/Transfer/invoicepayment.transfer.xml` file with the following content:

<details open>
<summary>Code sample:</summary>

```xml
<?xml version="1.0"?>
<transfers xmlns="spryker:transfer-01"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="spryker:transfer-01 http://static.spryker.com/transfer-01.xsd">

    <transfer name="Payment">
        <!-- Should be equal to PaymentMethodsConstants::PAYMENT_INVOICE_FORM_PROPERTY_PATH.
		Then the form fields can be automatically mapped to the transfer object inside this field. -->
        <property name="paymentmethodsinvoice" type="string"/>
    </transfer>
    </transfers>
```
    
</br>
</details>

3. Run the `vendor/bin/console transfer:generate` command to have the `PaymentTransfer` class updated.