Appointment Records Management System
-------------------------------------


This documentation outlines the entity relationship (ER) model for the Appointment Record Management System within DermVision. 
The ER model defines the structure of the data and the relationships between various entities involved in managing appointment records. 
Below is a detailed description of one of the key tables in the system: the **Appointment** table.


Appointment Entity
^^^^^^^^^^^^^^^^^^
The **Appointment** entity stores essential information about patients. This table is central to the Appointment Record Management System, 
as it contains the primary data necessary for identifying and managing patient records.

**Attributes**

.. csv-table:: 
   :header: "Attribute", "Description", "Data Type", "Constraints"
   :widths: 20, 40, 20, 20

   "_id", "A unique identifier for each patient.", "Integer", "Primary Key, Auto-increment, Not Null"
   "derma", "The id of the dermatologist that created the patient record", "Varchar(255)", "Not Null"
   "patient", "", "", "Not Null"
   "title", "", "", "Not Null"
   "notes", "", "", "Not Null"
   "date", "", "", "Not Null"
   "from", "", "", "Not Null"
   "to", "", "", "Not Null"
   "created", "The date the record was created", "DateTime", "Not Null"
   "modified", "The date the record was updated", "DateTime", "Not Null"
   "status", "", "", ""


**Relationships**

.. csv-table:: 
   :header: "Relationship", "Type", "Description", "Related Entity", "Foreign Key"
   :widths: 20, 20, 40, 20, 20

   "Appointments", "One-to-Many", "A patient can have multiple appointments.", "Appointment", "PatientID in the Appointment table references PatientID in the Patient table."
   "Diagnostics", "One-to-Many", "A patient can have multiple diagnostic records.", "Diagnostic", "PatientID in the Diagnostic table references PatientID in the Patient table."
   "ClinicalNotes", "One-to-Many", "A patient can have multiple clinical notes.", "ClinicalNote", "PatientID in the ClinicalNote table references PatientID in the Patient table."
   "Prescriptions", "One-to-Many", "A patient can have multiple prescriptions.", "Prescription", "PatientID in the Prescription table references PatientID in the Patient table."
   "Derma", "Many-to-One", "A dermatolgist can have multiple patients", "Prescription", "PatientID in the Prescription table references PatientID in the Patient table."


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

      
API
^^^

