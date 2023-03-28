# Page Load Completed

### Page Load Completed is part of the page load sequence, including virtual page loads in the case of single page apps, and must be the last event pushed in the page load event sequence.

## Javascript Code
```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ page_data: null });  // Clear the previous page_data object.
dataLayer.push({
  "event": "page_view",
  "detailed_event": "Page Load Completed",
    "page_data": {
        "country": "<country>",
        "language": "<language>",
        "page_title": "<page_title>",
        "page_variant": "<page_variant>",
        "product_category_level_1": "<product_category_level_1>",
        "product_category_level_2": "<product_category_level_2>",
        "site_section": "<site_section>"
    }
});
```

## Variable Definitions

|Path|Type|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|page_data.country|string|The country associated with the current page.|US, CA, FR, UK|||||||
|page_data.language|string|The language of the current page, usually pulled from the &lt;html&gt; tag lang attribute.|en-us, en-gb, ch-cn, fr-ca, fr-fr|||||||
|page_data.page_title|string|The title of the page currently being viewed, generally available in &lt;title&gt;.||||||||
|page_data.page_variant|string|When a feature ramp up is taking place, capture a code to identify users receiving that feature's experience.||||||||
|page_data.product_category_level_1|string|Defines the main product\/service defined on that page|MFH, Flood Insurance|||||||
|page_data.product_category_level_2|string|Defines the additional products offered under the main product category|Deposit Solutions|||||||
|page_data.site_section|string|The section of the site that the current page resides in. site\_section2 through site\_section5can also be used if the site has many sections.||||||||




