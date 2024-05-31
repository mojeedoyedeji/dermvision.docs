Appointment Record Management System
---------------

This section outlines the entity relationship (ER) model for the Appointment Record Management System within DermVision. 
The ER model defines the structure of the data and the relationships between various entities involved in managing appointment records. 
Below is a detailed description of one of the key tables in the system: the **Appointment** table.


Appointment Entity
^^^^^^^^^^^^^^
The **Appointment** entity stores essential information about patients. 
This table is central to the Appointment Record Management System, as it contains the primary data necessary for identifying and managing appointment records.

**Attributes**

.. csv-table:: 
   :header: "Attribute", "Description", "Data Type", "Constraints"
   :widths: 20, 40, 20, 20

   "_id", "A unique identifier for each patient.", "Integer", "Primary Key, Auto-increment, Not Null"
   "patient", "The first name of the patient.", "Varchar(50)", "Not Null"
   "derma", "The last name of the patient.", "Varchar(50)", "Not Null"
   "title", "The date of birth of the patient.", "Date", "Not Null"
   "notes", "The gender of the patient.", "Varchar(10)", "Not Null"
   "from", "The contact number of the patient.", "Varchar(15)", "Not Null"
   "to", "The email address of the patient.", "Varchar(100)", "Unique, Not Null"
   "created", "The residential address of the patient.", "Varchar(255)", "Not Null"
   "modified", "The emergency contact details for the patient.", "Varchar(255)", "Not Null"
   "status", "A summary of the patient's medical history.", "Text", "Nullable"


**Relationships**

.. csv-table:: 
   :header: "Relationship", "Type", "Description", "Related Entity", "Foreign Key"
   :widths: 20, 20, 40, 20, 20

   "Patients", "One-to-Many", "A patient can have multiple appointment records", "Patients", "PatientID in the Appointment table references _id in the Patient table."
   "Derma", "One-to-Many", "A dermatologists can create multiple appointment records.", "Dermatologist", "DermatologistID in the Diagnostic table references _id in the Dermatologist table."
   


API
^^^
.. uml::

      @startuml
      
      'style options 
      skinparam monochrome true
      skinparam circledCharacterRadius 0
      skinparam circledCharacterFontSize 0
      skinparam classAttributeIconSize 0
      hide empty members
      
      Class01 <|-- Class02
      Class03 *-- Class04
      Class05 o-- Class06
      Class07 .. Class08
      Class09 -- Class10
      
      @enduml

**URL:** `/api/user/{id}`

**Method:** `GET`

**Headers:**
- `Authorization`: `Bearer <token>`
- `Content-Type`: `application/json`

**Parameters:**

- `id` (path parameter): The unique identifier of the user.

**Response:**
- `200 OK`: A JSON object containing user data.
- `404 Not Found`: If the user does not exist.
- `401 Unauthorized`: If the authentication token is invalid or missing.

**Example Request:**

.. code-block:: javascript

    fetch('https://api.example.com/api/user/123', {
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
        "id": 123,
        "name": "John Doe",
        "email": "john.doe@example.com",
        "created_at": "2023-05-28T12:34:56Z"
    }

