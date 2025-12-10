# 🔐 Security+ — Día 40  
# Hardening del Sistema & Mitigación de Técnicas MITRE

## 🎯 Objetivo
Aprender defensas reales para frenar técnicas MITRE como ejecución maliciosa, persistencia, escalación de privilegios, movimiento lateral y exfiltración.  
Este módulo te acerca directamente a roles mejor pagados como SOC II, Threat Hunter Jr y Detection Engineer Jr.

---

# 🟥 1. ¿Qué es Hardening?

Hardening = reforzar el sistema para reducir las oportunidades de ataque.

Incluye:
- deshabilitar funciones innecesarias  
- limitar permisos  
- bloquear herramientas peligrosas  
- monitorear puntos críticos  
- aplicar configuraciones seguras  

El objetivo es **reducir la superficie de ataque**.

---

# 🟧 2. Mitigación para Ejecución Maliciosa (MITRE T1059)

La ejecución es una de las partes más comunes en ataques. Para frenarla:

### ✔ Restringir PowerShell
- activar **Constrained Language Mode**  
- bloquear PowerShell v2  
- permitir solo scripts firmados  
- registrar ScriptBlock Logging (evento 4104)

### ✔ Restringir cmd.exe y scripting
- permitir uso SOLO a roles administrativos  
- auditar comandos ejecutados  

### ✔ AppLocker o WDAC (Windows Defender Application Control)
Define exactamente qué aplicaciones pueden ejecutarse.

Previene:
- malware  
- ejecutables desde TEMP  
- scripts desconocidos  

### ✔ Bloquear macros peligrosas
- desactivar macros por defecto  
- bloquear macros provenientes de Internet  

---

# 🟨 3. Mitigación de Persistencia (MITRE T1547)

El atacante quiere quedarse dentro. Para evitarlo:

### ✔ Monitoreo y control de Run Keys
Las claves más usadas:
- `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`
- `HKLM\Software\...\Run`

Mitigación:
- alertar cambios  
- permitir solo apps firmadas  
- revisar Sysmon Event ID 13  

### ✔ Servicios sospechosos
- bloquear creación de servicios sin privilegios  
- alertar servicios nuevos con Sysmon Event ID 6  

### ✔ Tareas programadas
- auditar creación y modificación  
- alertar tareas fuera de horario  

---

# 🟦 4. Mitigación de Escalación de Privilegios (Privilege Escalation)

### ✔ Principio de Menor Privilegio
- nadie debe ser administrador por defecto  
- separar cuentas: una de uso normal y otra de admin  
- bloquear `RunAs` sin MFA  

### ✔ Restricción de herramientas de admin
- limitar `psexec`, `wmic`, `powershell` avanzado  
- permitir solo su uso a administradores legítimos  

### ✔ Parcheo
La mayoría de ataques de escalación explotan vulnerabilidades conocidas.  
Parches = la defensa más efectiva.

---

# 🟪 5. Mitigación de Movimiento Lateral (Lateral Movement — T1021, T1047)

### ✔ RDP Hardening
- deshabilitar RDP si no es necesario  
- permitirlo solo por VPN  
- bloquear conexiones externas  
- habilitar MFA  
- monitorear logon Type 10 (evento 4624)

### ✔ WMI Hardening
- limitar acceso remoto a WMI  
- alertar ejecución de `wmic` inusual  
- revisar Sysmon Event ID 1 (proceso creado)

### ✔ Bloquear SMB inseguro
- deshabilitar SMBv1  
- restringir puertos 445, 139  

### ✔ Reducción de superficie
- segmentar la red  
- evitar que un usuario pueda ver otras máquinas  

---

# 🟫 6. Mitigación de Credential Access (T1003)

### ✔ Proteger LSASS
- activar Credential Guard  
- evitar que usuarios puedan leer memoria  
- alertar Sysmon Event ID 10 (access to lsass.exe)

### ✔ Evitar contraseñas débiles
- política de contraseñas modernas  
- evitar password reuse  
- habilitar MFA  

### ✔ Limitar herramientas administrativas
- bloquear Mimikatz (firma + heurística + comportamiento)  

---

# 🟩 7. Mitigación de Exfiltración (Exfiltration)

### ✔ Monitorear conexiones de salida
- alertar conexiones a IPs desconocidas  
- bloquear tráfico hacia países no usados por la empresa  

### ✔ Detectar compresión de archivos
Eventos a monitorear:
- 4688 → ejecución de `zip`, `rar`, `7z`  

### ✔ DLP (Data Loss Prevention)
Evita que datos sensibles salgan por:
- correo  
- USB  
- web  
- aplicaciones  

### ✔ Limitar USB
- bloquear unidades externas  
- permitir solo dispositivos aprobados  

---

# 🟦 8. Preguntas típicas de entrevista

### ❓ "¿Cómo previenes ejecución maliciosa?"
→ AppLocker, WDAC, PowerShell restrictivo, macros bloqueadas.

### ❓ "¿Cómo previenes persistencia?"
→ monitoreo de Run Keys, servicios, tareas programadas.

### ❓ "¿Cómo previenes movimiento lateral?"
→ limitar RDP, bloquear WMI, segmentación de red.

### ❓ "¿Cómo proteges contra credential dumping?"
→ Credential Guard, limitar acceso a LSASS, Sysmon 10.

### ❓ "¿Cómo evitas exfiltración?"
→ análisis de tráfico saliente, DLP, alertas de compresión.

---

# ⭐ Resumen del Día 40

Hoy aprendiste:
- hardening del sistema  
- defensas contra técnicas MITRE clave  
- cómo frenar ejecución, persistencia, escalación, movimiento lateral y exfiltración  
- defensas que se usan en empresas reales  
- contenido que aparece en entrevistas profesionales  

Este módulo te posiciona como candidato serio para roles:
- Threat Hunter Jr  
- SOC Analyst II  
- Detection Engineer Jr  
- DFIR Jr  
