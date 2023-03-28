# User Visit Started

### 

## Javascript Code
```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  "event": "custom_session_start",
  "detailed_event": "User Visit Started",
    "event_data": {
        "environment": "<environment>"
    }
});
```








