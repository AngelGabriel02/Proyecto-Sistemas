![Diagrama_deCasos_de_Uso](DCU-001_Profesor.png)

/'
@startuml Diagrama de Casos de Uso Profesor
left to right direction

actor "Profesor" as prf

usecase "Alta Materia" as CU004
usecase "Baja Materia" as CU005
usecase "Cambio Materia" as CU006

usecase "Alta Alumno" as CU007
usecase "Baja Alumno" as CU008
usecase "Cambio Alumno" as CU009

usecase "Leer NFC" as nfc


prf --> CU004
prf --> CU005
prf --> CU006
prf --> CU007
prf --> CU008
prf --> CU009

CU007 <--> nfc
CU009 <--> nfc

@enduml
'/
