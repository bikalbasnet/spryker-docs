---
title: Event
originalLink: https://documentation.spryker.com/v6/docs/event
originalArticleId: 8d6f3f1c-c533-4a7c-bfe0-1dc0a6c375a1
redirect_from:
  - /v6/docs/event
  - /v6/docs/en/event
---

The Event module implements an Observer pattern where you can add hooks (events) to your code and allow other modules to listen and react to those events.

There are two methods:

1. Traditional Synchronous where listeners are handled at the same time as they are dispatched
2. Asynchronous (Queueable) where events are put into a queue and handled later by some queue service.