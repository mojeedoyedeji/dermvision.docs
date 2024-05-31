Diagnostic Model Management System
---------------


This documentation outlines the entity relationship (ER) model for the Patient Record Management System within DermVision. 
The ER model defines the structure of the data and the relationships between various entities involved in managing patient records. 
Below is a detailed description of one of the key tables in the system: the **Patient** table.


Patient Entity
^^^^^^^^^^^^^^
The **Patient** entity stores essential information about patients. This table is central to the Patient Record Management System, 
as it contains the primary data necessary for identifying and managing patient records.

**Attributes**

.. csv-table:: 
   :header: "Attribute", "Description", "Data Type", "Constraints"
   :widths: 20, 40, 20, 20

   "_id", "A unique identifier for each patient.", "Integer", "Primary Key, Auto-increment, Not Null"
   "name", "The full name of the patient.", "Varchar(50)", "Not Null"
   "email", "The email address of the patient", "Varchar(50)", "Not Null"
   "phone", "The phone number of the patient", "Date", "Not Null"
   "nationality", "The nationality of the patient", "Varchar(10)", "Not Null"
   "gender", "The gender of the patient", "Varchar(15)", "Not Null"
   "dob", "The date of birth of the patient", "Varchar(100)", "Unique, Not Null"
   "derma", "The id of the dermatologist that created the patient record", "Varchar(255)", "Not Null"
   "created", "The date the record was created", "Varchar(255)", "Not Null"
   "updated", "The date the record was updated", "Text", "Nullable"


**Relationships**

.. csv-table:: 
   :header: "Relationship", "Type", "Description", "Related Entity", "Foreign Key"
   :widths: 20, 20, 40, 20, 20

   "Appointments", "One-to-Many", "A patient can have multiple appointments.", "Appointment", "PatientID in the Appointment table references PatientID in the Patient table."
   "Diagnostics", "One-to-Many", "A patient can have multiple diagnostic records.", "Diagnostic", "PatientID in the Diagnostic table references PatientID in the Patient table."
   "ClinicalNotes", "One-to-Many", "A patient can have multiple clinical notes.", "ClinicalNote", "PatientID in the ClinicalNote table references PatientID in the Patient table."
   "Prescriptions", "One-to-Many", "A patient can have multiple prescriptions.", "Prescription", "PatientID in the Prescription table references PatientID in the Patient table."
   "Derma", "Many-to-One", "A dermatolgist can have multiple patients", "Prescription", "PatientID in the Prescription table references PatientID in the Patient table."

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

Error Responses
^^^^^^^^^^^^^^^

**404 Not Found:**

.. code-block:: json

    {
        "error": "User not found"
    }

**401 Unauthorized:**

.. code-block:: json

    {
        "error": "Invalid or missing token"
    }