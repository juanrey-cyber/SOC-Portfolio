# 🛡️ Reporte 12 — Alert Triage (Priorización de Alertas)

## 🎯 Objetivo
Demostrar cómo un analista SOC clasifica, prioriza y toma decisiones basadas en alertas generadas por un SIEM, separando falsos positivos de incidentes reales.

---

# 🧠 1. ¿Qué es Alert Triage?
Alert Triage = el proceso de:
1. Recibir una alerta  
2. Evaluar su contexto  
3. Decidir si es:  
   - Falso positivo  
   - Low severity  
   - Medium severity  
   - High / Critical  
4. Tomar acción inmediata o escalar  

Es la función MÁS constante de un SOC I.

---

# 🧩 2. Ejemplo de alertas recibidas (caso simulado)

Supongamos que el SIEM genera estas 5 alertas en 1 minuto:

### 1️⃣ Alerta: Login fallido (usuario: Ana.P)
- 3 intentos fallidos desde IP interna
- Contexto: usuario tipea mal la contraseña

### 2️⃣ Alerta: Anomalía de tráfico saliente
- 1.2GB enviados a IP desconocida

### 3️⃣ Alerta: Antivirus detectó archivo eliminado
- AV removió virus correctamente

### 4️⃣ Alerta: PowerShell ejecutado con parámetros sospechosos
- `powershell.exe -nop -w hidden -enc ...`

### 5️⃣ Alerta: Mala reputación de dominio accedido
- Usuario navegó a un sitio sospechoso

Un SOC I debe decidir cuál atender primero.

---

# 🧠 3. Priorización (cómo piensa un analista real)

Se clasifica así:

---

## 🔴 **CRITICAL — Acción inmediata**
### 🔹 Alerta 2 — Exfiltración de 1.2GB  
Razón:
- tráfico saliente anómalo  
- gran volumen  
- posible C2 o data theft  

### 🔹 Alerta 4 — PowerShell malicioso  
Razón:
- parámetros típicos de malware  
- posible explotación o persistence  

👉 Estas requieren **respuesta inmediata**.

---

## 🟠 **HIGH — Riesgo alto pero no inmediato**
### 🔹 Alerta 5 — Dominio malicioso  
Puede indicar:
- phishing  
- malware download  
- infección inicial  

Debe investigarse rápido.

---

## 🟡 **MEDIUM — Revisar con calma**
### 🔹 Alerta 1 — Login fallido  
Podría ser:
- usuario tecleando mal  
- brute force interno  

Se revisa comportamiento del usuario.

---

## 🟢 **LOW — No requiere acción**
### 🔹 Alerta 3 — Antivirus actuó automáticamente  
Sistema ya mitigó la amenaza.

---

# 📊 4. Tabla de Triage Final

| Alerta | Severidad | Acción |
|--------|-----------|--------|
| 1. Login fallido | Medium | Revisar logs, validar comportamiento |
| 2. Exfiltración | **Critical** | Aislar host, bloquear IP, investigar |
| 3. Antivirus | Low | Documentar, sin acción |
| 4. PowerShell malicioso | **Critical** | Aislar host, revisar procesos |
| 5. Dominio malicioso | High | Investigar, preguntar al usuario |

---

# 🏁 5. Conclusión del triage
Las alertas críticas se relacionan con:
- exfiltración de datos  
- ejecución sospechosa vía PowerShell  

Ambas representan compromiso directo del sistema y requieren acción inmediata.

El resto se maneja como advertencias o hallazgos de menor riesgo.

---

# 🧭 6. Beneficio en SOC real
Dominar Alert Triage permite:

- reducir ruido  
- responder rápido  
- priorizar amenazas reales  
- mejorar tiempos de contención  
- no perder ataques importantes entre falsos positivos  

Es una de las habilidades esenciales para aprobar entrevistas SOC.

