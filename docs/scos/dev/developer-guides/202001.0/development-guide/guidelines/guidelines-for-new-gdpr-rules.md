---
title: Guidelines for New GDPR Rules
description: GDPR contains rules relating to the protection and control of personal data.
originalLink: https://documentation.spryker.com/v4/docs/guidelines-for-new-gdpr-rules
originalArticleId: be6986ad-1572-4e5e-ba04-11e1f36b85bc
redirect_from:
  - /v4/docs/guidelines-for-new-gdpr-rules
  - /v4/docs/en/guidelines-for-new-gdpr-rules
---

As of May, the 25th 2018 the new General Data Protection Regulations (GDPR) will take effect. This information describes the ways that the Spryker Commerce OS supports regulatory compliance with the GDPR.

GDPR contains rules relating to the protection and control of personal data. 
For more information about GDPR, see:

* [The official site](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A32016R0679)
* A nice online [summary](https://gdpr-info.eu/)

In general terms of functionality, compliance is established through a customer’s ability to delete their account information and subscribe or unsubscribe to newsletters. Shop owners can delete customer accounts through the Administration Interface. In both cases, these actions do not affect billing and order related information. The process of deleting an account anonymizes customer information and address data but retains the relevant transaction details.

However, Spryker has no complete access to customer implementations and has no control systems that are implemented and deployed. Therefore, we can only provide partial aid with GDPR compliance by providing features (like account deletion or consent withdrawal) to support customers becoming GDPR compliant.

To further support our customers, we compiled a few notes and guidelines that can help. This information does not in any way replace any kind of official legal consulting which needs to be done by the customers themselves in order to be adjusted to each company’s business model. Moreover, all customers use 3rd party and own integrations with their tech infrastructure (DB, log files, CRM, mail providers) and need to oversee GDPR compliance of those connections too.

## General Ecommerce Guidelines

|                          What to do                          |                             How                              |                             When                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|                1. Collect only what you need                 | Only ask customers for data necessary for processing a request. Avoid collecting as much as you can without reason. Make sure you review your forms such as registration forms, subscription forms, contact forms, log files and 3rd-party integrations. Assess if you can justify each piece of information you collect. | During the Project implementation process and before going live with your project. For live projects, assess, evaluate and implement changes before May the 25th, 2018. |
|    2. Explain why the information collected is necessary     | Review data privacy statement, terms & conditions, newsletter subscription conditions, promo campaign conditions.Tips:Explain why certain data is needed to be collected in simple language.Avoid very long texts. | During the Project implementation process and before going live with your project. For live projects, assess, evaluate and implement changes before May the 25th, 2018. |
|                   3. Get customer consent                    | Replace preselected checkboxes to accept T&C, data privacy, newsletter subscription etc. with empty checkboxes.Offer a double opt-in process for newsletter subscription or other kinds of registration (e.g. account, loyalty program) | Double Opt-in functionality is an out-of-the-box feature for the newsletter subscription. All other measures should be taken during the Project implementation process and before going live with your project. For live projects, assess, evaluate and implement changes before May the 25th, 2018. |
|             4. Allow customers withdraw consent              | Use the consent withdrawal feature for newsletter subscription, data privacy statement etc. Spryker provides a “Delete account” feature for T&C and data privacy, without agreeing to terms there is no way to use the website.Add a checkbox to Unsubscribe from newsletters and to delete an email address from the Database. | Delete Account is an out-of-the-box feature. All other measures should be taken during the Project implementation process and before going live with your project. For live projects, assess, evaluate and implement changes before May the 25th, 2018. |
| 5. Allow customers get the copy of personal data in a readable form (PDF, text file) | Offer a “Copy of all data” feature which includes information from all data sources (Spryker, CRM, log files, 3rd-party applications). Spryker has a “User Account” page that shows the customer information: profile, orders, preferences. The information on this page can be saved as a PDF file and shared upon request. | User Accounts is an out-of-the-box feature. All other measures should be taken during the Project implementation process and before going live with your project. For live projects, assess, evaluate and implement changes before May the 25th, 2018. |
|              6. Allow deletion of personal data              | Use the “Delete Account” feature to anonymize customer information. Some information needs to be kept for other reasons (transactional information, order information for fiscal authorities etc.)Review and establish an Unsubscribe option that will delete the Email address from the respective Database.Add an Unsubscribe link to email communication. | Delete Account is an out-of-the-box feature. All other measures should be taken during the Project implementation process and before going live with your project. For live projects, assess, evaluate and implement changes before May the 25th, 2018. |
| 7. Control 3rd Party Integration Permissions and Data Collection | Offer an option to review and revoke access for 3rd-party integrations (Social media, payment providers etc.)Review data which is shared with 3rd-parties and make sure it is reflected and represented in data privacy and T&C (e.g. IP address for 3rd party payment provider integration).Check all existing “General Data Processing Agreements” for validity. | During the Project implementation process and before going live with your project. For live projects, assess, evaluate and implement changes before May the 25th, 2018.*Make sure you have valid "General Data Processing Agreements" with all 3rd party providers. |