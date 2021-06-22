---
title: Installation
description: Retrieve information about Marketplace offers via API
template: glue-api-storefront-guide-template
---

Every registered customer can retrieve the list of orders for their account, as well as the detailed order information, including every step of the calculation and addresses used in the orders.

In your development, this resource can help you to:

- Make the order history available to customers.
- Make order details available to enable reordering functionality.

The **Order History API** allows you to retrieve all orders made by a registered customer.

**Authentication**

Since order history is available for registered users only, the endpoints provided by the API cannot be accessed anonymously. For this reason, you always need to pass a user's authentication token in your REST requests. For details on how to authenticate a user and retrieve the token, see [**Authentication and authorization**](https://documentation.spryker.com/docs/retrieving-customers-order-history).

## Installation

For detailed information on the modules that provide the API functionality and related installation instructions, see:

- [**Glue API: Order Management feature integration**](https://documentation.spryker.com/docs/glue-api-order-management-feature-integration)

## Retrieve all orders

To retrieve a list of all orders made by a registered customer, send the request:

---
`GET` **/orders**

---

### Request

| HEADER KEY  | HEADER VALUE | REQUIRED | DESCRIPTION                                                  |
| ------------- | ------------ | -------- | -------------------------------- |
| Authorization | string   | &check;  | Alphanumeric string that authorizes the customer to send requests to protected resources. Get it by [authenticating as a customer](https://documentation.spryker.com/authenticating-as-a-customer). |

| QUERY PARAMETER | DESCRIPTION  | POSSIBLE VALUES |
| ---------------- | ---------------------- | ----------------------------- |
| offset | The offset of the order at which to begin the response. Works only together with page[limit]. To work correctly, the value should be devisable by the value of page[limit]. The default value is 0. | From 0 to any. |
| limit | The maximum number of entries to return. Works only together with page[offset]. The default value is 10. | From 1 to any. |
| include | Adds resource relationships to the request.  | merchants<br>{% info_block warningBox "Note" %}This option is available only in case you have upgraded your shop to the Marketplace provided by Spryker.{% endinfo_block %}. |

| REQUEST | USAGE  |
| --------------------- | ------------------ |
| `GET https://glue.mysprykershop.com/orders`  | Retrieve all customer’s orders.  |
| `GET https://glue.mysprykershop.com/orders?page[limit]=10`  | Retrieve 10 orders. |
| `GET https://glue.mysprykershop.com/orders?page[offset]=10&page[limit]=10` | Retrieve orders 11 through 20.  |
| `GET https://glue.mysprykershop.com/orders?page[offset]=20`  | Retrieve all orders starting from the twenty-first order.  |
| `GET https://glue.mysprykershop.com/orders?include=merchants`  | Retrieve all customer’s orders with the information on merchants included.<br>{% info_block warningBox "Note" %}This option is available only in case you have upgraded your shop to the Marketplace provided by Spryker.{% endinfo_block %}. |

### Response

The endpoint responds with an array of orders placed by the authenticated customer. In response, each order will have a unique identifier. It is specified in the *id* attribute. You can use the ID to retrieve detailed order information. Also, *self* links will be provided to access the order individually using the REST API.

<details>
<summary markdown='span'>Response sample: all orders</summary>

```json
{
    "data": [
        {
            "type": "orders",
            "id": "DE--5",
            "attributes": {
                "merchantReferences": [],
                "itemStates": [
                    "closed"
                ],
                "createdAt": "2020-10-19 15:26:37.868585",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 500,
                    "discountTotal": 9701,
                    "taxTotal": 10962,
                    "subtotal": 92013,
                    "grandTotal": 82812,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--5"
            }
        },
        {
            "type": "orders",
            "id": "DE--4",
            "attributes": {
                "merchantReferences": [],
                "itemStates": [
                    "shipped"
                ],
                "createdAt": "2020-10-19 15:25:57.909985",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 500,
                    "discountTotal": 14841,
                    "taxTotal": 0,
                    "subtotal": 143412,
                    "grandTotal": 129071,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--4"
            }
        },
        {
            "type": "orders",
            "id": "DE--3",
            "attributes": {
                "merchantReferences": [],
                "itemStates": [
                    "closed"
                ],
                "createdAt": "2020-10-19 15:25:14.861031",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 1500,
                    "discountTotal": 9147,
                    "taxTotal": 2893,
                    "subtotal": 91474,
                    "grandTotal": 83827,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--3"
            }
        },
        {
            "type": "orders",
            "id": "DE--2",
            "attributes": {
                "merchantReferences": [
                    "MER000002",
                    "MER000001"
                ],
                "itemStates": [
                    "new"
                ],
                "createdAt": "2020-10-19 15:16:21.879286",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 1590,
                    "discountTotal": 3959,
                    "taxTotal": 4957,
                    "subtotal": 39586,
                    "grandTotal": 37217,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--2"
            }
        },
        {
            "type": "orders",
            "id": "DE--1",
            "attributes": {
                "merchantReferences": [
                    "MER000001",
                    "MER000002",
                    "MER000006",
                    "MER000005"
                ],
                "itemStates": [
                    "confirmed"
                ],
                "createdAt": "2020-10-19 15:14:51.183582",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 4080,
                    "discountTotal": 11884,
                    "taxTotal": 12651,
                    "subtotal": 113944,
                    "grandTotal": 106140,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--1"
            }
        }
    ],
    "links": {
        "self": "https://glue.mysprykershop.com/orders"
    }
}
```
</details>

<details>
<summary markdown='span'>Response sample with information on merchants</summary>

This option is available only in case you have upgraded your shop to the Marketplace provided by Spryker.

```json
{
    "data": [
        {
            "type": "orders",
            "id": "DE--5",
            "attributes": {
                "merchantReferences": [],
                "itemStates": [
                    "closed"
                ],
                "createdAt": "2020-10-19 15:26:37.868585",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 500,
                    "discountTotal": 9701,
                    "taxTotal": 10962,
                    "subtotal": 92013,
                    "grandTotal": 82812,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--5?include=merchants"
            }
        },
        {
            "type": "orders",
            "id": "DE--4",
            "attributes": {
                "merchantReferences": [],
                "itemStates": [
                    "shipped"
                ],
                "createdAt": "2020-10-19 15:25:57.909985",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 500,
                    "discountTotal": 14841,
                    "taxTotal": 0,
                    "subtotal": 143412,
                    "grandTotal": 129071,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--4?include=merchants"
            }
        },
        {
            "type": "orders",
            "id": "DE--3",
            "attributes": {
                "merchantReferences": [],
                "itemStates": [
                    "closed"
                ],
                "createdAt": "2020-10-19 15:25:14.861031",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 1500,
                    "discountTotal": 9147,
                    "taxTotal": 2893,
                    "subtotal": 91474,
                    "grandTotal": 83827,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--3?include=merchants"
            }
        },
        {
            "type": "orders",
            "id": "DE--2",
            "attributes": {
                "merchantReferences": [
                    "MER000002",
                    "MER000001"
                ],
                "itemStates": [
                    "new"
                ],
                "createdAt": "2020-10-19 15:16:21.879286",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 1590,
                    "discountTotal": 3959,
                    "taxTotal": 4957,
                    "subtotal": 39586,
                    "grandTotal": 37217,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--2?include=merchants"
            },
            "relationships": {
                "merchants": {
                    "data": [
                        {
                            "type": "merchants",
                            "id": "MER000002"
                        },
                        {
                            "type": "merchants",
                            "id": "MER000001"
                        }
                    ]
                }
            }
        },
        {
            "type": "orders",
            "id": "DE--1",
            "attributes": {
                "merchantReferences": [
                    "MER000001",
                    "MER000002",
                    "MER000006",
                    "MER000005"
                ],
                "itemStates": [
                    "confirmed"
                ],
                "createdAt": "2020-10-19 15:14:51.183582",
                "currencyIsoCode": "EUR",
                "priceMode": "GROSS_MODE",
                "totals": {
                    "expenseTotal": 4080,
                    "discountTotal": 11884,
                    "taxTotal": 12651,
                    "subtotal": 113944,
                    "grandTotal": 106140,
                    "canceledTotal": 0,
                    "remunerationTotal": 0
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/orders/DE--1?include=merchants"
            },
            "relationships": {
                "merchants": {
                    "data": [
                        {
                            "type": "merchants",
                            "id": "MER000002"
                        },
                        {
                            "type": "merchants",
                            "id": "MER000001"
                        },
                        {
                            "type": "merchants",
                            "id": "MER000006"
                        },
                        {
                            "type": "merchants",
                            "id": "MER000005"
                        }
                    ]
                }
            }
        }
    ],
    "links": {
        "self": "https://glue.mysprykershop.com/orders?include=merchants"
    },
    "included": [
        {
            "type": "merchants",
            "id": "MER000002",
            "attributes": {
                "merchantName": "Video King",
                "merchantUrl": "/en/merchant/video-king",
                "contactPersonRole": "Country Manager DE",
                "contactPersonTitle": "Ms",
                "contactPersonFirstName": "Martha",
                "contactPersonLastName": "Farmer",
                "contactPersonPhone": "+31 123 345 678",
                "logoUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/videoking-logo.png",
                "publicEmail": "hi@video-king.nl",
                "publicPhone": "+31 123 345 777",
                "description": "Video King is a premium provider of video equipment. In business since 2010, we understand the needs of video professionals and enthusiasts and offer a wide variety of products with competitive prices. ",
                "bannerUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/videoking-banner.png",
                "deliveryTime": "2-4 days",
                "latitude": "4.838470",
                "longitude": "51.558107",
                "faxNumber": "+31 123 345 733",
                "legalInformation": {
                    "terms": "<p><span style=\"font-weight: bold;\">General Terms</span><br><br>(1) This privacy policy has been compiled to better serve those who are concerned with how their 'Personally identifiable information' (PII) is being used online. PII, as used in US privacy law and information security, is information that can be used on its own or with other information to identify, contact, or locate a single person, or to identify an individual in context. Please read our privacy policy carefully to get a clear understanding of how we collect, use, protect or otherwise handle your Personally Identifiable Information in accordance with our website. <br><br>(2) We do not collect information from visitors of our site or other details to help you with your experience.<br><br><span style=\"font-weight: bold;\">Using your Information</span><br><br>We may use the information we collect from you when you register, make a purchase, sign up for our newsletter, respond to a survey or marketing communication, surf the website, or use certain other site features in the following ways: <br><br>To personalize user's experience and to allow us to deliver the type of content and product offerings in which you are most interested.<br><br><span style=\"font-weight: bold;\">Protecting visitor information</span><br><br>Our website is scanned on a regular basis for security holes and known vulnerabilities in order to make your visit to our site as safe as possible. Your personal information is contained behind secured networks and is only accessible by a limited number of persons who have special access rights to such systems, and are required to keep the information confidential. In addition, all sensitive/credit information you supply is encrypted via Secure Socket Layer (SSL) technology.</p>",
                    "cancellationPolicy": "You have the right to withdraw from this contract within 14 days without giving any reason. The withdrawal period will expire after 14 days from the day on which you acquire, or a third party other than the carrier and indicated by you acquires, physical possession of the last good. You may use the attached model withdrawal form, but it is not obligatory. To meet the withdrawal deadline, it is sufficient for you to send your communication concerning your exercise of the right of withdrawal before the withdrawal period has expired.",
                    "imprint": "<p>Video King<br><br>Gilzeweg 24<br>4854SG Bavel<br>NL <br><br>Phone: +31 123 45 6789<br>Email: hi@video-king.nl<br><br>Represented by<br>Managing Director: Max Mustermann<br>Register Court: Amsterdam<br>Register Number: 1234.4567<br></p>",
                    "dataPrivacy": "Video King values the privacy of your personal data."
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/merchants/MER000002"
            }
        },
        {
            "type": "merchants",
            "id": "MER000001",
            "attributes": {
                "merchantName": "Spryker",
                "merchantUrl": "/en/merchant/spryker",
                "contactPersonRole": "E-Commerce Manager",
                "contactPersonTitle": "Mr",
                "contactPersonFirstName": "Harald",
                "contactPersonLastName": "Schmidt",
                "contactPersonPhone": "+49 30 208498350",
                "logoUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/spryker-logo.png",
                "publicEmail": "info@spryker.com",
                "publicPhone": "+49 30 234567891",
                "description": "Spryker is the main merchant at the Demo Marketplace.",
                "bannerUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/spryker-banner.png",
                "deliveryTime": "1-3 days",
                "latitude": "13.384458",
                "longitude": "52.534105",
                "faxNumber": "+49 30 234567800",
                "legalInformation": {
                    "terms": "<p><span style=\"font-weight: bold;\">General Terms</span><br><br>(1) This privacy policy has been compiled to better serve those who are concerned with how their 'Personally identifiable information' (PII) is being used online. PII, as used in US privacy law and information security, is information that can be used on its own or with other information to identify, contact, or locate a single person, or to identify an individual in context. Please read our privacy policy carefully to get a clear understanding of how we collect, use, protect or otherwise handle your Personally Identifiable Information in accordance with our website. <br><br>(2) We do not collect information from visitors of our site or other details to help you with your experience.<br><br><span style=\"font-weight: bold;\">Using your Information</span><br><br>We may use the information we collect from you when you register, make a purchase, sign up for our newsletter, respond to a survey or marketing communication, surf the website, or use certain other site features in the following ways: <br><br>To personalize user's experience and to allow us to deliver the type of content and product offerings in which you are most interested.<br><br><span style=\"font-weight: bold;\">Protecting visitor information</span><br><br>Our website is scanned on a regular basis for security holes and known vulnerabilities in order to make your visit to our site as safe as possible. Your personal information is contained behind secured networks and is only accessible by a limited number of persons who have special access rights to such systems, and are required to keep the information confidential. In addition, all sensitive/credit information you supply is encrypted via Secure Socket Layer (SSL) technology.</p>",
                    "cancellationPolicy": "You have the right to withdraw from this contract within 14 days without giving any reason. The withdrawal period will expire after 14 days from the day on which you acquire, or a third party other than the carrier and indicated by you acquires, physical possession of the last good. You may use the attached model withdrawal form, but it is not obligatory. To meet the withdrawal deadline, it is sufficient for you to send your communication concerning your exercise of the right of withdrawal before the withdrawal period has expired.",
                    "imprint": "<p>Spryker Systems GmbH<br><br>Julie-Wolfthorn-Straße 1<br>10115 Berlin<br>DE<br><br>Phone: +49 (30) 2084983 50<br>Email: info@spryker.com<br><br>Represented by<br>Managing Directors: Alexander Graf, Boris Lokschin<br>Register Court: Hamburg<br>Register Number: HRB 134310<br></p>",
                    "dataPrivacy": "Spryker Systems GmbH values the privacy of your personal data."
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/merchants/MER000001"
            }
        },
        {
            "type": "merchants",
            "id": "MER000006",
            "attributes": {
                "merchantName": "Sony Experts",
                "merchantUrl": "/en/merchant/sony-experts",
                "contactPersonRole": "Brand Manager",
                "contactPersonTitle": "Ms",
                "contactPersonFirstName": "Michele",
                "contactPersonLastName": "Nemeth",
                "contactPersonPhone": "030/123456789",
                "logoUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/sonyexperts-logo.png",
                "publicEmail": "support@sony-experts.com",
                "publicPhone": "+49 30 234567691",
                "description": "Capture your moment with the best cameras from Sony. From pocket-size to professional-style, they all pack features to deliver the best quality pictures.Discover the range of Sony cameras, lenses and accessories, and capture your favorite moments with precision and style with the best cameras can offer.",
                "bannerUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/sonyexperts-banner.png",
                "deliveryTime": "1-3 days",
                "latitude": "11.547788",
                "longitude": "48.131058",
                "faxNumber": "+49 30 234567600",
                "legalInformation": {
                    "terms": "<p><span style=\"font-weight: bold;\">General Terms</span><br><br>(1) This privacy policy has been compiled to better serve those who are concerned with how their 'Personally identifiable information' (PII) is being used online. PII, as used in US privacy law and information security, is information that can be used on its own or with other information to identify, contact, or locate a single person, or to identify an individual in context. Please read our privacy policy carefully to get a clear understanding of how we collect, use, protect or otherwise handle your Personally Identifiable Information in accordance with our website. <br><br>(2) We do not collect information from visitors of our site or other details to help you with your experience.<br><br><span style=\"font-weight: bold;\">Using your Information</span><br><br>We may use the information we collect from you when you register, make a purchase, sign up for our newsletter, respond to a survey or marketing communication, surf the website, or use certain other site features in the following ways: <br><br>To personalize user's experience and to allow us to deliver the type of content and product offerings in which you are most interested.<br><br><span style=\"font-weight: bold;\">Protecting visitor information</span><br><br>Our website is scanned on a regular basis for security holes and known vulnerabilities in order to make your visit to our site as safe as possible. Your personal information is contained behind secured networks and is only accessible by a limited number of persons who have special access rights to such systems, and are required to keep the information confidential. In addition, all sensitive/credit information you supply is encrypted via Secure Socket Layer (SSL) technology.</p>",
                    "cancellationPolicy": "You have the right to withdraw from this contract within 14 days without giving any reason. The withdrawal period will expire after 14 days from the day on which you acquire, or a third party other than the carrier and indicated by you acquires, physical possession of the last good. You may use the attached model withdrawal form, but it is not obligatory. To meet the withdrawal deadline, it is sufficient for you to send your communication concerning your exercise of the right of withdrawal before the withdrawal period has expired.",
                    "imprint": "<p>Sony Experts<br><br>Matthias-Pschorr-Straße 1<br>80336 München<br>DE<br><br>Phone: 030 1234567<br>Email: support@sony-experts.com<br><br>Represented by<br>Managing Director: Max Mustermann<br>Register Court: Munich<br>Register Number: HYY 134306<br></p>",
                    "dataPrivacy": "Sony Experts values the privacy of your personal data."
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/merchants/MER000006"
            }
        },
        {
            "type": "merchants",
            "id": "MER000005",
            "attributes": {
                "merchantName": "Budget Cameras",
                "merchantUrl": "/en/merchant/budget-cameras",
                "contactPersonRole": "Merchandise Manager",
                "contactPersonTitle": "Mr",
                "contactPersonFirstName": "Jason",
                "contactPersonLastName": "Weidmann",
                "contactPersonPhone": "030/123456789",
                "logoUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/budgetcameras-logo.png",
                "publicEmail": "support@budgetcamerasonline.com",
                "publicPhone": "+49 30 234567591",
                "description": "DSLR and mirrorless cameras are by far the most popular with filmmakers on a tight budget when you can't afford multiple specialist cameras.Budget Cameras is offering a great selection of digital cameras with the lowest prices.",
                "bannerUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/budgetcameras-banner.png",
                "deliveryTime": "2-4 days",
                "latitude": "10.004663",
                "longitude": "53.552463",
                "faxNumber": "+49 30 234567500",
                "legalInformation": {
                    "terms": "<p><span style=\"font-weight: bold;\">General Terms</span><br><br>(1) This privacy policy has been compiled to better serve those who are concerned with how their 'Personally identifiable information' (PII) is being used online. PII, as used in US privacy law and information security, is information that can be used on its own or with other information to identify, contact, or locate a single person, or to identify an individual in context. Please read our privacy policy carefully to get a clear understanding of how we collect, use, protect or otherwise handle your Personally Identifiable Information in accordance with our website. <br><br>(2) We do not collect information from visitors of our site or other details to help you with your experience.<br><br><span style=\"font-weight: bold;\">Using your Information</span><br><br>We may use the information we collect from you when you register, make a purchase, sign up for our newsletter, respond to a survey or marketing communication, surf the website, or use certain other site features in the following ways: <br><br>To personalize user's experience and to allow us to deliver the type of content and product offerings in which you are most interested.<br><br><span style=\"font-weight: bold;\">Protecting visitor information</span><br><br>Our website is scanned on a regular basis for security holes and known vulnerabilities in order to make your visit to our site as safe as possible. Your personal information is contained behind secured networks and is only accessible by a limited number of persons who have special access rights to such systems, and are required to keep the information confidential. In addition, all sensitive/credit information you supply is encrypted via Secure Socket Layer (SSL) technology.</p>",
                    "cancellationPolicy": "You have the right to withdraw from this contract within 14 days without giving any reason. The withdrawal period will expire after 14 days from the day on which you acquire, or a third party other than the carrier and indicated by you acquires, physical possession of the last good. You may use the attached model withdrawal form, but it is not obligatory. To meet the withdrawal deadline, it is sufficient for you to send your communication concerning your exercise of the right of withdrawal before the withdrawal period has expired.",
                    "imprint": "<p>Budget Cameras<br><br>Spitalerstraße 3<br>20095 Hamburg<br>DE<br><br>Phone: 030 1234567<br>Email: support@budgetcamerasonline.com<br><br>Represented by<br>Managing Director: Max Mustermann<br>Register Court: Hamburg<br>Register Number: HXX 134305<br></p>",
                    "dataPrivacy": "Budget Cameras values the privacy of your personal data."
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/merchants/MER000005"
            }
        }
    ]
}
```
</details>

**General order information**

| ATTRIBUTE    | TYPE  | DESCRIPTION     |
| -------------- | -------- | ----------------------- |
| merchantReferences | Array    | Merchant reference in the system. See [Merchant feature overview](/docs/marketplace/user/features/{{ page.version }}/merchants/merchants-feature-overview.html) for more details.<br>{% info_block warningBox "Note" %}This option is available only in case you have upgraded your shop to the Marketplace provided by Spryker.{% endinfo_block %}. |
| itemStates  | Array  | State of the item in the order.    |
| createdAt  | String   | Date and time when the order was created.    |
| currencyIsoCode | String | ISO 4217 code of the currency that was selected when placing the order. |
| priceMode  | String | Price mode that was active when placing the order. Possible values:<ul><li>NET_MODE—prices before tax</li><li>GROSS_MODE—prices after tax</li></ul> |

**Totals calculation**

|    ATTRIBUTE    | TYPE  |DESCRIPTION               |
| ----------------- | ------- | ------------------------------------------------------- |
| expenseTotal      | Integer | Total amount of expenses (for example, shipping costs). |
| discountTotal     | Integer | Total amount of discounts applied.                      |
| taxTotal          | Integer | Total amount of taxes paid.                             |
| subtotal          | Integer | Subtotal of the order.                                  |
| grandTotal        | Integer | Grand total of the order.                               |
| canceledTotal     | Integer | Total canceled amount.                                  |
| remunerationTotal | Integer | Total sum of remuneration.                              |

For the attributes of the included resources, see, [Retrieving merchant information](/docs/marketplace/dev/glue-api-guides/{{ page.version }}/retrieving-merchant-information.html).

## Retrieve an order

To retrieve detailed information on an order, send the request:

---
GET **/orders/{% raw %}*{{order_id}}*{% endraw %}**

---

| PATH PARAMETER | DESCRIPTION     |
| ------------------ | ------------------------------------------------------------ |
| {% raw %}***{{order_id}}***{% endraw %}       | Unique identifier of an order. [Retrieve all orders](https://documentation.spryker.com/docs/en/retrieving-customers-order-history#retrieving-all-orders) to get it. |

### Request

| HEADER KEY    | HEADER VALUE | REQUIRED | DESCRIPTION |
| ------------- | ------------ | -------- | ---------------------- |
| Authorization | string       | &check;        | Alphanumeric string that authorizes the customer to send requests to protected resources. Get it by [authenticating as a customer](https://documentation.spryker.com/authenticating-as-a-customer). |

| REQUEST | USAGE |
| ------------------------ | ------------------------ |
| `GET http://glue.mysprykershop.com/orders/DE--2`   | Retrieve information about the DE--1 order.  |
| `GET http://glue.mysprykershop.com/orders/DE--3?include=merchants` | Retrieve order DE--3 with information on merchants.<br>{% info_block warningBox "Note" %}This option is available only in case you have upgraded your shop to the Marketplace provided by Spryker.{% endinfo_block %}. |

### Response

<details>
<summary markdown='span'>Response sample: a specific order</summary>

```json
{
    "data": {
        "type": "orders",
        "id": "DE--2",
        "attributes": {
            "merchantReferences": [
                "MER000002",
                "MER000001"
            ],
            "itemStates": [
                "new"
            ],
            "createdAt": "2020-10-19 15:16:21.879286",
            "currencyIsoCode": "EUR",
            "priceMode": "GROSS_MODE",
            "totals": {
                "expenseTotal": 1590,
                "discountTotal": 3959,
                "taxTotal": 4957,
                "subtotal": 39586,
                "grandTotal": 37217,
                "canceledTotal": 0,
                "remunerationTotal": 0
            },
            "billingAddress": {
                "salutation": "Ms",
                "firstName": "Sonia",
                "middleName": null,
                "lastName": "Wagner",
                "address1": "Kirncher Str.",
                "address2": "7",
                "address3": "",
                "company": "Spryker Systems GmbH",
                "city": "Berlin",
                "zipCode": "10247",
                "poBox": null,
                "phone": "4902890031",
                "cellPhone": null,
                "description": null,
                "comment": "",
                "email": null,
                "country": "Germany",
                "iso2Code": "DE"
            },
            "shippingAddress": {
                "salutation": "Ms",
                "firstName": "Sonia",
                "middleName": null,
                "lastName": "Wagner",
                "address1": "Kirncher Str.",
                "address2": "7",
                "address3": "",
                "company": "Spryker Systems GmbH",
                "city": "Berlin",
                "zipCode": "10247",
                "poBox": null,
                "phone": "4902890031",
                "cellPhone": null,
                "description": null,
                "comment": "",
                "email": null,
                "country": "Germany",
                "iso2Code": "DE"
            },
            "items": [
                {
                    "merchantReference": "MER000002",
                    "state": "new",
                    "name": "Toshiba CAMILEO S30",
                    "sku": "205_6350138",
                    "sumPrice": 11611,
                    "quantity": 1,
                    "unitGrossPrice": 11611,
                    "sumGrossPrice": 11611,
                    "taxRate": "7.00",
                    "unitNetPrice": 0,
                    "sumNetPrice": 0,
                    "unitPrice": 11611,
                    "unitTaxAmountFullAggregation": 684,
                    "sumTaxAmountFullAggregation": 684,
                    "refundableAmount": 10450,
                    "canceledAmount": 0,
                    "sumSubtotalAggregation": 11611,
                    "unitSubtotalAggregation": 11611,
                    "unitProductOptionPriceAggregation": 0,
                    "sumProductOptionPriceAggregation": 0,
                    "unitExpensePriceAggregation": 0,
                    "sumExpensePriceAggregation": null,
                    "unitDiscountAmountAggregation": 1161,
                    "sumDiscountAmountAggregation": 1161,
                    "unitDiscountAmountFullAggregation": 1161,
                    "sumDiscountAmountFullAggregation": 1161,
                    "unitPriceToPayAggregation": 10450,
                    "sumPriceToPayAggregation": 10450,
                    "taxRateAverageAggregation": "7.00",
                    "taxAmountAfterCancellation": null,
                    "orderReference": null,
                    "uuid": "d5e948d9-f470-5b9a-b1c7-c1321761312a",
                    "isReturnable": false,
                    "bundleItemIdentifier": null,
                    "relatedBundleItemIdentifier": null,
                    "salesOrderConfiguredBundle": null,
                    "salesOrderConfiguredBundleItem": null,
                    "metadata": {
                        "superAttributes": {
                            "color": "Grey"
                        },
                        "image": "https://images.icecat.biz/img/gallery_mediums/img_6350138_medium_1481633011_6285_13738.jpg"
                    },
                    "salesUnit": null,
                    "calculatedDiscounts": [
                        {
                            "unitAmount": 1161,
                            "sumAmount": 1161,
                            "displayName": "10% Discount for all orders above",
                            "description": "Get a 10% discount on all orders above certain value depending on the currency and net/gross price. This discount is not exclusive and can be combined with other discounts.",
                            "voucherCode": null,
                            "quantity": 1
                        }
                    ],
                    "productOptions": [],
                    "amount": null
                },
                {
                    "merchantReference": "MER000001",
                    "state": "new",
                    "name": "Samsung Galaxy Note 4",
                    "sku": "061_24752508",
                    "sumPrice": 27975,
                    "quantity": 1,
                    "unitGrossPrice": 27975,
                    "sumGrossPrice": 27975,
                    "taxRate": "19.00",
                    "unitNetPrice": 0,
                    "sumNetPrice": 0,
                    "unitPrice": 27975,
                    "unitTaxAmountFullAggregation": 4020,
                    "sumTaxAmountFullAggregation": 4020,
                    "refundableAmount": 25177,
                    "canceledAmount": 0,
                    "sumSubtotalAggregation": 27975,
                    "unitSubtotalAggregation": 27975,
                    "unitProductOptionPriceAggregation": 0,
                    "sumProductOptionPriceAggregation": 0,
                    "unitExpensePriceAggregation": 0,
                    "sumExpensePriceAggregation": null,
                    "unitDiscountAmountAggregation": 2798,
                    "sumDiscountAmountAggregation": 2798,
                    "unitDiscountAmountFullAggregation": 2798,
                    "sumDiscountAmountFullAggregation": 2798,
                    "unitPriceToPayAggregation": 25177,
                    "sumPriceToPayAggregation": 25177,
                    "taxRateAverageAggregation": "19.00",
                    "taxAmountAfterCancellation": null,
                    "orderReference": null,
                    "uuid": "dedc66da-9af9-504f-bdfc-e45b23118786",
                    "isReturnable": false,
                    "bundleItemIdentifier": null,
                    "relatedBundleItemIdentifier": null,
                    "salesOrderConfiguredBundle": null,
                    "salesOrderConfiguredBundleItem": null,
                    "metadata": {
                        "superAttributes": {
                            "color": "Black"
                        },
                        "image": "https://images.icecat.biz/img/norm/medium/24752508-8866.jpg"
                    },
                    "salesUnit": null,
                    "calculatedDiscounts": [
                        {
                            "unitAmount": 2798,
                            "sumAmount": 2798,
                            "displayName": "10% Discount for all orders above",
                            "description": "Get a 10% discount on all orders above certain value depending on the currency and net/gross price. This discount is not exclusive and can be combined with other discounts.",
                            "voucherCode": null,
                            "quantity": 1
                        }
                    ],
                    "productOptions": [],
                    "amount": null
                }
            ],
            "expenses": [
                {
                    "type": "SHIPMENT_EXPENSE_TYPE",
                    "name": "Express",
                    "sumPrice": 590,
                    "unitGrossPrice": 590,
                    "sumGrossPrice": 590,
                    "taxRate": "19.00",
                    "unitNetPrice": 0,
                    "sumNetPrice": 0,
                    "canceledAmount": null,
                    "unitDiscountAmountAggregation": null,
                    "sumDiscountAmountAggregation": null,
                    "unitTaxAmount": 94,
                    "sumTaxAmount": 94,
                    "unitPriceToPayAggregation": 590,
                    "sumPriceToPayAggregation": 590,
                    "taxAmountAfterCancellation": null
                },
                {
                    "type": "SHIPMENT_EXPENSE_TYPE",
                    "name": "Air Sonic",
                    "sumPrice": 1000,
                    "unitGrossPrice": 1000,
                    "sumGrossPrice": 1000,
                    "taxRate": "19.00",
                    "unitNetPrice": 0,
                    "sumNetPrice": 0,
                    "canceledAmount": null,
                    "unitDiscountAmountAggregation": null,
                    "sumDiscountAmountAggregation": null,
                    "unitTaxAmount": 159,
                    "sumTaxAmount": 159,
                    "unitPriceToPayAggregation": 1000,
                    "sumPriceToPayAggregation": 1000,
                    "taxAmountAfterCancellation": null
                }
            ],
            "payments": [
                {
                    "amount": 37217,
                    "paymentProvider": "DummyMarketplacePayment",
                    "paymentMethod": "Marketplace Invoice"
                }
            ],
            "shipments": [],
            "calculatedDiscounts": {
                "10% Discount for all orders above": {
                    "unitAmount": null,
                    "sumAmount": 3959,
                    "displayName": "10% Discount for all orders above",
                    "description": "Get a 10% discount on all orders above certain value depending on the currency and net/gross price. This discount is not exclusive and can be combined with other discounts.",
                    "voucherCode": null,
                    "quantity": 2
                }
            },
            "bundleItems": []
        },
        "links": {
            "self": "https://glue.mysprykershop.com/orders/DE--2"
        }
    }
}
```
</details>

<details>
<summary markdown='span'>Response sample with information on merchants</summary>

```json
{
    "data": {
        "type": "orders",
        "id": "DE--2",
        "attributes": {
            "merchantReferences": [
                "MER000002",
                "MER000001"
            ],
            "itemStates": [
                "new"
            ],
            "createdAt": "2020-10-19 15:16:21.879286",
            "currencyIsoCode": "EUR",
            "priceMode": "GROSS_MODE",
            "totals": {
                "expenseTotal": 1590,
                "discountTotal": 3959,
                "taxTotal": 4957,
                "subtotal": 39586,
                "grandTotal": 37217,
                "canceledTotal": 0,
                "remunerationTotal": 0
            },
            "billingAddress": {
                "salutation": "Ms",
                "firstName": "Sonia",
                "middleName": null,
                "lastName": "Wagner",
                "address1": "Kirncher Str.",
                "address2": "7",
                "address3": "",
                "company": "Spryker Systems GmbH",
                "city": "Berlin",
                "zipCode": "10247",
                "poBox": null,
                "phone": "4902890031",
                "cellPhone": null,
                "description": null,
                "comment": "",
                "email": null,
                "country": "Germany",
                "iso2Code": "DE"
            },
            "shippingAddress": {
                "salutation": "Ms",
                "firstName": "Sonia",
                "middleName": null,
                "lastName": "Wagner",
                "address1": "Kirncher Str.",
                "address2": "7",
                "address3": "",
                "company": "Spryker Systems GmbH",
                "city": "Berlin",
                "zipCode": "10247",
                "poBox": null,
                "phone": "4902890031",
                "cellPhone": null,
                "description": null,
                "comment": "",
                "email": null,
                "country": "Germany",
                "iso2Code": "DE"
            },
            "items": [
                {
                    "merchantReference": "MER000002",
                    "state": "new",
                    "name": "Toshiba CAMILEO S30",
                    "sku": "205_6350138",
                    "sumPrice": 11611,
                    "quantity": 1,
                    "unitGrossPrice": 11611,
                    "sumGrossPrice": 11611,
                    "taxRate": "7.00",
                    "unitNetPrice": 0,
                    "sumNetPrice": 0,
                    "unitPrice": 11611,
                    "unitTaxAmountFullAggregation": 684,
                    "sumTaxAmountFullAggregation": 684,
                    "refundableAmount": 10450,
                    "canceledAmount": 0,
                    "sumSubtotalAggregation": 11611,
                    "unitSubtotalAggregation": 11611,
                    "unitProductOptionPriceAggregation": 0,
                    "sumProductOptionPriceAggregation": 0,
                    "unitExpensePriceAggregation": 0,
                    "sumExpensePriceAggregation": null,
                    "unitDiscountAmountAggregation": 1161,
                    "sumDiscountAmountAggregation": 1161,
                    "unitDiscountAmountFullAggregation": 1161,
                    "sumDiscountAmountFullAggregation": 1161,
                    "unitPriceToPayAggregation": 10450,
                    "sumPriceToPayAggregation": 10450,
                    "taxRateAverageAggregation": "7.00",
                    "taxAmountAfterCancellation": null,
                    "orderReference": null,
                    "uuid": "d5e948d9-f470-5b9a-b1c7-c1321761312a",
                    "isReturnable": false,
                    "bundleItemIdentifier": null,
                    "relatedBundleItemIdentifier": null,
                    "salesOrderConfiguredBundle": null,
                    "salesOrderConfiguredBundleItem": null,
                    "metadata": {
                        "superAttributes": {
                            "color": "Grey"
                        },
                        "image": "https://images.icecat.biz/img/gallery_mediums/img_6350138_medium_1481633011_6285_13738.jpg"
                    },
                    "salesUnit": null,
                    "calculatedDiscounts": [
                        {
                            "unitAmount": 1161,
                            "sumAmount": 1161,
                            "displayName": "10% Discount for all orders above",
                            "description": "Get a 10% discount on all orders above certain value depending on the currency and net/gross price. This discount is not exclusive and can be combined with other discounts.",
                            "voucherCode": null,
                            "quantity": 1
                        }
                    ],
                    "productOptions": [],
                    "amount": null
                },
                {
                    "merchantReference": "MER000001",
                    "state": "new",
                    "name": "Samsung Galaxy Note 4",
                    "sku": "061_24752508",
                    "sumPrice": 27975,
                    "quantity": 1,
                    "unitGrossPrice": 27975,
                    "sumGrossPrice": 27975,
                    "taxRate": "19.00",
                    "unitNetPrice": 0,
                    "sumNetPrice": 0,
                    "unitPrice": 27975,
                    "unitTaxAmountFullAggregation": 4020,
                    "sumTaxAmountFullAggregation": 4020,
                    "refundableAmount": 25177,
                    "canceledAmount": 0,
                    "sumSubtotalAggregation": 27975,
                    "unitSubtotalAggregation": 27975,
                    "unitProductOptionPriceAggregation": 0,
                    "sumProductOptionPriceAggregation": 0,
                    "unitExpensePriceAggregation": 0,
                    "sumExpensePriceAggregation": null,
                    "unitDiscountAmountAggregation": 2798,
                    "sumDiscountAmountAggregation": 2798,
                    "unitDiscountAmountFullAggregation": 2798,
                    "sumDiscountAmountFullAggregation": 2798,
                    "unitPriceToPayAggregation": 25177,
                    "sumPriceToPayAggregation": 25177,
                    "taxRateAverageAggregation": "19.00",
                    "taxAmountAfterCancellation": null,
                    "orderReference": null,
                    "uuid": "dedc66da-9af9-504f-bdfc-e45b23118786",
                    "isReturnable": false,
                    "bundleItemIdentifier": null,
                    "relatedBundleItemIdentifier": null,
                    "salesOrderConfiguredBundle": null,
                    "salesOrderConfiguredBundleItem": null,
                    "metadata": {
                        "superAttributes": {
                            "color": "Black"
                        },
                        "image": "https://images.icecat.biz/img/norm/medium/24752508-8866.jpg"
                    },
                    "salesUnit": null,
                    "calculatedDiscounts": [
                        {
                            "unitAmount": 2798,
                            "sumAmount": 2798,
                            "displayName": "10% Discount for all orders above",
                            "description": "Get a 10% discount on all orders above certain value depending on the currency and net/gross price. This discount is not exclusive and can be combined with other discounts.",
                            "voucherCode": null,
                            "quantity": 1
                        }
                    ],
                    "productOptions": [],
                    "amount": null
                }
            ],
            "expenses": [
                {
                    "type": "SHIPMENT_EXPENSE_TYPE",
                    "name": "Express",
                    "sumPrice": 590,
                    "unitGrossPrice": 590,
                    "sumGrossPrice": 590,
                    "taxRate": "19.00",
                    "unitNetPrice": 0,
                    "sumNetPrice": 0,
                    "canceledAmount": null,
                    "unitDiscountAmountAggregation": null,
                    "sumDiscountAmountAggregation": null,
                    "unitTaxAmount": 94,
                    "sumTaxAmount": 94,
                    "unitPriceToPayAggregation": 590,
                    "sumPriceToPayAggregation": 590,
                    "taxAmountAfterCancellation": null
                },
                {
                    "type": "SHIPMENT_EXPENSE_TYPE",
                    "name": "Air Sonic",
                    "sumPrice": 1000,
                    "unitGrossPrice": 1000,
                    "sumGrossPrice": 1000,
                    "taxRate": "19.00",
                    "unitNetPrice": 0,
                    "sumNetPrice": 0,
                    "canceledAmount": null,
                    "unitDiscountAmountAggregation": null,
                    "sumDiscountAmountAggregation": null,
                    "unitTaxAmount": 159,
                    "sumTaxAmount": 159,
                    "unitPriceToPayAggregation": 1000,
                    "sumPriceToPayAggregation": 1000,
                    "taxAmountAfterCancellation": null
                }
            ],
            "payments": [
                {
                    "amount": 37217,
                    "paymentProvider": "DummyMarketplacePayment",
                    "paymentMethod": "Marketplace Invoice"
                }
            ],
            "shipments": [],
            "calculatedDiscounts": {
                "10% Discount for all orders above": {
                    "unitAmount": null,
                    "sumAmount": 3959,
                    "displayName": "10% Discount for all orders above",
                    "description": "Get a 10% discount on all orders above certain value depending on the currency and net/gross price. This discount is not exclusive and can be combined with other discounts.",
                    "voucherCode": null,
                    "quantity": 2
                }
            },
            "bundleItems": []
        },
        "links": {
            "self": "https://glue.mysprykershop.com/orders/DE--2?include=merchants"
        },
        "relationships": {
            "merchants": {
                "data": [
                    {
                        "type": "merchants",
                        "id": "MER000002"
                    },
                    {
                        "type": "merchants",
                        "id": "MER000001"
                    }
                ]
            }
        }
    },
    "included": [
        {
            "type": "merchants",
            "id": "MER000002",
            "attributes": {
                "merchantName": "Video King",
                "merchantUrl": "/en/merchant/video-king",
                "contactPersonRole": "Country Manager DE",
                "contactPersonTitle": "Ms",
                "contactPersonFirstName": "Martha",
                "contactPersonLastName": "Farmer",
                "contactPersonPhone": "+31 123 345 678",
                "logoUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/videoking-logo.png",
                "publicEmail": "hi@video-king.nl",
                "publicPhone": "+31 123 345 777",
                "description": "Video King is a premium provider of video equipment. In business since 2010, we understand the needs of video professionals and enthusiasts and offer a wide variety of products with competitive prices. ",
                "bannerUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/videoking-banner.png",
                "deliveryTime": "2-4 days",
                "latitude": "4.838470",
                "longitude": "51.558107",
                "faxNumber": "+31 123 345 733",
                "legalInformation": {
                    "terms": "<p><span style=\"font-weight: bold;\">General Terms</span><br><br>(1) This privacy policy has been compiled to better serve those who are concerned with how their 'Personally identifiable information' (PII) is being used online. PII, as used in US privacy law and information security, is information that can be used on its own or with other information to identify, contact, or locate a single person, or to identify an individual in context. Please read our privacy policy carefully to get a clear understanding of how we collect, use, protect or otherwise handle your Personally Identifiable Information in accordance with our website. <br><br>(2) We do not collect information from visitors of our site or other details to help you with your experience.<br><br><span style=\"font-weight: bold;\">Using your Information</span><br><br>We may use the information we collect from you when you register, make a purchase, sign up for our newsletter, respond to a survey or marketing communication, surf the website, or use certain other site features in the following ways: <br><br>To personalize user's experience and to allow us to deliver the type of content and product offerings in which you are most interested.<br><br><span style=\"font-weight: bold;\">Protecting visitor information</span><br><br>Our website is scanned on a regular basis for security holes and known vulnerabilities in order to make your visit to our site as safe as possible. Your personal information is contained behind secured networks and is only accessible by a limited number of persons who have special access rights to such systems, and are required to keep the information confidential. In addition, all sensitive/credit information you supply is encrypted via Secure Socket Layer (SSL) technology.</p>",
                    "cancellationPolicy": "You have the right to withdraw from this contract within 14 days without giving any reason. The withdrawal period will expire after 14 days from the day on which you acquire, or a third party other than the carrier and indicated by you acquires, physical possession of the last good. You may use the attached model withdrawal form, but it is not obligatory. To meet the withdrawal deadline, it is sufficient for you to send your communication concerning your exercise of the right of withdrawal before the withdrawal period has expired.",
                    "imprint": "<p>Video King<br><br>Gilzeweg 24<br>4854SG Bavel<br>NL <br><br>Phone: +31 123 45 6789<br>Email: hi@video-king.nl<br><br>Represented by<br>Managing Director: Max Mustermann<br>Register Court: Amsterdam<br>Register Number: 1234.4567<br></p>",
                    "dataPrivacy": "Video King values the privacy of your personal data."
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/merchants/MER000002"
            }
        },
        {
            "type": "merchants",
            "id": "MER000001",
            "attributes": {
                "merchantName": "Spryker",
                "merchantUrl": "/en/merchant/spryker",
                "contactPersonRole": "E-Commerce Manager",
                "contactPersonTitle": "Mr",
                "contactPersonFirstName": "Harald",
                "contactPersonLastName": "Schmidt",
                "contactPersonPhone": "+49 30 208498350",
                "logoUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/spryker-logo.png",
                "publicEmail": "info@spryker.com",
                "publicPhone": "+49 30 234567891",
                "description": "Spryker is the main merchant at the Demo Marketplace.",
                "bannerUrl": "https://d2s0ynfc62ej12.cloudfront.net/merchant/spryker-banner.png",
                "deliveryTime": "1-3 days",
                "latitude": "13.384458",
                "longitude": "52.534105",
                "faxNumber": "+49 30 234567800",
                "legalInformation": {
                    "terms": "<p><span style=\"font-weight: bold;\">General Terms</span><br><br>(1) This privacy policy has been compiled to better serve those who are concerned with how their 'Personally identifiable information' (PII) is being used online. PII, as used in US privacy law and information security, is information that can be used on its own or with other information to identify, contact, or locate a single person, or to identify an individual in context. Please read our privacy policy carefully to get a clear understanding of how we collect, use, protect or otherwise handle your Personally Identifiable Information in accordance with our website. <br><br>(2) We do not collect information from visitors of our site or other details to help you with your experience.<br><br><span style=\"font-weight: bold;\">Using your Information</span><br><br>We may use the information we collect from you when you register, make a purchase, sign up for our newsletter, respond to a survey or marketing communication, surf the website, or use certain other site features in the following ways: <br><br>To personalize user's experience and to allow us to deliver the type of content and product offerings in which you are most interested.<br><br><span style=\"font-weight: bold;\">Protecting visitor information</span><br><br>Our website is scanned on a regular basis for security holes and known vulnerabilities in order to make your visit to our site as safe as possible. Your personal information is contained behind secured networks and is only accessible by a limited number of persons who have special access rights to such systems, and are required to keep the information confidential. In addition, all sensitive/credit information you supply is encrypted via Secure Socket Layer (SSL) technology.</p>",
                    "cancellationPolicy": "You have the right to withdraw from this contract within 14 days without giving any reason. The withdrawal period will expire after 14 days from the day on which you acquire, or a third party other than the carrier and indicated by you acquires, physical possession of the last good. You may use the attached model withdrawal form, but it is not obligatory. To meet the withdrawal deadline, it is sufficient for you to send your communication concerning your exercise of the right of withdrawal before the withdrawal period has expired.",
                    "imprint": "<p>Spryker Systems GmbH<br><br>Julie-Wolfthorn-Straße 1<br>10115 Berlin<br>DE<br><br>Phone: +49 (30) 2084983 50<br>Email: info@spryker.com<br><br>Represented by<br>Managing Directors: Alexander Graf, Boris Lokschin<br>Register Court: Hamburg<br>Register Number: HRB 134310<br></p>",
                    "dataPrivacy": "Spryker Systems GmbH values the privacy of your personal data."
                }
            },
            "links": {
                "self": "https://glue.mysprykershop.com/merchants/MER000001"
            }
        }
    ]
}
```
</details>

**General order information**

| ATTRIBUTE     | TYPE | DESCRIPTION            |
| ------------------ | -------- | ------------------------ |
| merchantReferences | Array    | Merchant reference in the system.This option is available only in case you have upgraded your shop to the Marketplace( provided by Spryker. |
| itemStates         | Array    | State of the item in the order.                          |
| createdAt          | String   | Date and time when the order was created.           |
| currencyIsoCode    | String   | ISO 4217 code of the currency that was selected when placing the order. |
| priceMode          | String   | Price mode that was active when placing the order. Possible values:<ul><li>NET_MODE—prices before tax.</li><li>GROSS_MODE—prices after tax.</li><ul> |

**Totals calculations**

| ATTRIBUTE     | TYPE | DESCRIPTION                |
| ----------------- | -------- | --------------- |
| expenseTotal      | Integer  | Total amount of expenses (for example, shipping costs). |
| discountTotal     | Integer  | Total amount of discounts applied.                      |
| taxTotal          | Integer  | Total amount of taxes paid.                             |
| subtotal          | Integer  | Subtotal of the order.                                  |
| grandTotal        | Integer  | Grand total of the order                                |
| canceledTotal     | Integer  | Total canceled amount.                                  |
| remunerationTotal | Integer  | Total sum of remuneration.                              |

**Billing and shipping addresses**

| ATTRIBUTE     | TYPE | DESCRIPTION                  |
| ----------------- | -------- | --------------------------------- |
| salutation        | String   | Salutation to use when addressing the customer.  |
| firstName         | String   | Customer's first name.                                       |
| lastName          | String   | Customer's last name.                                        |
| address1          | String   | The 1st line of the customer's address.                      |
| address2          | String   | The 2nd line of the customer's address.                      |
| address3          | String   | The 3rd line of the customer's address.                      |
| zipCode           | String   | ZIP code.                                                    |
| city              | String   | Specifies the city.                                          |
| country           | String   | Specifies the country.                                       |
| poBox             | String   | PO Box to use for communication.                             |
| company           | String   | Specifies the customer's company.                            |
| phone             | String   | Specifies the customer's phone number.                       |
| cellPhone         | String   | Mobile phone number.                                         |
| email             | String   | Email address to use for communication.                      |
| isDefaultShipping | Boolean  | Specifies whether the address should be used as the default shipping address of the customer. If the parameter is not set, the default value is `true`. If the customer does not have a default shipping address, the value is 'true'. |
| isDefaultBilling  | Boolean  | Specifies whether the address should be used as the default billing address of the customerIf the parameter is not set, the default value is `true`. If the customer does not have a default billing address, the value is `true`. |
| iso2Code          | String   | ISO 2-Letter Country Code to use.                            |
| description       | String   | Address description.                                         |
| comment           | String   | Address comment.                                             |

**Order item information**

| ATTRIBUTE | TYPE | DESCRIPTION     |
| -------------------- | -------- | ----------------------------- |
| name                     | String   | Name of the product.                                         |
| sku                      | String   | SKU of the product.                                          |
| sumPrice                 | Integer  | Sum of the prices.                                           |
| sumPriceToPayAggregation | Integer  | Sum of the prices to pay (after discounts).       |
| quantity                 | Integer  | Quantity of the product ordered.                             |
| superAttributes          | String   | Since the bought product is a concrete product, and super attributes are saved with the abstract product, this field is expected to stay empty. |
| image                    | String   | URL to an image of the product.                              |

**Order item information** (for each item)

| ATTRIBUTE   | TYPE | DESCRIPTION   |
| ---------------- | -------- | ---------------------------- |
| name                              | String   | Product name.                                                |
| SKU                               | String   | Product SKU.                                                 |
| sumPrice                          | Integer  | Sum of all product prices.       |
| quantity                          | Integer  | Product quantity ordered.      |
| unitGrossPrice                    | Integer  | Single item gross price.   |
| sumGrossPrice                     | Integer  | Sum of items gross price.    |
| taxRate                           | Integer  | Current tax rate, in percent.  |
| unitNetPrice                      | Integer  | Single item net price.    |
| sumNetPrice                       | Integer  | Sum total of net prices for all items.   |
| unitPrice       | Integer  | Single item price without assuming if it is net or gross. *This price should be displayed everywhere when a product price is displayed. It allows switching tax mode without side effects*. |
| unitTaxAmountFullAggregation      | Integer  | Total tax amount for a given item, with additions.    |
| sumTaxAmountFullAggregation   | Integer  | Total tax amount for a given sum of items, with additions.   |
| refundableAmount   | Integer  | Available refundable amount for an item (order only).   |
| canceledAmount   | Integer  | Total canceled amount for this item (order only). |
| sumSubtotalAggregation  | Integer  | Sum of subtotals of the items.  |
| unitSubtotalAggregation  | Integer  | Subtotal for the given item. |
| unitProductOptionPriceAggregation | Integer  | Item total product option price.  |
| sumProductOptionPriceAggregation  | Integer  | Item total of product options for the given sum of items.  |
| unitExpensePriceAggregation  | Integer  | Item expense total for a given item.  |
| sumExpensePriceAggregation        | Integer  | Total amount of expenses for the given items.   |
| unitDiscountAmountAggregation  | Integer  | Item total discount amount.      |
| sumDiscountAmountAggregation   | Integer  | Sum of item total discount amounts.   |
| unitDiscountAmountFullAggregation | Integer  | Sum of item total discount amount.   |
| sumDiscountAmountFullAggregation  | Integer  | Item total discount amount, with additions. |
| unitPriceToPayAggregation     | Integer  | Item total price to pay after discounts, with additions.     |
| sumPriceToPayAggregation   | Integer  | Sum of all prices to pay (after discounts were applied).     |
| taxRateAverageAggregation   | Integer  | Item tax rate average, with additions. This value is used when recalculating the tax amount after cancellation. |
| taxAmountAfterCancellation    | Integer  | Tax amount after cancellation, recalculated using tax average. |
| uuid    | String   | Unique identifier of the order.    |
| isReturnable    | Boolean  | Specifies whether the sales order item is returnable or not. |
| superAttributes    | String   | Always empty. Since products purchased are concrete products, and super attributes are available for abstract products, this field is expected to be empty at all times. |
| image    | String   | Product image URL.     |

**Calculated discounts for items**

| ATTRIBUTE | TYPE | DESCRIPTION         |
| ------------- | -------- | ------------------------------- |
| unitAmount    | Integer  | Discount value applied to each order item of the corresponding product. |
| sumAmount     | Integer  | Sum of the discount values applied to the order items of the corresponding product. |
| displayName   | String   | Name of the discount applied.                                |
| description   | String   | Description of the discount.                                 |
| voucherCode   | String   | Voucher code redeemed.                                       |
| quantity      | String   | Number of discounts applied to the corresponding product.    |

**Product options**

| ATTRIBUTE  | TYPE | DESCRIPTION      |
| ------------ | -------- | -------------------------- |
| sku          | String   | SKU of the product option.    |
| optionName   | String   | Name of the product option.   |
| price        | Integer  | Price for the product option. |

**Calculated discounts**

| ATTRIBUTE | TYPE | DESCRIPTION       |
| ------------- | -------- | --------------------------- |
| unitAmount    | Integer  | Amount of the discount provided by the given item for each unit of the product, in cents. |
| sumAmount     | Integer  | Total amount of the discount provided by the given item, in cents. |
| displayName   | String   | Display name of the given discount.                          |
| description   | String   | Description of the given discount.                           |
| voucherCode   | String   | Voucher code applied if any.                                |
| quantity      | String   | Number of times the discount was applied.                    |

**Expenses**

| ATTRIBUTE    | TYPE | DESCRIPTION          |
| ------------------- | -------- | ---------------------- |
| type      | String   | Expense type.       |
| name       | String   | Expense name.       |
| sumPrice    | Integer  | Sum of expenses calculated.      |
| unitGrossPrice    | Integer  | Single item's gross price.    |
| sumGrossPrice   | Integer  | Sum of items' gross price.    |
| taxRate    | Integer  | Current tax rate in percent.   |
| unitNetPrice   | Integer  | Single item net price.      |
| sumNetPrice     | Integer  | Sum of items' net price.    |
| canceledAmount   | Integer  | Total canceled amount for this item (order only).  |
| unitDiscountAmountAggregation | Integer  | Item total discount amount.   |
| sumDiscountAmountAggregation  | Integer  | Sum of items' total discount amount.    |
| unitTaxAmount    | Integer  | Tax amount for a single item after discounts.   |
| sumTaxAmount     | Integer  | Tax amount for a sum of items (order only).   |
| unitPriceToPayAggregation  | Integer  | Item total price to pay after discounts with additions.   |
| sumPriceToPayAggregation   | Integer  | Sum of items' total price to pay after discounts with additions. |
| taxAmountAfterCancellation    | Integer  | Tax amount after cancellation, recalculated using tax average. |

**Measurement unit calculations**

| ATTRIBUTE  | TYPE | DESCRIPTION              |
| --------------- | -------- | ----------------------------- |
| salesUnit       | Object   | List of attributes defining the sales unit to be used for item amount calculation. |
| conversion      | integer  | Factor to convert a value from sales to a base unit. If it is `null`, the information is taken from the global conversions. |
| precision       | integer  | Ratio between a sales unit and base unit.                  |
| measurementUnit | string   | Code of the measurement unit.                                |
| name            | String   | Name of the measurement unit.                                |
| code            | String   | Code of the measurement unit.                                |

**Payments**

| ATTRIBUTE  | TYPE | DESCRIPTION   |
| --------------- | -------- | -------------------------- |
| amount          | Integer  | Amount paid via the corresponding payment provider in cents. |
| paymentProvider | String   | Name of the payment provider.                                |
| paymentMethod   | String   | Name of the payment method.                                  |

**Shipments**

| ATTRIBUTE     | TYPE | DESCRIPTION      |
| ------------------ | ----------- | ------------------------ |
| shipmentMethodName | String      | Shipment method name.   |
| carrierName        | String      | Shipment method name.        |
| deliveryTime       | DateTimeUtc | Desired delivery time, if available.    |
| defaultGrossPrice  | Integer     | Default gross price of delivery, in cents.   |
| defaultNetPrice    | Integer     | Default net price of delivery, in cents.   |
| currencyIsoCode    | String      | ISO 4217 code of the currency in which the prices are specified. |

For the attributes of the included resources, see, [Retrieving merchant information](/docs/marketplace/dev/glue-api-guides/{{ page.version }}/retrieving-merchant-information.html).