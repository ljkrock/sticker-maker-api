---
title: Sticker-maker
description: Running sticker-maker workflow. Only pay for the GPU runtime, billed by the second.
---

# Demo
![login](https://img5.aitools99.net/2.png)|![login](https://img5.aitools99.net/4.png)|![login](https://img5.aitools99.net/7.png)
---|---|---

# Run time and cost

This model runs on 1001 GPU hardware. Predictions are typically completed within 16 seconds.

This model runs on 1002 GPU hardware. Predictions are typically completed within 18 seconds.
<br />
<br />
# Generate API 


## How to obtain an APIKey


Notice: When using the API, you must include the `apikey` in the request header.


1. Log in and navigate to the ApiKey management page.

![login](https://img5.aitools99.net/login.png)

2. Add an API key, then copy it into your code.

![login](https://img5.aitools99.net/addapikey.png)

## API Domain

api.aitools99.net

## HTTP Request

`POST /api/v1/generate`

## Headers

| Parameter Name | Required | Type   | Description                 |
|----------------|----------|--------|-----------------------------|
| Content-Type   | Yes      | String | Must be set to `application/json` |
| apikey         | Yes      | String | Used for authentication     |


## Request Body (Body)

The request body is in JSON format and includes the following parameters:

```json
    {
        "mid":3123,
        "input":{
            "seed":342383,  //Optional
            "steps": 20,
            "width": 1024,
            "height": 1024,
            "prompt": "cute cat",
            "upscale": false,
            "upscale_steps": 10,
            "negative_prompt": ""
        }
    }
```

### Request Parameters

| Parameter Name | Required | Type   | Description |
|----------------|----------|--------|-------------|
| mid            | Yes      | String | model id    |
| input          | Yes      | Object | input data  |

## Request Example

```http
POST /api/v1/generate HTTP/1.1
Host: api.aitools99.net
Content-Type: application/json
apikey:73cf14b2-97bc-48e4-8e68-c7e616a23f07

{
    "mid":3123,
    "input":{
        "seed":342383,
        "steps": 20,
        "width": 1024,
        "height": 1024,
        "prompt": "cute cat",
        "upscale": false,
        "upscale_steps": 10,
        "negative_prompt": ""
    }
}
```

## Response Parameters

| Parameter Name | Type   | Description     |
|----------------|--------|-----------------|
| message        | String | message         |
| data           | String | data containing tid |
| code           | number | code            |
| status_code    | String | status          |

## Response Example

```json
    {
        "message": "post success.",
        "data": {
            "tid": "207be346-9ed9-49af-9fb3-a1726f14de93"
        },
        "code": 20000,
        "status_code": "success"
    }
```


<br />
<br />
<br />

# Result API

## API Domain

api.aitools99.net

## HTTP Request

`GET /api/v1/result?tid=${tid}`

## Headers

| Parameter Name | Required | Type   | Description     |
|----------------|----------|--------|-----------------|
| apikey         | Yes      | String | Used for authentication |

## Request Body (Body)

null

### Request Parameters

| Parameter Name | Required | Type   | Description |
|----------------|----------|--------|-------------|
| tid            | Yes      | String | tid         |

## Request Example

```
https://api.aitools99.net/api/v1/result?tid=207be346-9ed9-49af-9fb3-a1726f14de93

```

## Response Parameters

| Parameter Name   | Type   | Description     |
|------------------|--------|-----------------|
| message          | String | message         |
| data             | Object | Returned result data |
| code             | number | code            |
| status_code      | String | status          |

## Response Example

```json
    {
        "message": "get success.",
        "data": {
            "tid": "207be346-9ed9-49af-9fb3-a172sh14de93",
            "input": {
                "prompt": "cute cat",
                "negative_prompt": "",
                "width": 1024,
                "height": 1024,
                "steps": 20,
                "upscale": false,
                "upscale_steps": 10
            },
            "output": [
                "https://img.aitools99.net/4089c55cd1544ebd9d5e7eff1e882717.png",
                "https://img.aitools99.net/9adde76cb70a24f2a48449d1a44f3070.png"
            ],
            "created_at": "2024-03-16T01:37:49.475Z",
            "started_at": "2024-03-16T01:37:50.262Z",
            "completed_at": "2024-03-16T01:38:09.220Z",
            "predict_time": 13,
            "total_time": 25
        },
        "code": 20000,
        "status_code": "success"
    }
```
<br />
<br />

# others

Uses:

ArtificialGuyBr’s awesome stickers lora: https://huggingface.co/artificialguybr/StickersRedmond

With the AlbedobaseXL model: https://civitai.com/models/140737/albedobase-xl

Using Dreamshaper 8 and 4xAnimeSharp upscale models


## notice
Non-commercial use only.

It uses the following weights which are non-commercial:

- BRIA AI RMBG