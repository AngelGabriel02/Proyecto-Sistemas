![Diagrama_deCasos_de_Uso](DCU-002_Alumno.png)﻿

/'
@startuml Diagrama de Caso de Uso Alumno
left to right direction

actor Profesor as prof
actor Alumno as alm

usecase "Registrar Asistencia" as CU010
usecase "Generar Informe" as CU011
usecase "Válidar NFC" as CU012
usecase "Leer NFC" as CU013

CU013 <--> CU012
CU010 --> CU013

alm --> CU010
prof --> CU010
prof --> CU011

@enduml
'/
