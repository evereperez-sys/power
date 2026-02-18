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



