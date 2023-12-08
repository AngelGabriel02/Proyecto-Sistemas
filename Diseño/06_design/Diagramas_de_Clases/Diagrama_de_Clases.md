![Diagrama_de_Clases](Diagrama_de_Clases.png)

<!--
@startuml

interface iAsistencia {

  + obtenerFecha(): Date
  + establecerFecha(fecha: Date): void
  + obtenerHora(): Time
  + establecerHora(hora: Time): void
  + obtenerNFCAlumno(): String
  + establecerNFCAlumno(nfc: String): void

}

class asistencia {

  - fecha: Date
  - hora: Time
  - NFCAlumno: String
  + asistencia(fecha: Date, hora: Time, NFCAlumno: String)

}

iAsistencia <|.. asistencia

interface iAlumno {

  + obtenerNombre(): String
  + establecerNombre(nombre: String): void
  + obtenerNumeroDeCuenta(): String
  + establecerNumeroDeCuenta(numero: String): void
  + obtenerNFC(): String
  + establecerNFC(nfc: String): void

}

class alumno {

  - nombre: String
  - numeroDeCuenta: String
  - NFC: String
  + alumno(nombre: String, numeroDeCuenta: String, NFC: String)

}

iAlumno <|.. alumno

interface iMateria {

  + obtenerAlumnos(): iAlumno[]
  + agregarAlumno(alumno: iAlumno): void
  + eliminarAlumno(alumno: iAlumno): void
  + obtenerAsistencias(): iAsistencia[]
  + agregarAsistencia(asistencia: iAsistencia): void
  + eliminarAsistencia(asistencia: iAsistencia): void

}

class materia {

  - alumnos: iAlumno[]
  - asistencias: iAsistencia[]
  + materia(alumnos: iAlumno[], asistencias: iAsistencia[])

}
iMateria <|.. materia

class reporte {

  - asistencias: iAsistencia[]
  - materia: iMateria
  + reporte(asistencias: iAsistencia[], materia: iMateria)

}
interface iModelo {

  + obtenerMateria(): iMateria
  + establecerMateria(iMateria): void
  + altaAlumno(alumno): iAlumno
  + bajaAlumno(alumno): void
  + cambioAlumno(alumno): iAlumno
  + altaMateria(materia): iMateria
  + bajaMateria(materia): void
  + cambioMateria(materia): iMateria
  + altaAsistencia(asistencia): iAsistencia
  + bajaAsistencia(asistencia): void
  + cambioAsistencia(asistencia): iAsistencia
  + obtenerNombrePorNFC(NFC: String): String
  + generarReporte(materia): reporte

}

class modelo {

  - materia: iMateria
  + modelo(materia: iMateria)

}
iModelo <|.. modelo

interface iVista {

  + actualizar(): void

}

class vista {

  - modelo: iModelo
  - controlador: iControlador
  + vista(modelo: iModelo, controlador: iControlador)

}
iVista <|.. vista

interface iControlador {

  + manejarAltaAlumno(): void
  + manejarBajaAlumno(): void
  + manejarCambioAlumno(): void
  + manejarAltaMateria(): void
  + manejarBajaMateria(): void
  + manejarCambioMateria(): void
  + manejarAltaAsistencia(): void
  + manejarBajaAsistencia(): void
  + manejarCambioAsistencia(): void
  + manejarGenerarReporte(): void

}

class controlador {

  - modelo: iModelo
  - vista: iVista
  + controlador(modelo: iModelo, vista: iVista)

}
iControlador <|.. controlador

class lectorNFC {

  + leerTarjeta(): String

}

interface iDataStorage {

  + readAlumno(): alumno
  + writeAlumno(alumno)
  + readMateria(): materia
  + writeMateria(materia)
  + readAsistencia(): asistencia
  + writeAsistencia(asistencia)

}

class dataStorage {

}

iDataStorage <|.. dataStorage

iModelo "1" o-- "1" iControlador
iControlador "1" o-- "1" iVista
iVista "1" o-- "1" iModelo
iModelo "1" *-- "1" iMateria
iMateria "1" *-- "*" iAlumno
iMateria "1" *-- "*" iAsistencia
iControlador "1" o-- "1" iDataStorage
iControlador "1" o-- "1" lectorNFC
reporte "1" *-- "1" iMateria
reporte "1" *-- "*" iAsistencia

@enduml

-->
