---
title: Demo
description: Recipe Description
hidden: true
recipe:
  color: '#018FF4'
  icon: 🦉
---
```python Python
import requests

url = "https://www.google.com/account-access-consents"

payload = { "Data": { "Permissions": ["ReadAccountsBasic"] } }
headers = {
    "accept": "application/json; charset=utf-8",
    "content-type": "application/json"
}

response = requests.post(url, json=payload, headers=headers)

print(response.text)
```

```json Response Example
{"success":true}
```

# Setup imports

<!-- python@1 -->



# Set url

<!-- python@3 -->

