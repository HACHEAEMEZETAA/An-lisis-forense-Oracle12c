# PROYECTO G10 - EQUIPO FORENSE ORACLE

## 📋 Documentación Completa del Análisis Forense Digital

[cite_start]Este documento presenta la metodología, los procedimientos técnicos y los resultados de un análisis forense digital especializado en entornos Oracle, llevado a cabo por el **Equipo Forense Oracle**[cite: 1]. [cite_start]El proyecto se centra en la identificación, recolección, análisis y preservación de evidencia digital [cite: 12] [cite_start]en un entorno de **Windows Server 2012** con **Oracle 12c**[cite: 309, 260].

---

## [cite_start]🎯 Objetivos del Proyecto [cite: 58, 62]

[cite_start]El **Objetivo General** es desarrollar e implementar una metodología forense especializada en entornos Oracle[cite: 61].

**Objetivos Específicos:**
* [cite_start]Aplicar protocolos que aseguren la integridad y autenticidad de la evidencia[cite: 63].
* [cite_start]Detectar y documentar accesos no autorizados y manipulaciones en bases de datos Oracle[cite: 64].
* [cite_start]Validar y optimizar el proceso forense mediante pruebas piloto y análisis de resultados[cite: 65].

---

## [cite_start]⚖️ Principios Clave y Normativa [cite: 29]

El análisis se rige por principios fundamentales y cumple con normativas clave para garantizar la validez legal de la evidencia:

### Principios Clave
* [cite_start]**Integridad:** Garantizar que la evidencia no sufra alteraciones[cite: 31, 32].
* [cite_start]**Cadena de Custodia:** Registro exhaustivo de cada acceso y manipulación[cite: 35, 36].
* [cite_start]**Repetibilidad:** Diseño de procesos replicables para obtener resultados consistentes[cite: 37, 38].

### Normativas Relevantes
* [cite_start]**RGPD (Reglamento General de Protección de Datos):** Normas sobre el tratamiento de datos personales[cite: 42, 43].
* [cite_start]**Convención de Budapest sobre Ciberdelincuencia:** Marco internacional para delitos informáticos[cite: 48, 49].
* [cite_start]**ISO/IEC 27037:** Directrices para la identificación, recopilación y preservación de evidencias digitales[cite: 51].
* [cite_start]**NIST 800-86:** Guía para la realización de análisis forense digital[cite: 54].

---

## [cite_start]⚙️ Fases del Análisis Forense Digital [cite: 90]

El proyecto se estructura en fases, siguiendo una metodología de análisis forense digital:

1.  [cite_start]**Identificación:** Determinar la información relevante (logs de auditoría, registros de transacciones) y los sistemas involucrados[cite: 91, 92, 93].
2.  [cite_start]**Adquisición:** Extracción de datos (copias bit a bit) y captura de registros de transacciones (redo logs, undo logs) sin alterar la información original[cite: 94, 95, 96].
3.  [cite_start]**Análisis:** Examen detallado de la actividad registrada para identificar irregularidades, accesos no autorizados y patrones de fraude[cite: 97, 98, 99].
4.  [cite_start]**Documentación y Presentación:** Elaboración de informes técnicos, presentación de evidencias y preparación de testimonio experto[cite: 101, 102, 103, 104].

---

## 🛠️ Herramientas de Software Forense y Entorno

[cite_start]El análisis se realiza en un entorno de laboratorio virtualizado [cite: 105] [cite_start]con **Windows Server 2012** [cite: 108] [cite_start]y **Oracle 12c**[cite: 110], utilizando herramientas especializadas:

### [cite_start]Herramientas Específicas para Oracle [cite: 163]
* [cite_start]**Oracle LogMiner:** Análisis detallado de transacciones[cite: 164].
* [cite_start]**Oracle Auditing:** Monitoreo y revisión de actividades[cite: 166].
* [cite_start]**SQL Developer Forensics:** Recuperación y análisis de datos eliminados o alterados[cite: 167].

### [cite_start]Software Forense General [cite: 183]
* [cite_start]**Autopsy:** Plataforma de código abierto para análisis forense de discos y sistemas de archivos, usada para la recuperación de archivos eliminados y análisis de metadatos[cite: 194, 195, 311].
* [cite_start]**Volatility:** Herramienta para análisis de memoria RAM[cite: 200].
* [cite_start]**Wireshark:** Analizador de protocolos de red para captura y análisis de tráfico[cite: 205].
* [cite_start]**Kaspersky Endpoint Security:** Utilizado para la revisión de registros de amenazas[cite: 185, 187].
* [cite_start]**Nmap:** Herramienta de escaneo de redes para evaluar vulnerabilidades[cite: 211].

---

## [cite_start]🔎 Hallazgos Clave del Análisis (Fase 4 - Día 7-8) [cite: 442]

[cite_start]El análisis técnico detallado confirmó una intrusión en el entorno[cite: 445, 446], con el siguiente impacto:

| Categoría | Nivel | Detalle |
| :--- | :--- | :--- |
| **Confidencialidad** | Alto | [cite_start]12 GB de datos sensibles exfiltrados [cite: 456] |
| **Integridad** | Crítico | [cite_start]Credenciales DBA comprometidas [cite: 456] |
| **Disponibilidad** | Medio | [cite_start]Downtime de 15 minutos [cite: 456] |

### [cite_start]Línea de Tiempo del Ataque [cite: 458]
* [cite_start]**10:15:32:** Explotación de Oracle TNS Listener (CVE-2023-1234)[cite: 459].
* [cite_start]**10:16:18:** Ejecución de `"sqlplus.exe"` desde `C:\Temp\`[cite: 461].
* [cite_start]**10:17:45:** Conexión a C2 (`192.168.1.100:443`) vía DNS tunneling[cite: 463].
* [cite_start]**10:19:30:** Descarga de herramienta Mimikatz en memoria[cite: 464].

### Evidencia Digital Recolectada
* [cite_start]**Memoria RAM (Volatility):** Proceso `sqlplus.exe` (PID 1234) cuyo padre era `cmd.exe` (PID 567) con línea de comando maliciosa[cite: 466, 468, 469, 470].
* [cite_start]**Logs de Oracle:** Consulta maliciosa detectada: `GRANT DBA TO attacker_user;`[cite: 472, 473].

---

## [cite_start]🛡️ Recomendaciones de Mitigación [cite: 486]

### [cite_start]Acciones Inmediatas [cite: 487]
* [cite_start]**Contención:** Aislar servidores afectados (VLAN de cuarentena) y revocar privilegios DBA no esenciales[cite: 489, 490].
* [cite_start]**Erradicación:** Ejecutar el comando `Stop-Process -Name "sqlplus" -Force` en PowerShell para eliminar procesos maliciosos[cite: 494].

### [cite_start]Mejoras a Largo Plazo [cite: 496, 497]
* [cite_start]**Hardening Oracle:** Implementar Database Vault (Prioridad Alta)[cite: 497].
* [cite_start]**Monitoreo:** Desplegar SIEM con reglas Sigma (Prioridad Crítica)[cite: 497].
* [cite_start]**Adicional:** Se recomienda una revisión periódica de cuentas y la implementación de políticas de control de acceso más estrictas[cite: 621].
