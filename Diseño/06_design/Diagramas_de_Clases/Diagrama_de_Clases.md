![Diagrama_de_Clases](Diagrama_de_Clases.png)

<!--
@startuml Diagrama_de_Clases

interface IAdministración {
  +AñadirProfesor()
  +DarBajaProfesor()
  +ModificarProfesor()
  +AñadirAlumno()
  +DarBajaAlumno()
  +ModificarAlumno()
  +AñadirGrupo()
  +EliminarGrupo()
  +ModificarGrupo()
}

interface IProfesor {
  +RegistrarAsistencia()
  +ExpedirInformeMensual()
}

class Administración implements IAdministración {
}

class Profesor implements IProfesor {
  - String Nombre
  - int RFC
}

class Materia {
  -String Nombre
  -id: UUID
  -Alumno alumnos[1..]
}

class Asistencia {
  -fecha: Date
  -alumno: Alumno
  -Asistencia: Boolean
}

class Alumno {
  -id: UUID
  -nombre: String
  -tarjeta: Tarjeta
  -asistencias[]: Asistencia
}

class Tarjeta {
  -nfc: UUID
}

IProfesor *-- Asistencia
IAdministración ..|> IProfesor
IAdministración ..|> Materia
IProfesor ..|> Alumno
Materia --* Alumno
Alumno --o Asistencia
Alumno --o Tarjeta
Profesor <-- Materia

@enduml

-->
