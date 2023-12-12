![Diagramas_de_Secuencia](DS-Alta_Materia.png)﻿﻿

/'
@startuml
actor Usuario as Profesor
participant App
participant "Data Source" as DataSource
participant DAO as Dao
participant BD as BaseDatos

Profesor -> App: Solicita agregar materia
activate App
App -> DataSource: Consulta información de materia
activate DataSource
DataSource -> Dao: Busca materia en la BD
activate Dao
Dao --> DataSource: Devuelve materia encontrada
deactivate Dao
DataSource --> App: Devuelve información de la materia
deactivate DataSource
App -> Profesor: Muestra información existente de la materia
Profesor -> App: Ingresa nueva información de la materia
App -> Dao: Actualiza información de la materia en BD
activate Dao
Dao -> BaseDatos: Actualiza datos de la materia
activate BaseDatos
BaseDatos --> Dao: Confirma actualización
deactivate BaseDatos
Dao --> App: Confirma actualización en la BD
deactivate Dao
App -> Profesor: Muestra mensaje de éxito de registro de materia
deactivate App
@enduml
'/
