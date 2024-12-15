(práctica : Virtualización con Proxmox en Debian)

# Hipervisores I

## Hipervisores clase 1

- **Conocidos como hipervisores nativos o sin sistema operativo**, se ejecuta directamente en el hardware del host y gestiona los equipos virtuales y sus sistemas operativos. Otro nombre que reciben también es el de **bare-metal**.
- **Suelen usar todo el hardware disponible** para solo la virtualización.
- Los solemos encontrar en **los centros de datos empresariales** o en otros entornos basados en servidores.
- Los más conocidos son: **KVM, VMware vSphere, Citrix Xen Server, ProxMox, Microsoft Hyper-V** y **OpenVZ**.

# Hipervisores II

## Hipervisores clase 2

- **Conocidos como hipervisores alojados**, se ejecutan en un sistema operativo convencional como una capa de software o una aplicación más compitiendo por recursos.
- Es una mejor solución para **los usuarios individuales** que buscan experimentar ejecutando varios sistemas operativos en una computadora personal, al mismo tiempo que usan otro tipo de aplicaciones según las requieran.
- Los más conocidos son: **VMware Workstation Player, Oracle VirtualBox, Linux Virtual Manager** y **Parallels**.

# Hipervisores III 

## Contenedores

- Es un conjunto de **uno o más procesos independientes y aislados** del resto del sistema operativo base, pero ejecutándose sobre este en un **espacio protegido (sandbox)**.
- Permite que los procesos accedan solo a las **solicitudes de recursos** que se especificaron.
- Estas **limitaciones en los recursos** garantizan que el contenedor pueda ejecutarse en un nodo con suficiente capacidad **optimizando el uso de los recursos**.

# ProxMox VE ( Debian GNU Linux )

- **Hipervisor de clase 1** de **Código Abierto**.
- Usando **Debian** como base (SO mínimo, Kernel, librerías y utilerías).
- Para **plataformas x86_64** con soporte de virtualización por hardware.
- Permite **virtualización de equipos** usando **KVM** y **Qemu**.
- Permite activación de **Contenedores** usando **Linux Containers (LXC)**.
- Permite la conexión con **múltiples fuentes de almacenamiento seguro**.
- Puede trabajar con otros dos productos de apoyo:
  - **ProxMox Mail Gateway**
  - **ProxMox BackUp Server**

# Características de ProxMox para un Clúster

- Tiene como pilares **tres ejes**, independiente entre sí:
  - **Procesamiento** (nodos, procesadores, núcleos y memoria).
  - **Almacenamiento** (espacios comunes que comparten archivos).
  - **Comunicaciones** (Red de Datos, Red de Almacenamiento).
  
- La **Gestión** une a los tres ejes de forma central, controlando todo:
  - Gestión vía **aplicación nativa y específica** (no es el caso de ProxMox).
  - Gestión vía **interfaz web**, con soporte a **Clústers**.

- **Virtualización** de múltiples tipos de hardware / computadoras (**KVM + Qemu**).

- **Definición y activación de Contenedores** (Linux Containers - **LXC**).

# Requerimientos

- **Red de Almacenamiento** (si se usa clúster de almacenamiento):
  - En caso de **SAN** o de **Clúster**, la red de almacenamiento puede ser independiente (**Ceph** puede estar en los nodos de procesamiento).

- **Red de Datos**:
  - Switcher desde **100 Mbps** (aunque no se recomienda), hasta **10 Gbps**.
  - Con el número de **puertos** para el máximo de nodos (**x2** si se considera redundancia).
  - Cada nodo contando al menos con una **tarjeta de red** correspondiente; pueden ser más (si se considera redundancia y red de almacenamiento).

# Beneficios I

## Beneficios del uso de Clúster de Virtualización:

- Menor número de equipos físicos (máquinas reales).
- Mayor utilización de la inversión (uso intensivo de los recursos).
- Reducción de costos de operación (**mejor ROI**).
- Menor complejidad y gasto de energía eléctrica.
- Mantenimiento de menor impacto.
- Mayor flexibilidad y adaptabilidad.
- Mayor disponibilidad en servicios.

# Beneficios II

## Beneficios para la Gestión de cada Máquina Virtual:

- **Independencia** entre máquinas y sistemas operativos.
- **Uso del tiempo relativo**:
  - Se pueden generar **time stamps** y regresar a esos puntos.
  - Se puede **detener la ejecución** y continuarla después.
- **Migración de máquinas virtuales en vivo**.
- **Ajuste de características en hardware** según requerimientos 
  (sin necesidad de comprar más hardware).
- **Declaración de servidores de Alta Disponibilidad (HA)**.

# Hardware e Hipervisor Tipo I

## Tabla: Hipervisor tipo I y Hardware

| Aplicaciones | Aplicaciones | Aplicaciones | Aplicaciones |
|--------------|--------------|--------------|--------------|
| **SO no modificado (anfitrión)** | **SO no modificado (huésped)** | **SO no modificado (huésped)** | **SO no modificado (huésped)** |
| **hipervisor tipo I (micro-kernel)** | **Anillo -1** | **hardware** |  |

---

## Información Adicional

- **Hardware**: Extensiones en CPU (Intel-VT, AMD-V)
- **Hipervisor tipo I**  
- **Ejemplos**: KVM, Xen HVM, Hyper-V  
- **Ventajas**: Alto rendimiento  
- **Defecto**: No sirve en hardware convencional  
- **Utilización**: Servidores / CPD


# Hardware e Hipervisor Tipo II

## Tabla: Hipervisor tipo II y Hardware

| Aplicaciones | Aplicaciones | Aplicaciones |
|--------------|--------------|--------------|
| **SO no modificado (huésped)** | **SO no modificado (huésped)** | **SO no modificado (huésped)** |
| **hipervisor tipo II** | **hipervisor tipo II** | **hipervisor tipo II** |
| **SO no modificado (anfitrión)** | **hardware** |  |

---

## Información Adicional

- **Hardware**: Convencional
- **Hipervisor tipo II**
- **Ejemplos**: VMWare Server, VirtualBox, Parallels Desktop, Virtual PC  
- **Ventaja**: Facilidad de uso  
- **Defecto**: Bajo rendimiento  
- **Utilización**: Virtualización en equipos convencionales


# Tabla de Virtualización y Licencias

| **Nombre**           | **Emu** | **Comp** | **Para** | **Hw** | **Cont** | **Licencia**  |
|-----------------------|:-------:|:--------:|:--------:|:------:|:--------:|:-------------:|
| Qemu                 | ✅      | ❌       | ❌       | ❌     | ❌       | Libre         |
| Xen                  | ❌      | ❌       | ✅       | ✅     | ❌       | Libre         |
| VirtualBox           | ❌      | ✅       | ❌       | ❌     | ❌       | Mixta         |
| LXC                  | ❌      | ❌       | ❌       | ❌     | ✅       | Libre         |
| Jails                | ❌      | ❌       | ❌       | ❌     | ✅       | Libre         |
| Containers           | ❌      | ❌       | ❌       | ❌     | ✅       | Libre         |
| KVM                  | ❌      | ❌       | ❌       | ✅     | ❌       | Libre         |
| VMWare ESX(i)        | ❌      | ❌       | ✅       | ❌     | ❌       | Privativa     |
| Hyper-V              | ❌      | ❌       | ✅       | ❌     | ❌       | Privativa     |
| XenServer            | ❌      | ❌       | ✅       | ✅     | ❌       | Libre?        |
| Virtuozzo            | ❌      | ❌       | ❌       | ❌     | ✅       | Privativa     |


