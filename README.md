# RESTful API Documentation

## Introduction

Welcome to the documentation for API collection. This document will guide you on how to interact with the API, including request formats, response formats, and status codes.

## Base URL

`https://api.example.com/v1`


## Endpoints

### 1. Endpoint Should Have

#### Description

[Description of what this endpoint does]

#### URL

The route of endpoint Like (/Tickets)

`/endpoint`

#### Methods

Every endpoint like (/Tickets) should has this methods

- [**GET**](#GET): Retrieve Data
- [**POST**](#POST): Create a new or update exist instance 
- [**DELETE**](#DELETE): Delete item 

#### Response Codes

- `200 OK`: Successful request
- `201 Created`: Resource created successfully
- `400 Bad Request`: Invalid request data
- `401 Unauthorized`: Token Expired 
- `403 forbidden`: Token Expired / User Unverified
- `404 Not Found`: Resource not found
- `422 Validation Error`: The server can't process your request, although it understands itResource not found
- `429 Too Many Requests`: User Send Many requests to server
- `500 Internal Server Error`: Server encountered an error


---
<a name="GET"></a>
**GET Request:**

This section provides examples of how will be GET request shape to the API, along with the necessary headers and request body (if applicable).

**Retrieve Data** 

 1. List items when you use 
  ```http
  GET /endpoint
  ```

 2. single item when you use 
  ```http
  GET /endpoint/${Id}

  ```
<a name="GET-Parameter"></a>
**Parameter Name**:
- Example: `status` (String) 
```http
GET /endpoint?status=${String}
```

**Response Body Exaples**: 
- Success Response :
   1. List items
    ```json
    {
      "data": [],
      "message": "Resources Retrieve successfully"
    }
    ```
  2. single item 
    ```json
    {
      "data": {},
      "message": "Resource Retrieve successfully"
    }
    ```


- Fail Response :
    ```json
    {
      "errors": [],
      "message": "Fail Reason"
    }
    ```

<a name="POST"></a>
**POST Request:**

This section provides examples of how will be POST request shape to the API, along with the necessary headers and request body (if applicable).

**Create Resource** 
  ```http

  POST /endpoint
  
  ```
and body will contain data of resource 

  ```json
  {
    "example_key": "example_value",
  }
  ```
**Update resource** 
  ```http
  POST /endpoint/${Id}

  ```
and body will contain data of resource that want to update
  ```json
  {
    "example_key": "example_value",
  }
  ```

**Response Body Exaples**: 
- Success Response :
  ```json
  {
    "data": {},
    "message": "The resource has been (created or updated) successfully"
  }
  ```

- Fail Response :
  ```json
  {
    "errors": [],
    "message": "Fail Reason"
  }
  ```

<a name="DELETE"></a>
**DELETE Request:**

This section provides examples of how will be DELETE request shape to the API.

_Note_: This Api must be used with a token or authorized user.

**Create Resource** 
  ```http

  DELETE /endpoint/${Id}
  
  ```

**Response Body Exaples**: 
- Success Response :
  ```json
  {
    "data": {},
    "message": "The resource has been Deleted successfully"
  }
  ```
- Fail Response :
  ```json
  {
    "errors": [],
    "message": "Fail Reason"
  }
  ```

## Localization

To support multiple languages, you can include the `Accept-Language` header in your requests. The API will respond with content in the requested language if available. If the requested language is not supported, the default language will be used.


**Request with Preferred Language:**
 To use it add key and value in header
```json
{
  "Accept-Language": "ar"
}
```


## Pagination

For endpoints that return a large set of results, you can paginate through the data using the `page` and `limit` parameters.

- `page`: The page number you want to retrieve (1-based index).
- `limit`: The number of items to return per page.

you can use it with [GET](#GET) request as [Parameter](#GET-Parameter) 
