# User Detected

### 

## Javascript Code
```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  "event": "detect_user",
  "detailed_event": "User Detected",
    "user_data": {
        "anonymous_user_id": "<anonymous_user_id>"
    }
});
```

## Variable Definitions

|Path|Type|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|user_data.anonymous_user_id|string|When a user is not logged in, this captures an anonymous user ID.||||||||

## Attached Notes

<p>Pass this event with a hashed value after the form submission is successful</p>
