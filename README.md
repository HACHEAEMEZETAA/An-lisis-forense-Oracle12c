# PROYECTO G10 - EQUIPO FORENSE ORACLE

## 📋 Documentación Completa del Análisis Forense Digital

Este documento presenta la metodología, los procedimientos técnicos y los resultados de un análisis forense digital especializado en entornos Oracle, llevado a cabo por el **Equipo Forense Oracle**. El proyecto se centra en la identificación, recolección, análisis y preservación de evidencia digital en un entorno de **Windows Server 2012** con **Oracle 12c**.

---

## 🎯 Objetivos del Proyecto

El **Objetivo General** es desarrollar e implementar una metodología forense especializada en entornos Oracle que permita identificar, recolectar y analizar evidencia digital de manera precisa y conforme a las normativas vigentes.

**Objetivos Específicos:**
* Aplicar protocolos que aseguren la integridad y autenticidad de la evidencia.
* Detectar y documentar accesos no autorizados y manipulaciones en bases de datos Oracle.
* Validar y optimizar el proceso forense mediante pruebas piloto y análisis de resultados.

---

## ⚖️ Principios Clave y Normativa

El análisis se rige por principios fundamentales y cumple con normativas clave para garantizar la validez legal de la evidencia:

### Principios Clave
* **Integridad:** Garantizar que la evidencia no sufra alteraciones durante su adquisición y análisis.
* **Cadena de Custodia:** Registro exhaustivo de cada acceso y manipulación de la evidencia para preservar su valor legal.
* **Repetibilidad:** Diseño de procesos replicables que permitan obtener resultados consistentes en análisis realizados por diferentes expertos.

### Normativas Relevantes
* **RGPD (Reglamento General de Protección de Datos):** Establece principios y obligaciones en el tratamiento de datos personales en la Unión Europea.
* **Convención de Budapest sobre Ciberdelincuencia:** Marco internacional para la cooperación en la investigación de delitos informáticos.
* **ISO/IEC 27037:** Directrices para la identificación, recopilación y preservación de evidencias digitales.
* **NIST 800-86:** Guía para la realización de análisis forense digital en sistemas informáticos.

---

## ⚙️ Fases del Análisis Forense Digital

El proyecto se estructura en fases, siguiendo una metodología de análisis forense digital:

1.  **Identificación:** Determinar la información relevante (logs de auditoría, registros de transacciones, archivos de configuración) y los dispositivos y sistemas Oracle involucrados.
2.  **Adquisición:** Extracción de datos mediante técnicas forenses (copias bit a bit) y captura de registros de transacciones (redo logs, undo logs, flashback logs) sin alterar la información original.
3.  **Análisis:** Examen detallado de la actividad registrada en la base de datos para identificar irregularidades, detectar accesos no autorizados y correlacionar eventos.
4.  **Documentación y Presentación:** Elaboración de informes técnicos que incluyan metodología, hallazgos y conclusiones.

---

## 🛠️ Herramientas de Software Forense y Entorno

El análisis se realiza en un entorno de laboratorio virtualizado con **Windows Server 2012** y **Oracle 12c**, utilizando herramientas especializadas:

### Herramientas Específicas para Oracle
* **Oracle LogMiner:** Análisis detallado de transacciones.
* **Oracle Auditing:** Monitoreo y revisión de actividades.
* **AWR (Automatic Workload Repository):** Evaluación del rendimiento y cambios en la base de datos.
* **SQL Developer Forensics:** Recuperación y análisis de datos eliminados o alterados.

### Software Forense General
* **Autopsy:** Plataforma de código abierto para análisis forense de discos y sistemas de archivos, usada para la recuperación de archivos eliminados y extracción de metadatos.
* **Volatility:** Herramienta para análisis de memoria RAM.
* **Wireshark:** Analizador de protocolos de red para captura y análisis de tráfico.
* **Kaspersky Endpoint Security:** Utilizado para la revisión de registros de amenazas.
* **Nmap:** Herramienta de escaneo de redes para detectar dispositivos y evaluar vulnerabilidades.

---

## 🔎 Hallazgos Clave del Análisis (Fase 4 - Día 7-8)

El análisis técnico detallado confirmó una intrusión en el entorno Oracle 12c/Windows Server 2012, con el siguiente impacto:

| Categoría | Nivel | Detalle |
| :--- | :--- | :--- |
| **Confidencialidad** | Alto | 12 GB de datos sensibles exfiltrados |
| **Integridad** | Crítico | Credenciales DBA comprometidas |
| **Disponibilidad** | Medio | Downtime de 15 minutos |

### Línea de Tiempo del Ataque
* **10:15:32:** Explotación de Oracle TNS Listener (CVE-2023-1234).
* **10:16:18:** Ejecución de `"sqlplus.exe"` desde `C:\Temp\`.
* **10:17:45:** Conexión a C2 (`192.168.1.100:443`) vía DNS tunneling.
* **10:19:30:** Descarga de herramienta Mimikatz en memoria.

### Evidencia Digital Recolectada
* **Memoria RAM (Volatility):** Proceso `sqlplus.exe` (PID 1234) cuyo padre era `cmd.exe` (PID 567) con línea de comando maliciosa.
* **Logs de Oracle:** Consulta maliciosa detectada: `GRANT DBA TO attacker_user;`.

---

## 🛡️ Recomendaciones de Mitigación

### Acciones Inmediatas
* **Contención:**
