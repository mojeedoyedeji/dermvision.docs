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


Get all patient record
~~~~~~~~~~~~~~~~~~~~~~

**Endpoint URL:** `/patient/`

**Method:** `GET`

**Description:**  Get all patient records

**Headers:**

.. code-block:: http

    Authorization: Bearer {token}
    Content-Type: application/json



**Body:**

.. code-block:: json

    {
        "derma": 123,
        "name": "John Doe",
        "email": "john.doe@example.com",
        "phone": "+966507133905"
        "dob": "08-Nov-1980" 
    }


**Response:**
- `200 OK`: A JSON object containing user data.
- `404 Not Found`: If the user does not exist.
- `401 Unauthorized`: If the authentication token is invalid or missing.

**Example Request:**

.. code-block:: javascript
    fetch('https://api.dermvision.com/patient/', {
        method: 'GET',
        headers: {
            'Authorization': 'Bearer YOUR_ACCESS_TOKEN',
            'Content-Type': 'application/json'
        }
    })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));

**Example Response:**

.. code-block:: json

    {
        
    }


