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
        "audience_segment": "<audience_segment>",
        "line_of_business": "<line_of_business>",
        "page_title": "<page_title>",
        "page_variant": "<page_variant>",
        "product_category_level_1": "<product_category_level_1>",
        "site_section": "<site_section>"
    }
});
```

## Variable Definitions

|Path|Type|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|page_data.audience_segment|string|Custom DLV source for Assurant.com's Audience Segment||||||||
|page_data.line_of_business|string|Custom DLV for Assurant.com's line of business||||||||
|page_data.page_title|string|The title of the page currently being viewed, generally available in &lt;title&gt;.||||||||
|page_data.page_variant|string|When a feature ramp up is taking place, capture a code to identify users receiving that feature's experience.||||||||
|page_data.product_category_level_1|string|Defines the main product\/service defined on that page|MFH, Flood Insurance|||||||
|page_data.site_section|string|The section of the site that the current page resides in. site\_section2 through site\_section5can also be used if the site has many sections.||||||||

## Attached Notes

<p>page_data.page_variant can be used to pass along whether the content is "gated" or "non-gated". site_section value should be comparable to the values in the top-level navigation.&nbsp;</p>
