Developer API
=============

Welcome to the DermVision API documentation. DermVision provides advanced AI-powered diagnostic tools for dermatological analysis. 
This API allows developers to seamlessly integrate DermVision's diagnostic capabilities into their applications. With endpoints for image uploads, 
diagnostic result retrieval, and image management, the DermVision API is designed to be easy to use while providing robust and accurate diagnostic insights. 
By leveraging this API, developers can enhance their applications with cutting-edge dermatological analysis, enabling early detection and better management of 
skin conditions. Whether you are building mobile apps, web services, or integrating with electronic health records, 
the DermVision API offers a comprehensive solution for AI-based skin diagnostics.

Base URL: https://api.dermvision.com

Endpoints
---------

Upload Image
~~~~~~~~~~~~
- **Endpoint:** `POST /v1/images`
- **Description:** Uploads an image for diagnostic processing.
- **Request:**
  - **Headers:**
    - `Content-Type: multipart/form-data`
  - **Body:**
    - `image` (file): The image file to be diagnosed.
- **Response:**
  - `201 Created`
  - **Body:**
    ::
    
      {
        "image_id": "string",
        "status": "uploaded",
        "diagnosis_url": "https://api.dermvision.com/v1/images/{image_id}/diagnosis"
      }

Get Diagnostic Result
~~~~~~~~~~~~~~~~~~~~~
- **Endpoint:** `GET /v1/images/{image_id}/diagnosis`
- **Description:** Retrieves the diagnostic result for a previously uploaded image.
- **Request:**
  - **Headers:**
    - `Accept: application/json`
  - **Parameters:**
    - `image_id` (string): The ID of the image.
- **Response:**
  - `200 OK`
  - **Body:**
    ::
    
      {
        "image_id": "string",
        "diagnosis": {
          "condition": "string",
          "confidence": "float",
          "recommendation": "string"
        },
        "status": "diagnosed"
      }

List All Images
~~~~~~~~~~~~~~~
- **Endpoint:** `GET /v1/images`
- **Description:** Lists all uploaded images with their statuses.
- **Request:**
  - **Headers:**
    - `Accept: application/json`
- **Response:**
  - `200 OK`
  - **Body:**
    ::
    
      {
        "images": [
          {
            "image_id": "string",
            "status": "uploaded | processing | diagnosed"
          }
        ]
      }

Delete Image
~~~~~~~~~~~~
- **Endpoint:** `DELETE /v1/images/{image_id}`
- **Description:** Deletes an uploaded image.
- **Request:**
  - **Headers:**
    - `Accept: application/json`
  - **Parameters:**
    - `image_id` (string): The ID of the image.
- **Response:**
  - `204 No Content`

Example Usage
-------------

Upload Image
~~~~~~~~~~~~
.. code-block:: bash

  curl -X POST https://api.dermvision.com/v1/images \\
    -H "Content-Type: multipart/form-data" \\
    -F "image=@/path/to/skin_image.jpg"

Get Diagnostic Result
~~~~~~~~~~~~~~~~~~~~~
.. code-block:: bash

  curl -X GET https://api.dermvision.com/v1/images/{image_id}/diagnosis \\
    -H "Accept: application/json"

List All Images
~~~~~~~~~~~~~~~
.. code-block:: bash

  curl -X GET https://api.dermvision.com/v1/images \\
    -H "Accept: application/json"

Delete Image
~~~~~~~~~~~~
.. code-block:: bash

  curl -X DELETE https://api.dermvision.com/v1/images/{image_id} \\
    -H "Accept: application/json"

Error Handling
--------------

All endpoints should provide appropriate HTTP status codes and error messages. Example:

- **400 Bad Request:** Invalid request parameters.
- **401 Unauthorized:** Authentication failed.
- **404 Not Found:** Image not found.
- **500 Internal Server Error:** Server encountered an error.

Authentication
--------------

For security, the API should use authentication mechanisms such as API keys, OAuth tokens, or JWT. Example:

- **Header:** `Authorization: Bearer {token}`

Rate Limiting
-------------

To prevent abuse, implement rate limiting. Example:

- **X-RateLimit-Limit:** The number of allowed requests in the current period.
- **X-RateLimit-Remaining:** The number of remaining requests in the current period.
- **X-RateLimit-Reset:** The time at which the rate limit resets.