---
title: Implementing a Query Container
description: To create a new Query Container you can copy and paste the snippet from this article and replace Mymodule with your module name.
originalLink: https://documentation.spryker.com/v3/docs/implementing-a-query-container
originalArticleId: c5211497-f4d8-40e4-b217-eeefdf7b9907
redirect_from:
  - /v3/docs/implementing-a-query-container
  - /v3/docs/en/implementing-a-query-container
---


To create a new Query Container you can copy and paste the following snippet and replace `Mymodule` with your module name.

```php
<?php
namespace Pyz\Zed\MyBundle\Persistence;

use Spryker\Zed\Kernel\Persistence\AbstractQueryContainer;

/**
 * @method MyBundlePersistenceFactory getFactory()
 */
class MyBundleQueryContainer extends AbstractQueryContainer implements MyBundleQueryContainerInterface
{
}
```

## Conventions for Query Containers

There are some conventions which should be followed here:

* All methods have the prefix `query*()`.
* All public methods are exposed in the related interface (e.g. `MyBundleQueryContainerInterface`).
* Queries are returned unterminated, so that the user can add restrictions (limit, offset) and can choose how to terminate (`count()`, `find()`, `findAll()`).
* Query containers do not access higher layers. So no usage of a facade here.
* Query containers do not contain any logic which is not needed to build queries.
