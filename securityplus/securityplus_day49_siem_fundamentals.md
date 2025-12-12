# Security+ — Día 49  
# SIEM Fundamentals explicado fácil

Objetivo:
Comprender qué es un SIEM, qué logs procesa, cómo genera alertas y cómo trabaja un analista SOC con Splunk, Sentinel o Elastic.

------------------------------------------------------------
1. Qué es un SIEM
------------------------------------------------------------
Un SIEM es una plataforma que:
- recolecta logs
- normaliza la información
- correlaciona eventos
- genera alertas
- permite investigar incidentes

Ejemplos:
Splunk
Microsoft Sentinel
Elastic SIEM
QRadar
ArcSight

------------------------------------------------------------
2. Qué hace un SIEM
------------------------------------------------------------
Recolección: obtiene logs de Windows, Linux, firewalls, aplicaciones, cloud, EDR.
Normalización: convierte todos los logs a un formato entendible.
Correlación: detecta patrones sospechosos combinando eventos.
Alertas: crea notificaciones cuando algo parece ataque.
Investigación: permite hacer búsquedas, análisis y reconstruir incidentes.

------------------------------------------------------------
3. Logs más comunes dentro de un SIEM
------------------------------------------------------------
Windows Event Logs: 4624, 4625, 4672, 4104, etc.
Sysmon: creación de procesos, conexiones de red, hashes.
Linux: auth log, ssh logs, sudo usage.
Firewall: tráfico permitido o bloqueado.
Cloud: cambios en IAM, permisos, buckets.
EDR: detecciones, malware, C2, beaconing.

------------------------------------------------------------
4. Cómo ve un SOC las alertas dentro del SIEM
------------------------------------------------------------
Ejemplo alerta fuerza bruta:
Multiple failed logins for user admin desde IP externa.
Interpretación: ataque automatizado.

Ejemplo alerta PowerShell sospechoso:
EncodedCommand ejecutado por powershell.exe lanzado por winword.exe.
Interpretación: macro maliciosa o script malicioso.

Ejemplo alerta C2:
Conexiones periódicas a IP desconocida desde un proceso raro.
Interpretación: beaconing.

------------------------------------------------------------
5. Flujo de investigación en un SIEM
------------------------------------------------------------
1. Revisar la alerta: usuario, host, hora, tipo de evento.
2. Buscar eventos relacionados: logon, procesos, red, sysmon.
3. Contextualizar: IP válida, hora esperada, usuario legítimo.
4. Determinar si es benigno, falso positivo o incidente real.
5. Escalar si es necesario.

------------------------------------------------------------
6. Detecciones típicas en SIEM
------------------------------------------------------------
Fuerza bruta: muchos intentos fallidos seguidos.
RDP sospechoso: logon type 10 desde IP interna rara.
PowerShell peligroso: comandos codificados o lanzados por Office.
Persistencia: creación de nuevos usuarios o servicios.
C2: conexiones salientes repetidas.
SSH brute force: muchos failed password en Linux auth log.

------------------------------------------------------------
7. Preguntas comunes de entrevista
------------------------------------------------------------
Qué es un SIEM: plataforma para recolectar logs, correlarlos y generar alertas.
Qué logs entran en un SIEM: Windows, Linux, firewall, EDR, cloud.
Cómo detectar fuerza bruta: múltiples eventos fallidos seguidos por uno exitoso.
Qué evento indica PowerShell sospechoso: comandos codificados o llamados desde procesos no usuales.
Por qué es importante Sysmon: porque muestra procesos, parent processes, conexiones de red y hashes.

------------------------------------------------------------
Resumen Día 49
------------------------------------------------------------
Aprendiste:
- funcionamiento de un SIEM
- tipos de logs
- ejemplos de alertas reales
- cómo piensa un analista SOC
- detecciones típicas
- preguntas de entrevista
