## Octopus Overview

This is the documentation for the Models API. The API is a RESTful API that allows you to interact with the models available in the Octopus platform. We currently have 16 models available in the API. 

## Authentication

The API uses API key and secret key for authentication. You can get your API key and secret key by request only.

## API Endpoints

### 1. Get Model List

#### Description

This endpoint will allow you to get a `list` of models available in the API.

#### HTTP Method

`GET`

#### Endpoint

`/api/model/list`

#### Headers

- `api-key: <your_api_key>`
- `secret-key: <your_secret_key>`
- `content-type: application/json`

#### Request Body

No request body on get request

#### Python Example

```python
import requests

url = "https://octopus-app-2z7or.ondigitalocean.app/api/model/list"

payload = {}
headers = {
  'api-key': '<your_api_key>',
  'secret-key': '<your_secret_key>',
  'content-type': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```

---

### 2. Model Prediction (prompt)

#### Description

This is where you call the model, by providing the prompt and the model will return the prediction.

#### HTTP Method

`POST`

#### Endpoint

`/api/model`

#### Headers

- `api-key: <your_api_key>`
- `secret-key: <your_secret_key>`
- `content-type: application/json`

#### Request Body
```json
{
  "model_name": "<model_name>",
  "prompt": "<prompt>",
  "max_tokens": 250,
  "temperature": 0.5
}
```
`max_tokens`(int) and `temperature`(float) are optional.

#### Python Example

```python
import requests
import json

url = "https://octopus-app-2z7or.ondigitalocean.app/api/model"

payload = json.dumps({
  "model_name": "gpt-3.5-turbo",
  "prompt": "if I'm looking to start a diet, I heard the Mediterranean diet is good explain that to me",
  "max_tokens": 250, # optional
  "temperature": 0.5 # optional
})
headers = {
  'api-key': '<your_api_key>',
  'secret-key': '<your_secret_key>',
  'content-type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

---

### 3. Model Costs

#### Description

This will get you a breakdown of the cost per model and per user.

#### HTTP Method

`GET`

#### Endpoint

`/api/model/costs`

#### Headers

- `api-key: <your_api_key>`
- `secret-key: <your_secret_key>`
- `content-type: application/json`

#### Python Example

```python
import requests
import json

url = "https://octopus-app-2z7or.ondigitalocean.app/api/model/costs"

payload = {}
headers = {
  'api-key': '<your_api_key>',
  'secret-key': '<your_secret_key>',
  'content-type': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```

## IP Blocking and Rate Limiting

I will be adding rate limiting to the API soon. I will also be adding IP blocking to the API soon.

## Additional Information

Let me know if you think of any other things I should add or something doesn't make sense or if if you have any questions
