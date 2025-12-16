# 🔐 Security+ — Día 50  
# MITRE ATT&CK (cómo usarlo para pensar como SOC II / Threat Hunter Jr)

## 🎯 Objetivo
Entender MITRE ATT&CK como “mapa de tácticas y técnicas” para:
- investigar incidentes
- escribir detecciones
- hablar como profesional en entrevistas
- conectar logs (Windows/Linux/SIEM) con etapas de ataque

---

## 🟥 1. ¿Qué es MITRE ATT&CK?

MITRE ATT&CK es una base de conocimiento que describe:
- cómo atacan en el mundo real
- en qué etapas del ataque
- con qué técnicas

En vez de decir “me hackearon”, dices:
“Hubo ejecución + persistencia + movimiento lateral”.

Eso te sube de nivel en entrevistas.

---

## 🟧 2. Tácticas vs Técnicas (la idea clave)

- Táctica = el objetivo (el “para qué”)
- Técnica = el método (el “cómo”)

Ejemplo:
Táctica: Credential Access (robar credenciales)
Técnica: OS Credential Dumping (intentar extraer credenciales del sistema)

---

## 🟨 3. Las tácticas que más verás en SOC (alto impacto)

Initial Access
Execution
Persistence
Privilege Escalation
Defense Evasion
Credential Access
Discovery
Lateral Movement
Collection
Command and Control
Exfiltration
Impact

(Impact incluye ransomware, borrado, interrupción de servicio.)

---

## 🟦 4. Cómo conectar MITRE con logs (lo que tú ya aprendiste)

Ejemplos prácticos:

Execution:
- PowerShell 4104 con script sospechoso
- Sysmon Event 1 con command line rara

Credential Access:
- Sysmon Event 10 (acceso a LSASS)
- procesos intentando herramientas de dumping

Lateral Movement:
- 4624 Logon Type 3 o Type 10 (RDP)
- WMI o servicios remotos (si aparece en tu telemetría)

Command and Control (C2):
- Sysmon Event 3: conexiones repetidas a IP desconocida
- tráfico pequeño y constante (beaconing)

Persistence:
- creación de usuarios
- tareas programadas
- cambios de servicios

---

## 🟪 5. Cómo usar MITRE en entrevistas (frases que suman salario)

En vez de:
“vi un login raro”

Dices:
“Observé intentos fallidos (4625) seguidos de acceso exitoso (4624), lo que sugiere brute force o password spraying. Luego revisé Execution y C2 buscando procesos anómalos y conexiones repetitivas.”

Eso suena a SOC II.

---

## 🟫 6. Mini-playbook (plantilla mental para investigar con MITRE)

Paso 1: Identifica el evento inicial (alerta SIEM o log clave)
Paso 2: Clasifica la etapa MITRE probable (Initial Access / Execution / etc.)
Paso 3: Busca evidencia hacia adelante (¿hubo persistencia? ¿hubo C2?)
Paso 4: Busca evidencia hacia atrás (¿cómo entró? ¿phishing? ¿RDP?)
Paso 5: Decide: benigno, falso positivo o incidente
Paso 6: Documenta con lenguaje MITRE (profesional)

---

## 🟩 7. Checklist “MITRE rápido” para tu portfolio

Para cada mini-investigación en GitHub, incluye:
- Qué pasó (resumen)
- Evidencia (logs/eventos)
- Mapeo MITRE (tácticas/técnicas)
- Qué harías como respuesta (containment)
- Qué mejorarías (hardening)

---

## ⭐ Resumen del Día 50

Hoy aprendiste:
- qué es MITRE ATT&CK y para qué sirve
- diferencia táctica vs técnica
- cómo conectar MITRE con Windows/Linux/Sysmon/SIEM
- cómo hablar como SOC II en entrevistas
- plantilla de investigación profesional para tu GitHub
