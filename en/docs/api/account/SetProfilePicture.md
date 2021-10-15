# SetProfilePicture

The method is aimed for setting an account picture.

## Request {#request}

To set an account picture, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/setProfilePicture/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`file` | **file** | Yes | Sent file in *.jpg 

### Request body example {#request-example-body}

Python request example

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setProfilePicture/{{apiTokenInstance}}"

payload={}
files=[
  ('file',('{{file}}.jpeg',open('/C:/{{file}}.jpeg','rb'),'image/jpeg'))
]
headers = {}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | ----- 
`setProfilePicture` | **boolean** | Picture setting result flag 
`urlAvatar` | **string** | Set picture url  
`reason` | **string** | Reason why the picture hasn't been set  

### Response body example {#response-example-body}

If successful, in response to the request, a JSON string of the below form with HTTP status 200 is returned: 

```json
{
    "setProfilePicture": true,
    "urlAvatar": "https://pps.whatsapp.net/v/t61.24******-24/23**********_********23704_************77468_n.jpg?ccb=11-4&oh=**********b6ccc377d6332abad7d0bb&oe=********"
}
```

### SetProfilePicture errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section
