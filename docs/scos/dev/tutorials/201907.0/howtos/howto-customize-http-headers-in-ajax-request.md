---
title: HowTo - Customize HTTP Headers in AJAX Request
originalLink: https://documentation.spryker.com/v3/docs/ht-customize-http-headers-in-ajax-request
originalArticleId: 263b5f9b-664b-4d3b-b2bd-722467ed8726
redirect_from:
  - /v3/docs/ht-customize-http-headers-in-ajax-request
  - /v3/docs/en/ht-customize-http-headers-in-ajax-request
---

The `XMLHttpRequest` method `setRequestHeader()` sets the value of an HTTP request header. When using `setRequestHeader()`, you must call it after calling `open()`, but before calling `send()`. If this method is called several times with the same header, the values are merged into a single request header.

To update `ajax-provider.ts` for adding custom headers, add `this.headers.forEach((value: string, key: string) => this.xhr.setRequestHeader(key, value));` into Promise of the`fetch` method.

{% info_block infoBox "Usage example:" %}
this.ajaxProvider.headers.set('Accept', 'application/json'
{% endinfo_block %};.)