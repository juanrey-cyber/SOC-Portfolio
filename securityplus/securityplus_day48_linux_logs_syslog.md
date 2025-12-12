# 🔐 Security+ — Día 48  
# Linux Logs, Syslog & Auth Logs (explicado fácil para SOC y Threat Hunting)

## 🎯 Objetivo
Aprender cómo interpretar logs de Linux: auth.log, syslog, SSH, sudo y actividad del sistema.  
Esto es crítico en SOC, Threat Hunting y Cloud Security porque la mayoría de servidores son Linux.

---

# 🟥 1. ¿Dónde están los logs en Linux?

La gran mayoría está en:
- /var/log/

Los más importantes para SOC:
- /var/log/auth.log (o secure.log en RedHat)
- /var/log/syslog
- /var/log/messages
- /var/log/kern.log

---

# 🟧 2. auth.log / secure.log (EL LOG MÁS IMPORTANTE)

Contiene:
- intentos de login (exitosos y fallidos)
- actividad de SSH
- uso de sudo
- cambios de usuario
- escalación de privilegios

### Ejemplos de líneas típicas:

1) Login FALLIDO por SSH  
"Failed password for invalid user admin from 192.168.1.50 port 50542 ssh2"

Interpretación SOC:
→ ataque de fuerza bruta o recon.

2) Login EXITOSO  
"Accepted password for juan from 10.0.0.22 port 49220 ssh2"

Interpretación SOC:
→ revisar si la IP es esperada.  
→ revisar horario.

3) Uso de sudo (escalación de privilegios)  
"juansudo: TTY=pts/0 ; PWD=/home/juan ; USER=root ; COMMAND=/bin/apt update"

Interpretación SOC:
→ actividad privilegiada → SIEMPRE revisar.

---

# 🟨 3. SSH logs: Claves SOC

SSH es el principal objetivo de ataque en Linux.

### Señales clave:

- Many "Failed password" → brute force  
- "Invalid user" → enumeración de cuentas  
- "Connection closed by authenticating user" → intento fallido automatizado  
- "Accepted publickey" → autenticación por llave  
- Logins desde IP fuera del rango esperado → investigar

---

# 🟦 4. sudo logs (escalación de privilegios)

sudo = ejecutar comandos como root.

Linux registra:
- quién lo usó  
- qué comando ejecutó  
- desde qué terminal  
- a qué usuario escaló  

Señales SOC:
- uso de sudo fuera de horario  
- sudo ejecutado por cuentas que nunca lo usan  
- comandos peligrosos: rm, usermod, chmod 777, etc.

---

# 🟪 5. syslog y messages

Estos logs muestran:
- actividad del sistema  
- servicios que empiezan y se detienen  
- errores críticos  
- actividad sospechosa  

Ejemplos:
- reinicios inesperados  
- servicios caídos  
- procesos fallando repetidamente  
- actividad de red (si no está filtrada)

---

# 🟫 6. Detecciones SOC reales en Linux

### 🔥 Caso 1 — Fuerza bruta SSH
Miles de líneas:
"Failed password for invalid user…"
→ alerta directa.

### 🔥 Caso 2 — Compromiso de cuenta
"Accepted password for juan from IP-rara"
→ revisar movimiento lateral.

### 🔥 Caso 3 — Root escalado con sudo
"juan : TTY... USER=root COMMAND=/bin/bash"
→ posible escalación no autorizada.

### 🔥 Caso 4 — Persistencia
Creación de nuevos usuarios en auth.log:
"useradd: new user ‘backupadmin’"

### 🔥 Caso 5 — Malware / cryptomining
En syslog:
- CPU usage alto  
- servicios manipulados  
- scripts ejecutándose desde /tmp  

---

# 🟩 7. Preguntas típicas de entrevista

¿Qué log contiene intentos de login?
→ auth.log (o secure.log)

¿Cómo detectas fuerza bruta en Linux?
→ múltiples “Failed password”

¿Dónde ves uso de sudo?
→ auth.log

¿Qué indica “Accepted password for user”?
→ login exitoso, revisar origen y horario.

¿Cómo detectas persistencia?
→ creación de usuarios o cambios de sudoers.

---

# ⭐ Resumen Día 48
Aprendiste:
- auth.log: login, SSH, sudo, escalación  
- syslog: servicios y sistema  
- señales de ataque  
- detecciones SOC reales  
- preguntas típicas de entrevista  
