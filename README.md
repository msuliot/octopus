## Octopus Overview

This document serves as the guide for the Models API. The API is designed as a RESTful interface, facilitating interactions with the various models hosted within the R&D API framework. As of now, a total of 16 models are accessible through this API.

## Authentication

Authentication is achieved through the use of an API key and a secret key. These keys are obtainable upon request. For access, please follow the designated process for submitting your request, which can be found at [specific instructions or contact information].

This revision aims to enhance clarity and ensure readers have a straightforward understanding of how to access and utilize the API effectively.

## API Endpoints

### 1. Get Model List

#### Description

This endpoint provides users with the ability to retrieve a `list` of all models currently available through the API. Upon calling this endpoint, you will receive a structured list detailing each model's unique identifiers and key characteristics, enabling you to identify and select models for your specific needs.

#### HTTP Method

`GET`

#### Endpoint

`/api/model/list`

#### Headers

- `api-key: <your_api_key>`
- `secret-key: <your_secret_key>`
- `content-type: application/json`

#### Request Body

For this GET request, no request body is required or processed. GET requests are designed to retrieve data from the server based on the specified endpoint and query parameters, if any, without the need for a request body. This simplifies the request process, focusing solely on the endpoint URL to access the available models in the API.

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

### 2. Model Prediction (prompt)

#### Description

This endpoint is designed for making predictions by interacting directly with the model. Users are required to submit a prompt or input data, which the model uses as the basis for its prediction. Upon receiving the prompt, the model processes the input and generates a response that constitutes the prediction. This process is key for applications involving natural language processing, image recognition, or other data analysis tasks where model-based insights are needed. The response format and the specificity of the prediction depend on the model's design and the nature of the prompt provided.

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

### 3. Model Costs

#### Description

This endpoint is designed to provide a detailed breakdown of `costs` associated with the use of each model, tailored to individual users. Upon request, users will receive information detailing the cost per model, along with any variations based on usage patterns or subscription levels. This cost analysis aims to offer transparency and help users in planning and budgeting their usage of the API services more effectively. It takes into account factors such as the number of requests made, the complexity of the models used, and any additional services or resources consumed during the prediction process.

#### HTTP Method

`GET`

#### Endpoint

`/api/model/costs`

#### Headers

- `api-key: <your_api_key>`
- `secret-key: <your_secret_key>`
- `content-type: application/json`

#### Request Body

For this GET request, no request body is required or processed. GET requests are designed to retrieve data from the server based on the specified endpoint and query parameters, if any, without the need for a request body. This simplifies the request process, focusing solely on the endpoint URL to access the available models in the API.

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
