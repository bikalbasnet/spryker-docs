---
title: Queue Pool
originalLink: https://documentation.spryker.com/v3/docs/queue-pool
originalArticleId: 9da55ca2-c87e-4ce7-a08e-45968c0ddd1d
redirect_from:
  - /v3/docs/queue-pool
  - /v3/docs/en/queue-pool
---

Queue pool is designed to allow P&S ([Publish and Synchronization](/docs/scos/dev/developer-guides/201907.0/development-guide/back-end/data-manipulation/data-publishing/publish-and-synchronization.html)) messages to be sent to several queues.

## Configuration
Queue pools are defined with unique names in `config/Shared/stores.php`

```php
<?php
...
    'currencyIsoCodes' => ['EUR', 'CHF'],
    'queuePools' => [
        'synchronizationPool' => [
            'AT-connection',
            'DE-connection',
        ],
        'fooPool' => [
            'DE-connection',
            'US-connection',
        ]
    ],
    'storesWithSharedPersistence' => ['AT'],
];
...
```
## Sending Messages
Messages must be prepared for sending to queue pools. You can do it by setting the `QueuePool` property for the `QueueSendMessageTransfer`.
```php
<?php
...
$queueSendTransfer = new QueueSendMessageTransfer();
    $queueSendTransfer->setQueuePoolName('fooPool');
 
    $queueClient->sendMessage('mail', $queueSendTransfer);
...
```
In this example, the message is configured to be sent to mail queue in DE and US store queues.

<!--Last review date: Apr 25, 2019 by by Ehsan Zanjani, Andrii Tserkovnyi-->