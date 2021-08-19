---
title: Xdebug does not work
description: Learn how to fix the issue with a non-working Xdebug
originalLink: https://documentation.spryker.com/v6/docs/xdebug-does-not-work
originalArticleId: 34810efe-ac24-44fa-a71c-ceaceb7e892d
redirect_from:
  - /v6/docs/xdebug-does-not-work
  - /v6/docs/en/xdebug-does-not-work
---

## Description
Xdebug does not work.

## Solution
1. Ensure that Xdebug is enabled in `deploy.*.yml`:
```
```yaml
docker:
...
    debug:
      xdebug:
        enabled: true
```
2. Ensure that IDE is listening to the port 9000.
3. Check if the host is accessible from the container:
```bash
docker/sdk cli -x bash -c 'nc -zv ${SPRYKER_XDEBUG_HOST_IP} 9000'
```