![Diagramas_de_Secuencia](DS-Cambio_Materia.png)﻿﻿

/'
@startuml
actor Usuario as Profesor
participant App
participant "Data Source" as DataSource
participant DAO as Dao
participant BD as BaseDatos

Profesor -> App: Solicita modificar atributos de una materia
activate App
App -> DataSource: Consulta información de materia a modificar
activate DataSource
DataSource -> Dao: Busca materia en la BD
activate Dao
Dao --> DataSource: Devuelve materia encontrada
deactivate Dao
DataSource --> App: Devuelve información de la materia a modificar
deactivate DataSource
App -> Profesor: Muestra información existente de la materia a modificar
Profesor -> App: Ingresa nueva información de la materia
App -> Dao: Actualiza información de la materia en BD
activate Dao
Dao -> BaseDatos: Actualiza datos de la materia
activate BaseDatos
BaseDatos --> Dao: Confirma actualización
deactivate BaseDatos
Dao --> App: Confirma actualización en la BD
deactivate Dao
App -> Profesor: Muestra mensaje de éxito de modificación de atributos
deactivate App
@enduml
'/
