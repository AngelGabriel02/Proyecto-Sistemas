![Diagramas_de_Secuencia](DS-Baja_Alumno.png)﻿﻿

/'
@startuml
actor Usuario as Profesor
participant App
participant "Data Source" as DataSource
participant DAO as Dao
participant BD as BaseDatos

Profesor -> App: Solicita dar de baja a un alumno
activate App
App -> Profesor: Solicita datos del alumno a dar de baja
Profesor -> App: Ingresa datos del alumno a dar de baja
App -> DataSource: Consulta información del alumno a dar de baja
activate DataSource
DataSource -> Dao: Busca datos del alumno en la BD
activate Dao
Dao --> DataSource: Devuelve datos del alumno
deactivate Dao
DataSource --> App: Devuelve información del alumno
deactivate DataSource
App -> Profesor: Muestra datos del alumno para confirmación de baja
Profesor -> App: Confirma dar de baja al alumno
App -> Dao: Elimina datos del alumno de la BD
activate Dao
Dao -> BaseDatos: Elimina datos del alumno
activate BaseDatos
BaseDatos --> Dao: Confirma eliminación de datos
deactivate BaseDatos
Dao --> App: Confirma eliminación en la BD
deactivate Dao
App -> Profesor: Muestra mensaje de éxito de baja de alumno
deactivate App
@enduml
'/
