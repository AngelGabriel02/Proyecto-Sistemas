![Diagrama_deCasos_de_Uso](DCU-002_Alumno.png)﻿

/'
@startuml Diagrama de Caso de Uso Alumno

left to right direction

actor Profesor as prof
actor Alumno as alm

usecase "Registrar Asistencia" as CU010
usecase "Generar Informe" as CU011

alm --> CU010
prof --> CU010
prof --> CU011

@enduml
'/
