Diagnostics Record Management System
---------------

This documentation outlines the entity relationship (ER) model for the Diagnostic Record Management System within DermVision. 
The ER model defines the structure of the data and the relationships between various entities involved in managing diagnostic records. 
Below is a detailed description of one of the key tables in the system: the **Diagnostic** table.


Diagnostic Entity
^^^^^^^^^^^^^^^^^
The **Diagnostic** entity stores essential information about the diagnosis for each patient. 
This table is central to the Diagnostic Record Management System,  as it contains the primary data necessary 
for identifying and managing patient records.

**Attributes**

.. csv-table:: 
   :header: "Attribute", "Description", "Data Type", "Constraints"
   :widths: 20, 40, 20, 20

   "_id", "A unique identifier for each patient.", "Integer", "Primary Key, Auto-increment, Not Null"
   "image", "The first name of the patient.", "Varchar(50)", "Not Null"
   "patient", "The last name of the patient.", "Varchar(50)", "Not Null"
   "age", "The date of birth of the patient.", "Date", "Not Null"
   "gender", "The gender of the patient.", "Varchar(10)", "Not Null"
   "bleeding", "The contact number of the patient.", "Varchar(15)", "Not Null"
   "elevation", "The email address of the patient.", "Varchar(100)", "Unique, Not Null"
   "changed", "The residential address of the patient.", "Varchar(255)", "Not Null"
   "hurt", "The emergency contact details for the patient.", "Varchar(255)", "Not Null"
   "grew", "A summary of the patient's medical history.", "Text", "Nullable"
   "itchy", "A summary of the patient's medical history.", "Text", "Nullable"
   "region", "A summary of the patient's medical history.", "Text", "Nullable"
   "location", "A summary of the patient's medical history.", "Text", "Nullable"
   "tone", "A summary of the patient's medical history.", "Text", "Nullable"
   "symptoms", "A summary of the patient's medical history.", "Text", "Nullable"
   "cam", "A summary of the patient's medical history.", "Text", "Nullable"
   "prediction", "A summary of the patient's medical history.", "Text", "Nullable"
   "probabilities", "A summary of the patient's medical history.", "Text", "Nullable"
   "derma", "A summary of the patient's medical history.", "Text", "Nullable"
   "created", "A summary of the patient's medical history.", "Text", "Nullable"
   "modified", "A summary of the patient's medical history.", "Text", "Nullable"


**Relationships**

.. csv-table:: 
   :header: "Relationship", "Type", "Description", "Related Entity", "Foreign Key"
   :widths: 20, 20, 40, 20, 20

   "Patients", "One-to-Many", "A patient can have multiple diagnostic records", "Appointment", "PatientID in the Appointment table references PatientID in the Patient table."
   "Derma", "One-to-Many", "A dermatologists can create multiple diagnostic records.", "Diagnostic", "PatientID in the Diagnostic table references PatientID in the Patient table."
   
   
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