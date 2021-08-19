---
title: Too many open files in Dev VM
description: Learn how to fix the issue with too many open files in Dev VM
originalLink: https://documentation.spryker.com/v6/docs/too-many-open-files-in-dev-vm
originalArticleId: a4ca59d7-6f20-4421-9f9f-4eedafa9c534
redirect_from:
  - /v6/docs/too-many-open-files-in-dev-vm
  - /v6/docs/en/too-many-open-files-in-dev-vm
---

## Description
When running `./vendor/bin/install`, the *Too many open files* error occurs.

## Cause
Maximum number of open files is too high.

## Solution
Adjust the maximum number of open files as follows:
```bash
ulimit -n 65535
```