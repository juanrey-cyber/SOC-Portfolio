# 🔐 Security+ — Día 38  
# Firmas, Comportamiento y Heurística — Cómo funcionan las detecciones modernas

## 🎯 Objetivo
Aprender cómo los sistemas de seguridad (AV, EDR, SIEM) detectan malware y actividad maliciosa.  
Esto es clave para entrevistas y para trabajar como SOC Analyst o Threat Hunter.

---

# 🟥 1. Detección basada en firmas (Signature-Based Detection)

### ¿Qué es?
El sistema compara archivos o procesos contra una “base de datos” de malware conocido.

Ejemplos:
- hash del archivo coincide con malware conocido  
- patrón específico dentro de un ejecutable  
- string malicioso en un script  

### Ventajas:
✔ muy precisa  
✔ poco falsa alarma  

### Desventajas:
✘ NO detecta malware nuevo  
✘ fácil de evadir si el atacante modifica el archivo  

### Lo que debes recordar para Security+:
- Usa *hashes*, *patrones*, *firmas del motor AV*.  
- Es como reconocer una cara conocida: si no está en la base, no la detecta.

---

# 🟧 2. Detección basada en comportamiento (Behavior-Based)

### ¿Qué es?
En lugar de mirar el archivo, observa **lo que el archivo hace**.

Ejemplos sospechosos:
- un proceso en `AppData` creando otro proceso  
- PowerShell ejecutando comandos codificados  
- un documento de Word lanzando `cmd.exe`  
- un proceso intentando deshabilitar antivirus  
- conexiones saliendo a IPs raras  

### Ventajas:
✔ detecta malware nuevo  
✔ detecta ataques sin archivos (fileless)  
✔ detecta técnicas MITRE  

### Desventajas:
✘ puede generar falsos positivos  

### Lo que debes recordar:
- Evalúa acciones, no archivo.  
- Es lo que usan **EDRs modernos** (CrowdStrike, SentinelOne, Defender).  
- Es *lo más poderoso* para Threat Hunting.

---

# 🟨 3. Detección heurística (Heuristic-Based)

### ¿Qué es?
El sistema usa reglas + lógica para adivinar si algo parece malicioso, aunque no sea malware conocido.

Ejemplos:
- archivo comprimido con contraseña que contiene `.exe`  
- macros en documentos  
- nombres sospechosos (xxJJ39.exe)  
- estructuras raras dentro del archivo  

### Ventajas:
✔ detecta malware desconocido  
✔ detecta patrones sospechosos  

### Desventajas:
✘ más falsos positivos  
✘ menos precisa que comportamiento  

### Úsalo para:
- identificar “probable malware”  
- evaluar archivos desconocidos  

---

# 🟦 4. Detección basada en IA/ML (moderna)

*Entender esto te da ventaja en entrevistas, pero lo explico simple.*

### ¿Qué hace?
Analiza:
- miles de características del archivo  
- patrones de comportamiento  
- similitudes con ataques anteriores  

NO necesitas saber matemáticas de ML.  
Debes saber:

✔ detecta malware antes de que se haga famoso  
✔ se adapta a nuevas amenazas  
✔ es “predictiva”, no solo reactiva  

---

# 🟪 5. ¿Cómo se ven estas detecciones en un entorno SOC?

Ejemplos reales que verías:

### Firma:
- “Malicious file detected — hash matches known malware”

### Comportamiento:
- “Suspicious PowerShell command executed”
- “Process spawned from unexpected parent”

### Heurística:
- “File contains characteristics similar to malware”
- “Document is attempting to run scripts”

### IA / ML:
- “Anomalous activity pattern detected”
- “High-risk behavior score”

---

# 🟫 6. Preguntas clásicas de entrevista (MUY comunes)

### ❓ “¿Cuál es la diferencia entre firma y comportamiento?”
Firma → compara archivo  
Comportamiento → observa acciones

### ❓ “¿Cómo detectarías malware fileless?”
Con detección basada en comportamiento (PowerShell anómalo).

### ❓ “¿Por qué las firmas no bastan?”
Porque los atacantes cambian el archivo ligeramente y evaden detección.

### ❓ “¿Qué ventaja tiene heurística?”
Detecta cosas “sospechosas” sin depender de firmas.

### ❓ “¿Para qué sirve ML?”
Para detectar malware y comportamientos nuevos, no vistos antes.

---

# ⭐ Resumen del Día 38

Hoy aprendiste:
- cómo detectan amenazas los antivirus y EDR  
- diferencias entre firmas, comportamiento y heurística  
- cómo se ven estas detecciones en un SIEM  
- qué responder en entrevistas  
- cómo piensa un verdadero Threat Hunter  

Este módulo es la base para:
➡️ Threat Hunting Jr  
➡️ SOC II  
➡️ Detection Engineer Jr  
➡️ DFIR Jr  

Y te coloca a un nivel superior frente a candidatos entry-level.
