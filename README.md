# Power Server Linux Project

📘 Resumen académico

El texto expone la implementación de Power Server y Power Client sobre Linux (Ubuntu 22.04) utilizando Engine, basada estrictamente en la documentación oficial de Appeon y en las directrices de Power Server 2025. La experiencia presentada corresponde a un entorno productivo desarrollado por la especialista Alda Marilla González, representante de Jirama Soft, empresa orientada a soluciones de gestión empresarial.

1️⃣ Contexto y justificación

Tradicionalmente, las aplicaciones desarrolladas en PowerBuilder se implementaban en arquitecturas cliente-servidor dentro de redes locales o sobre entornos Windows con IIS. Sin embargo, la adopción de Power Server amplía el panorama tecnológico, permitiendo despliegues en Linux con servicios HTTPS, certificados SSL, proxies inversos y configuraciones avanzadas de seguridad.

En este escenario, Engine cumple un rol fundamental como:

Intermediario (reverse proxy)

Capa de seguridad

Gestor de múltiples servicios Power Server

Punto de terminación HTTPS

La arquitectura permite que Power Server opere internamente bajo HTTP, mientras Engine administra HTTPS, certificados, dominios y reglas de seguridad, desacoplando completamente la capa pública de la lógica de aplicación.

2️⃣ Arquitectura técnica

La solución se implementa sobre:

Ubuntu Server 22.04

Power Server Web API

Engine Service

Base de datos PostgreSQL

Servicios Linux configurados con reinicio automático (alta disponibilidad 24/7)

Características clave:

Múltiples Power Server publicados en un mismo servidor.

Cada servicio asociado a un puerto específico.

Un único punto de acceso público (URL).

Gestión centralizada mediante archivos de configuración.

Reverse proxy interno gestionado por Engine.

Seguridad avanzada: SSL, limitación de IPs, cabeceras HTTP seguras.

Esta arquitectura garantiza:

Escalabilidad

Aislamiento de servicios

Seguridad perimetral

Facilidad de mantenimiento

3️⃣ Flujo de despliegue

El proceso de despliegue comprende:

Compilación en PowerBuilder

Configuración tipo Folder.

Generación de runtime y cloud install.

Definición de target Linux 64-bit para Power Server.

Transferencia al servidor

Mediante WinSCP o automatización con scripts .bat.

Compresión previa para optimizar transferencia.

Despliegue en Ubuntu

Descompresión automática.

Actualización de directorios.

Reinicio del servicio.

Verificación mediante logs y estado del servicio.

Se automatiza el proceso para múltiples proyectos, permitiendo desplegar nuevas aplicaciones mediante parámetros configurables, reduciendo errores y tiempos operativos.

4️⃣ Seguridad y producción

La implementación enfatiza que no basta con que el sistema funcione, sino que debe cumplir requisitos de producción:

Servicios corriendo como daemon (no manuales).

Reinicio automático ante fallos.

Configuración SSL.

Restricción de IPs.

Cabeceras de seguridad.

Separación lógica de cliente y API.

Desde la perspectiva del usuario final, el sistema es transparente: percibe una única aplicación web, independientemente de si internamente opera como Power Client o Power Server.

5️⃣ Conclusión académica

La implementación demuestra que Power Server puede ejecutarse eficientemente en Linux sin depender exclusivamente de entornos Windows. El uso de Engine como proxy inverso y capa de seguridad permite:

Desacoplar infraestructura de aplicación.

Publicar múltiples servicios bajo una sola URL.

Mejorar seguridad y mantenibilidad.

Garantizar disponibilidad continua.

La propuesta no redefine la arquitectura oficial, sino que la respeta y extiende hacia un entorno Linux robusto, estable y apto para producción empresarial.

🧠 Mapa Conceptual
```mermaid
flowchart TD

    A[Implementación Power Server en Linux] 

    A --> B[Base Tecnológica]
    B --> B1[PowerBuilder 2025]
    B --> B2[Power Server 2025]
    B --> B3[Engine]
    B --> B4[Ubuntu 22.04]
    B --> B5[PostgreSQL]

    A --> C[Arquitectura]
    C --> C1[Power Client]
    C1 --> C2[Conexión HTTPS]
    C2 --> C3[Engine - Reverse Proxy]
    C3 --> C4[Power Server - HTTP Interno]
    C4 --> C5[Base de Datos PostgreSQL]

    A --> D[Seguridad]
    D --> D1[Certificados SSL]
    D --> D2[Restricción de IPs]
    D --> D3[Cabeceras HTTP Seguras]
    D --> D4[Servicios con Auto-Reinicio]

    A --> E[Despliegue]
    E --> E1[Compilación en PowerBuilder]
    E --> E2[Generación Folder]
    E --> E3[Compresión]
    E --> E4[Transferencia SSH / WinSCP]
    E --> E5[Descompresión en Ubuntu]
    E --> E6[Reinicio Servicio]

    A --> F[Beneficios]
    F --> F1[Escalabilidad]
    F --> F2[Centralización]
    F --> F3[Múltiples Proyectos]
    F --> F4[Alta Disponibilidad 24/7]
    F --> F5[Mantenibilidad]


IMPLEMENTACIÓN POWER SERVER EN LINUX
│
├── Base Tecnológica
│   ├── PowerBuilder
│   ├── Power Server 2025
│   ├── Engine
│   ├── Ubuntu 22.04
│   └── PostgreSQL
│
├── Arquitectura
│   ├── Cliente (Power Client)
│   │      └── Conexión HTTPS
│   │
│   ├── Engine
│   │      ├── Reverse Proxy
│   │      ├── Gestión SSL
│   │      ├── Seguridad
│   │      └── Enrutamiento por puerto
│   │
│   ├── Power Server (HTTP interno)
│   │      ├── Web API
│   │      └── Servicios por proyecto
│   │
│   └── Base de Datos
│          └── PostgreSQL
│
├── Seguridad
│   ├── Certificados SSL
│   ├── Restricción IP
│   ├── Cabeceras HTTP
│   └── Servicios Linux con reinicio automático
│
├── Despliegue
│   ├── Compilación en PowerBuilder
│   ├── Generación Folder
│   ├── Compresión
│   ├── Transferencia (WinSCP / Script .bat)
│   ├── Descompresión en servidor
│   └── Reinicio servicio
│
└── Beneficios
    ├── Escalabilidad
    ├── Centralización
    ├── Múltiples proyectos
    ├── Alta disponibilidad 24/7
    └── Mantenibilidad simplificada

Aquí tienes el contenido organizado en formato Markdown, optimizado para que se vea profesional en un archivo README.md de GitHub. He incluido una sección de arquitectura con Mermaid, que GitHub renderiza automáticamente como un diagrama.Implementación de Power Server y Power Client sobre Ubuntu con NginxEste repositorio contiene el resumen ejecutivo y la estructura técnica de la implementación de soluciones PowerBuilder en entornos Linux, basada en la presentación de la Ing. Alda Marilla González (Jirama Soft).📝 Resumen AcadémicoLa transición de aplicaciones tradicionales de escritorio hacia la web mediante Power Server y Power Client permite modernizar sistemas legados sin perder la robustez de PowerBuilder. El uso de Ubuntu Server 22.04 como sistema operativo base, junto con Nginx como servidor web y proxy inverso, ofrece una infraestructura estable, segura y altamente escalable.Puntos Clave:Desvinculación de IIS: Se rompe la dependencia de Windows Server para el despliegue de APIs.Seguridad Avanzada: Nginx actúa como escudo (terminación SSL, filtrado de IPs y cabeceras de seguridad), manteniendo a Power Server aislado de ataques directos.Alta Disponibilidad: Configuración de servicios en Linux con reinicio automático (Daemon) para asegurar operatividad 24/7.Automatización: Uso de scripts .bat (Windows) y .sh (Linux) para comprimir, transferir y desplegar cambios en segundos.🏗️ Arquitectura TécnicaComponenteTecnologíaFunciónSO ServidorUbuntu 22.04Host principal de los servicios.Proxy InversoNginx (Engine)Gestión de HTTPS, certificados y ruteo por puertos.App ServerPower Server (Web API)Ejecución de la lógica de negocio sobre .NET Core.Base de DatosPostgreSQLAlmacenamiento de datos persistentes.ClientePower ClientAplicación instalable que se comunica vía HTTPS.🗺️ Mapa Conceptual (Mermaid)GitHub renderizará el siguiente código como un diagrama de flujo:Fragmento de códigograph TD
    User((Usuario / Power Client)) -- HTTPS/SSL --> Nginx{Nginx Proxy Inverso}
    
    subgraph Servidor Ubuntu 22.04
        Nginx -- Port Mapping --> PS1[Power Server API - Proyecto A]
        Nginx -- Port Mapping --> PS2[Power Server API - Proyecto B]
        PS1 --> DB[(PostgreSQL)]
        PS2 --> DB
    end

    subgraph Flujo de Despliegue
        PB[PowerBuilder 2025] --> Comp[Compilación Local]
        Comp --> Bat[Script .BAT / WinSCP]
        Bat --> Unzip[Script .SH / Despliegue]
    end
🚀 Flujo de Despliegue AutomatizadoEl proceso de actualización se resume en tres etapas críticas:Compilación en PowerBuilder 2025: Se genera el target para Linux 64-bit (Power Server) y los archivos de instalación (Power Client).Transferencia Segura: Un script local comprime los binarios y los envía al servidor mediante SCP o WinSCP.Actualización en Caliente: Un script en el servidor descomprime los archivos en el directorio /var/www/ y reinicia los servicios del sistema para aplicar cambios sin intervención manual extensa.Nota: "Engine" (Nginx) es el encargado de decidir qué Power Server responde a cada URL recibida, permitiendo manejar múltiples sistemas en un solo servidor Linux.🛠️ Requisitos de ImplementaciónLicencia activa de Apeon PowerBuilder (Cloud Edition).Servidor con Ubuntu 22.04 LTS.SDK de .NET Runtime instalado en el servidor.Configuración de systemd para la gestión de procesos de la API.



