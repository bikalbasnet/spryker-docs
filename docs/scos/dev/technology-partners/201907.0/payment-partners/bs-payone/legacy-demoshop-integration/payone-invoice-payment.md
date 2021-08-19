---
title: PayOne - Invoice Payment
description: Integrate invoice payment through Payone into the Spryker-based shop.
originalLink: https://documentation.spryker.com/v3/docs/payone-invoice
originalArticleId: eafd763c-2083-41bd-b616-b906e19d57cc
redirect_from:
  - /v3/docs/payone-invoice
  - /v3/docs/en/payone-invoice
---

## Front-end Integration

To adjust the frontend appearance, provide the following templates in your theme directory:
`src/<project_name>/Yves/Payone/Theme/<custom_theme_name>/invoice.twig`

## State Machine Integration

Payone module provides a demo state machine for the Invoice payment method which implements Authorization flow.

To enable the demo state machine, extend the configuration with following values:

```php
<?php
$config[SalesConstants::PAYMENT_METHOD_STATEMACHINE_MAPPING] = [
 ...
 PayoneConfig::PAYMENT_METHOD_INVOICE => 'PayoneInvoice',
];

$config[OmsConstants::ACTIVE_PROCESSES] = [
 ...
 'PayoneInvoice',
];
```
