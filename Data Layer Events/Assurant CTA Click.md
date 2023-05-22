# Assurant CTA Click

### 

## Javascript Code
```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  "event": "cta_click",
  "detailed_event": "Assurant CTA Click",
    "event_data": {
        "link_id": "<link_id>",
        "link_text": "<link_text>",
        "link_url": "<link_url>"
    }
});
```

## Variable Definitions

|Path|Type|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|event_data.link_id|string|Link identifier|MiddleSection\_C123\_Col00|||||||
|event_data.link_text|string|Readable text on button or link|Get in Touch|||||||
|event_data.link_url|string|Full path of the click URL||||||||




