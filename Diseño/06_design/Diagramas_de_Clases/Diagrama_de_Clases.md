![Diagrama_de_Clases](Diagrama_de_Clases.png)

<!--

@startuml Diagrama_de_Clases

interface IAsistencia {

  + obtenerFechaAsistencia(): Date
  + establecerFechaAsistencia(fecha: Date): void
  + obtenerHoraAsistencia(): Time
  + establecerHoraAsistencia(hora: Time): void
  + obtenerNfcAlumnoAsistencia(): String
  + establecerNfcAlumnoAsistencia(nfc: String): void

}
class Asistencia {

  - fecha: Date
  - hora: Time
  - nfcAlumno: String
  + Asistencia(fecha: Date, hora: Time, nfcAlumno: String)

}

IAsistencia <|.. Asistencia

interface IAlumno {

  + obtenerNombreAlumno(): String
  + establecerNombreAlumno(nombre: String): void
  + obtenerNumeroDeCuentaAlumno(): String
  + establecerNumeroDeCuentaAlumno(numero: String): void
  + obtenerNfcAlumno(): String
  + establecerNfcAlumno(nfc: String): void

}

class Alumno {

  - nombre: String
  - numeroDeCuenta: String
  - nfc: String
  + Alumno(nombre: String, numeroDeCuenta: String, nfc: String)

}

IAlumno <|.. Alumno

interface IMateria {

  + obtenerNombreMateria(): String
  + obtenerAlumnosMateria(): IAlumno[]
  + agregarAlumnoMateria(alumno: IAlumno): void
  + eliminarAlumnoMateria(alumno: IAlumno): void
  + obtenerAsistenciasMateria(): IAsistencia[]
  + agregarAsistenciaMateria(asistencia: IAsistencia): void
  + eliminarAsistenciaMateria(asistencia: IAsistencia): void

}

class Materia {

  - nombreDeMateria: String
  - alumnos: IAlumno[]
  - asistencias: IAsistencia[]
  + Materia(alumnos: IAlumno[], asistencias: IAsistencia[])

}

IMateria <|.. Materia

class Reporte {

  - asistencias: IAsistencia[]
  - materia: IMateria
  + Reporte(asistencias: IAsistencia[], materia: IMateria)

}

interface IAlumnoModelo {

  + altaAlumnoModelo(alumno): void
  + bajaAlumnoModelo(alumno): void
  + cambioAlumnoModelo(alumno): IAlumno

}

interface IMateriaModelo {

  + obtenerMateriaModelo(): IMateria
  + establecerMateriaModelo(IMateria): void
  + altaMateriaModelo(materia): void
  + bajaMateriaModelo(materia): void
  + cambioMateriaModelo(materia): IMateria

}

interface IAsistenciaModelo {

  + altaAsistenciaModelo(asistencia): void
  + bajaAsistenciaModelo(asistencia): void
  + cambioAsistenciaModelo(asistencia): IAsistencia
  + generarReporteModelo(materia): Reporte

}

class Modelo {

  - materia: IMateria
  + Modelo(materia: IMateria)

}

IAlumnoModelo <|.. Modelo
IMateriaModelo <|.. Modelo
IAsistenciaModelo <|.. Modelo

interface IVista {

  + actualizarVista(): void

}

class Vista {

  - modelo: Modelo
  - controlador: IControlador
  + Vista(modelo: Modelo, controlador: IControlador)

}

IVista <|.. Vista

interface IAlumnoControlador {

  + manejarAltaAlumnoControlador(): void
  + manejarBajaAlumnoControlador(): void
  + manejarCambioAlumnoControlador(): void

}

interface IMateriaControlador {

  + manejarAltaMateriaControlador(): void
  + manejarBajaMateriaControlador(): void
  + manejarCambioMateriaControlador(): void

}

interface IAsistenciaControlador {

  + manejarAltaAsistenciaControlador(): void
  + manejarBajaAsistenciaControlador(): void
  + manejarCambioAsistenciaControlador(): void
  + manejarGenerarReporteControlador(): void

}

class Controlador {

  - modelo: Modelo
  - vista: IVista
  + Controlador(modelo: Modelo, vista: IVista)

}

IAlumnoControlador <|.. Controlador
IMateriaControlador <|.. Controlador
IAsistenciaControlador <|.. Controlador

class LectorNfc {

  + registrarTarjerta(): String
  + actualizarTarjeta(): String

}

interface IAlumnoDao {

  + readAlumno(): Alumno
  + writeAlumno(alumno)

}
interface IMateriaDao {

  + readMateria(): Materia
  + writeMateria(materia)

}

interface IAsistenciaDao {

  + readAsistencia(): Asistencia
  + writeAsistencia(asistencia)

}

class DataStorage {}
IAlumnoDao <|.. DataStorage
IMateriaDao <|.. DataStorage
IAsistenciaDao <|.. DataStorage
Modelo "1" o-- "1" Controlador
IVista "1" o-- "1" Controlador
IVista "1" o-- "1" Modelo
Modelo "1" *-- "1" IMateria
IMateria "1" *-- "*" IAlumno
IMateria "1" *-- "*" IAsistencia
Controlador "1" o-- "1" DataStorage
Controlador "1" o-- "1" LectorNfc
Reporte "1" *-- "1" IMateria
Reporte "1" *-- "*" IAsistencia

@enduml

-->