# 🔐 Security+ — Día 37  
# Correlación de Ataques + Kill Chain (modelos reales usados en SOC & Threat Hunting)

## 🎯 Objetivo
Aprender cómo correlacionar eventos para identificar patrones de ataque.  
Esto es CRÍTICO para:
- entrevistar en SOC II  
- entrar a Threat Hunting Jr  
- detectar ataques reales  
- resolver incidentes  
- determinar si un evento aislado importa o no  

Aquí pasamos de “saber logs” a **pensar como investigador**.

---

# 🟥 1. ¿Qué es correlación de ataques?

La correlación significa:
### 👉 Conectar múltiples eventos para ver si juntos forman un ataque.

Un evento aislado puede ser normal.  
Pero varios juntos pueden ser un patrón MUY sospechoso.

Ejemplo:
- 4625 → intentos fallidos  
- 4624 → login exitoso  
- 4672 → privilegios  
- 4688 → proceso extraño  

Separados, no dicen mucho.  
Juntos → ataque claro.

---

# 🟧 2. Modelo Kill Chain (explicación fácil)

La “Kill Chain” describe las fases típicas de un ataque:

### 1) **Reconnaissance**  
El atacante investiga a la víctima.  
Ejemplo:
- escaneo de puertos  
- intento de identificar servicios  

### 2) **Weaponization**  
Crea la herramienta/malware.

### 3) **Delivery**  
Envía el ataque.  
Ejemplo:
- phishing  
- enlace malicioso  
- descarga del payload  

### 4) **Exploitation**  
Explota una vulnerabilidad.

### 5) **Installation**  
Instala malware/persistencia.

### 6) **Command & Control**  
La máquina empieza a hablar con el servidor del atacante.

### 7) **Actions on Objectives**  
Lo que quieren hacer:
- robar datos  
- moverse lateralmente  
- ransomware  

---

# 🟨 3. Correlaciones más comunes que se ven en SOC / Threat Hunting

### 🔸 **Patrón 1 — Fuerza Bruta Exitosa**
1. Muchos **4625** (logon fallido)  
2. Un **4624** (logon exitoso)  
3. Luego actividad anómala  
   - 4672  
   - 4688  
   - conexiones remotas  

Este patrón es clásico de compromisos.

---

### 🔸 **Patrón 2 — Escalación de privilegios**
1. 4624  
2. 4672 (privilegios especiales)  
3. 4688 ejecutando herramientas administrativas  
   - `cmd.exe`  
   - `powershell.exe`  
   - `whoami /priv`  

La pregunta clave:  
**¿Por qué este usuario está elevando privilegios?**

---

### 🔸 **Patrón 3 — Persistencia**
Buscamos evidencia de que el atacante quiere quedarse:

- servicios nuevos  
- claves Run  
- tareas programadas  
- scripts en Startup  

Preguntas típicas:
- ¿Se creó un servicio después de un proceso sospechoso?  
- ¿Hay tareas que antes no existían?  

---

### 🔸 **Patrón 4 — Movimiento lateral**
Eventos que indican que el atacante pasó a otra máquina:

- conexiones RDP inesperadas  
- uso de `wmic`, `psexec`  
- logs de autenticación remota en otros hosts  

Suele acompañarse de:
- 4624 tipo 10 (remote)  
- escaneos internos  

---

### 🔸 **Patrón 5 — Exfiltración**
Indicadores:

- procesos comprimiendo archivos (`rar`, `zip`)  
- conexiones salientes grandes a IPs desconocidas  
- tráfico HTTPS inusual  
- actividad fuera de horario  

---

# 🟦 4. Cómo correlacionar como profesional

Cada evento responde una pregunta:

### 1) **¿Inicio de sesión raro?**  
4625 → 4624 → 4672

### 2) **¿Qué ejecutó después?**  
Revisar 4688

### 3) **¿Se movió a otra máquina?**  
Revisar RDP / WinRM

### 4) **¿Instaló persistencia?**  
Revisar servicios, tareas programadas, Run keys

### 5) **¿Robó datos?**  
Buscar compresión, transferencias, C2

Esto te convierte en hunter.

---

# 🟪 5. Preguntas típicas de entrevista sobre correlación

### ❓ “¿Cómo detectarías un ataque de fuerza bruta exitoso?”
Explicar:
- 4625 repetidos  
- 4624 exitoso  
- actividad posterior (privilegios o procesos)

### ❓ “¿Cómo sabes si hubo escalación de privilegios?”
→ Evento 4672 + procesos administrativos

### ❓ “¿Qué indica movimiento lateral?”
→ Conexiones RDP inesperadas, uso de WMI o PSExec.

### ❓ “¿Cómo detectas persistencia?”
→ servicios nuevos, claves Run, tareas programadas

### ❓ “¿Por qué es peligrosa la secuencia 4624 → 4672 → 4688?”
→ Es ejecución privilegiada posterior al acceso.

---

# ⭐ Resumen del Día 37

Hoy aprendiste:
- qué es correlación de ataques  
- cómo conectar eventos para ver un patrón  
- el modelo Kill Chain  
- patrones profesionales de ataque  
- cómo identificar fuerza bruta, escalación, persistencia, exfiltración  
- cómo responder preguntas técnicas reales  

Este módulo te acerca directamente a roles:
- Threat Hunter Jr  
- DFIR Jr  
- Detection Engineer Jr  
- SOC II  

y aumenta exponencialmente tu valor en entrevistas.
