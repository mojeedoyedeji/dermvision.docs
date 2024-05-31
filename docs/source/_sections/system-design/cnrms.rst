Clinical Notes Record Management System
---------------

This documentation outlines the entity relationship (ER) model for the Clinical Notes Record Management System within DermVision. 
The ER model defines the structure of the data and the relationships between various entities involved in managing clinical notes records. 
Below is a detailed description of one of the key tables in the system: the **Clinical Notes** table.


Clinical Note Entity
^^^^^^^^^^^^^^^^^^^^
The **ClinicalNote** entity stores information about clinical notes recorded by healthcare providers. 
This table is essential for managing and tracking clinical notes related to patients.

**Attributes**

.. csv-table:: 
   :header: "Attribute", "Description", "Data Type", "Constraints"
   :widths: 20, 40, 20, 20

   "_id", "A unique identifier for each clinical note.", "Integer", "Primary Key, Auto-increment, Not Null"
   "title", "The ID of the patient associated with the note.", "Integer", "Foreign Key, Not Null"
   "note", "The date of the clinical note.", "Date", "Not Null"
   "derma", "The content of the clinical note.", "Text", "Not Null"
   "patient", "The ID of the healthcare provider.", "Integer", "Not Null"
   "created", "The ID of the healthcare provider.", "Integer", "Not Null"
   "modified", "The ID of the healthcare provider.", "Integer", "Not Null"
   "deleted", "The ID of the healthcare provider.", "Integer", "Not Null"


**Relationships**

.. csv-table:: 
   :header: "Relationship", "Type", "Description", "Related Entity", "Foreign Key"
   :widths: 20, 20, 40, 20, 20

   "Patients", "Many-to-One", "Multiple clinical notes can belong to one patient.", "Patient", "PatientID in the ClinicalNote table references PatientID in the Patient table."


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

