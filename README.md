# wk-8-Clinic-Booking-System2

## ERD @startuml
' Define entities with their attributes

entity "Patients" as Patients {
  * patient_id : INT <<PK>>
  --
  first_name : VARCHAR
  last_name : VARCHAR
  date_of_birth : DATE
  phone : VARCHAR
}

entity "Doctors" as Doctors {
  * doctor_id : INT <<PK>>
  --
  first_name : VARCHAR
  last_name : VARCHAR
  specialization : VARCHAR
}

entity "Services" as Services {
  * service_id : INT <<PK>>
  --
  service_name : VARCHAR
}

entity "Appointments" as Appointments {
  * appointment_id : INT <<PK>>
  --
  patient_id : INT <<FK>>
  doctor_id : INT <<FK>>
  appointment_date : DATETIME
  service_id : INT <<FK>>
}

entity "Payments" as Payments {
  * appointment_id : INT <<PK>> <<FK>>
  --
  amount : DECIMAL
  payment_date : DATE
}

entity "Doctor_Services" as DoctorServices {
  * doctor_id : INT <<FK>>
  * service_id : INT <<FK>>
}

' Relationships

Patients ||--o{ Appointments : "has"
Doctors ||--o{ Appointments : "has"
Appointments ||--|| Payments : "has"
Doctors ||--o{ DoctorServices : ""
Services ||--o{ DoctorServices : ""
Services ||--o{ Appointments : "used in"
@enduml


 
