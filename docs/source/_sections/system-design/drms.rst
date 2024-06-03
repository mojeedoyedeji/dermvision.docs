Diagnostics Record Management System
---------------

.. _system-design-drms:

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
   "bleeding", "", "Varchar(15)", "Not Null"
   "elevation", "", "Varchar(100)", "Unique, Not Null"
   "changed", "", "Varchar(255)", "Not Null"
   "hurt", "", "Varchar(255)", "Not Null"
   "grew", "", "Text", "Nullable"
   "itchy", "", "Text", "Nullable"
   "region", "", "Text", "Nullable"
   "location", "", "Text", "Nullable"
   "tone", "", "Text", "Nullable"
   "symptoms", "", "Text", "Nullable"
   "cam", "", "Text", "Nullable"
   "prediction", "", "Text", "Nullable"
   "probabilities", "", "Text", "Nullable"
   "derma", "", "Text", "Nullable"
   "created", "", "Text", "Nullable"
   "modified", "", "Text", "Nullable"


**Relationships**

.. csv-table:: 
   :header: "Relationship", "Type", "Description", "Related Entity", "Foreign Key"
   :widths: 20, 20, 40, 20, 20

   "Patients", "One-to-Many", "A patient can have multiple diagnostic records", "Patients", "PatientID in the Appointment table references _id in the Patient table."
   "Derma", "One-to-Many", "A dermatologists can create multiple diagnostic records.", "Dermatologist", "DermatologistID in the Diagnostic table references _id in the Dermatologist table."
   

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

Get all diagnostic records
~~~~~~~~~~~~~~~~~~~~~~~~~~

**Endpoint URL:** `/diagnostic`

**Method:** `GET`

**Description:**  Get all diagnostic records

**Headers:**

.. code-block:: http

    Authorization: Bearer {token}
    Content-Type: application/json

**Response:**
- `200 OK`: A JSON object containing user data.
- `404 Not Found`: If the user does not exist.
- `401 Unauthorized`: If the authentication token is invalid or missing.

**Example Request:**

.. code-block:: javascript

    fetch('https://api.dermvision.com/diagnostic', {
        method: 'POST',
        headers: {
            'Authorization': 'Bearer YOUR_ACCESS_TOKEN',
            'Content-Type': 'application/json'
        }
    })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));


Perform a diagnosis
~~~~~~~~~~~~~~~~~~~

**Endpoint URL:** `/diagnostic/diagnose`

**Method:** `POST`

**Description:**  Perform a diagnosis using image and clinical data

**Headers:**

.. code-block:: http

    Authorization: Bearer {token}
    Content-Type: application/json

**Body:**

.. code-block:: json

    {
        "image": 123,
        "x": "John Doe",
        "y": "john.doe@example.com",
        "z": "+966507133905"
        "a": "08-Nov-1980" 
    }


**Response:**
- `200 OK`: A JSON object containing user data.
- `404 Not Found`: If the user does not exist.
- `401 Unauthorized`: If the authentication token is invalid or missing.

**Example Request:**

.. code-block:: javascript

    fetch('https://api.dermvision.com/diagnostic/diagnose', {
        method: 'POST',
        headers: {
            'Authorization': 'Bearer YOUR_ACCESS_TOKEN',
            'Content-Type': 'application/json'
        }
    })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
