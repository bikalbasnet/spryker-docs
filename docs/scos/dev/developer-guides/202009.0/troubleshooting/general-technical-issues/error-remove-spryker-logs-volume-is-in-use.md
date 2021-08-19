---
title: ERROR- remove spryker_logs- volume is in use
description: The solution to the `ERROR- remove spryker_logs- volume is in use` error.
originalLink: https://documentation.spryker.com/v6/docs/error-remove-spryker-logs-volume-is-in-use
originalArticleId: 7f1919c3-67c7-4485-9bc1-8280b26e2723
redirect_from:
  - /v6/docs/error-remove-spryker-logs-volume-is-in-use
  - /v6/docs/en/error-remove-spryker-logs-volume-is-in-use
---

You get the error `ERROR: remove spryker_logs: volume is in use - [{container_hash}]`

## Solution

1. Run the command:
```
docker rm -f {container_hash}
```

2. Repeat the failed command.