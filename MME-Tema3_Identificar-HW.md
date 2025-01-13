# TEMA 3. MME. SMR. IDENTIFICAR HARDWARE

## Práctica: Identificando el Hardware de un Ordenador

### Objetivo:
Aprender a identificar y analizar los componentes de hardware de un ordenador utilizando
herramientas y métodos accesibles sin requerir permisos de administrador.
Duración: 2 horas

### Materiales:
 Acceso a internet
 Herramientas de software: CPU-Z, o comandos nativos del sistema operativo.


## Parte 1: Métodos basados en software

1.1. Uso de herramientas integradas del sistema operativo

### Windows

1. Información del sistema:
o Presiona Win + R, escribe msinfo32 y presiona Enter.
o Explora: Procesador, RAM instalada, modelo de la placa base.
o Anota: Las especificaciones encontradas en tu cuaderno.

2. Administrador de tareas:
o Presiona Ctrl + Shift + Esc para abrir el Administrador de tareas.
o Ve a la pestaña "Rendimiento".
o Tarea: Identifica y anota los núcleos del CPU, la velocidad de la RAM y el uso del
disco.

### GNU/Linux

1. Comandos básicos (sin sudo):

o lscpu: Información sobre el procesador.
o lsblk: Lista de dispositivos de almacenamiento.
o free -h: Memoria RAM instalada y disponible.

o Tarea: Anota las especificaciones clave del CPU, RAM y disco.

2. Monitor del sistema:
o Usa una aplicación como Gnome System Monitor o KDE System Monitor.
o Explora: Uso de CPU, memoria y almacenamiento.

## TEMA 3. MME. SMR. IDENTIFICAR HARDWARE

1.2. Consultar información detallada con PowerShell
1. Abrir PowerShell:
o Presiona Win + S, escribe "PowerShell" y selecciona el programa.
2. Comandos útiles para investigar la placa base y componentes:
o Placa base (Fabricante y modelo):
Escribe el código
Get-WmiObject Win32_BaseBoard | Select-Object Manufacturer, Product
Tarea: Identifica y anota el fabricante y el modelo de la placa base.
o Procesador:
Get-WmiObject Win32_Processor | Select-Object Name, NumberOfCores, MaxClockSpeed
Tarea: Especifica el modelo del CPU, número de núcleos y velocidad
máxima.
o Memoria RAM instalada:
Get-WmiObject Win32_PhysicalMemory | Select-Object Manufacturer, Capacity, Speed
Tarea: Identifica el fabricante, la capacidad total de la RAM (en bytes) y la
velocidad.
o Almacenamiento:
Get-WmiObject Win32_DiskDrive | Select-Object Model, Size
Tarea: Anota el modelo del disco (HDD o SSD) y su capacidad.
o Sistema operativo:
Get-ComputerInfo | Select-Object CsName, WindowsVersion, OsArchitecture
