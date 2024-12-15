
# MME - Tema 4: El Microprocesador

partimos del PDF oficial - a complementar con 

MME_Tema4_El_Microprocesador-y-el-Kernel-Linux-I.md

págs. 1 a 32 del programa en PDF 

MME_Tema4_El_Microprocesador-y-el-Kernel-Linux-II.md

págs. 32 a 80 del programa en PDF 

MME_Tema4_El_Microprocesador-y-el-Kernel-Linux-III.md

págs. 80 a 122 del programa en PDF 


## CPU: Características

### Frecuencia de Reloj
- Velocidad del procesador: frecuencia a la que los transistores conmutan.
- **Frecuencia de reloj** no equivale a operaciones por segundo (instrucciones).
- **Medida en hercios (Hz)**.

#### Tipos de Velocidades
1. **Velocidad interna**: la velocidad de operación interna del microprocesador. Ejemplo: 4.40 GHz.
2. **Velocidad externa o del bus del sistema**: velocidad de comunicación con la placa base. Ejemplo: 3.2 GHz.

#### Consideraciones
- Incrementar la frecuencia aumenta el calor.
- **Límite físico** encontrado alrededor de los 5 GHz, lo que obligó a cambiar hacia estrategias multiprocesador.

### Turbo Boost y Precisión Boost
- Mejoran el rendimiento del núcleo aumentando potencia, temperatura y consumo de energía.

---

## Microprocesador: Núcleos

### Qué es un Núcleo
- Subconjunto electrónico de la unidad central encargado de ejecutar instrucciones.
- **Funciones:** resolver operaciones aritméticas y lógicas.
- Formado por millones de transistores.

### Estructura Interna
- **Cache L1**: memoria próxima al núcleo.
- **Cache L2 y L3**: mayor capacidad pero menor velocidad.
- **Unidad de control y ALU**.

---

## Multi-Núcleo y Multi-Hilo

### Estrategias de Paralelización
- **Multi-núcleo**: permite ejecutar procesos en paralelo.
- **Hilos (Threads):** dividen las tareas en subprocesos ejecutados cuando los núcleos están libres.

#### Tecnologías Relacionadas
1. **Hyper-Threading (Intel):** permite ejecutar más de un hilo por núcleo.
2. **Thread Director (Intel):** gestión entre núcleos eficientes y de alto rendimiento.

---

## Chiplets

### Definición
- Subdivisión de un microprocesador en partes independientes que trabajan conjuntamente.
- Ventajas:
  - Diseño escalable y modular.
  - Mayor rendimiento y eficiencia de fabricación.

---

## Memoria Caché

### Definición
- Memoria de acceso directo donde se almacenan datos e instrucciones frecuentes.
- Tipos de memoria:
  - **L1**: más cercana al núcleo, hasta 1 MB.
  - **L2**: intermedia, hasta 18 MB.
  - **L3**: compartida entre varios núcleos, hasta 64 MB.

### Características
- Memoria **SRAM**.
- Velocidades de hasta 200 GB/s.

---

## Controlador de Memoria Principal

### Qué es
- Circuito digital integrado en la CPU para gestionar el flujo de datos entre la memoria y el procesador.

### Canales
1. **Single Channel**: un único bus de 64 bits.
2. **Dual Channel**: dos buses, doble ancho de banda.
3. **Triple y Quad Channel**: incrementan ancho de banda y reducen latencia.

---

## Juego de Instrucciones

### Tipos
1. **CISC (Complex Instruction Set Computer):**
   - Amplio conjunto de instrucciones.
   - Ejemplo: Intel 286, 386, Pentium.
   - Ventajas: reduce costos de software y facilita la depuración.
2. **RISC (Reduced Instruction Set Computer):**
   - Instrucciones simples y optimizadas.
   - Ejemplo: arquitecturas ARM.
   - Ventajas: eficiencia energética y menor consumo de calor.

---

## Virtualización

### Qué es
- División de recursos de hardware para ejecutar máquinas virtuales.
- Tecnologías: Intel VT, AMD-V.

### Activación
- Habilitable desde UEFI/BIOS.

---

## Arquitectura

### Tamaño de Palabra
- 32 o 64 bits:
  - Determina el ancho de operandos, buses y memoria direccionable.
  - Actualmente dominan los sistemas de 64 bits.

---

## Alimentación Eléctrica

### Voltajes
- **Voltaje externo:** comunicación con la placa base (3.3V).
- **Voltaje interno:** operaciones del núcleo (0.5-2V).

---

## Overclocking

### Definición
- Incrementar la frecuencia de reloj más allá de los valores certificados.
- Consecuencias:
  - Mayor rendimiento.
  - Incremento del calor generado.
  - Requiere enfriamiento adicional.

---

