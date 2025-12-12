# 🔐 Security+ — Día 47  
# Log Analysis Avanzado: Windows Event Logs (explicado como humano)

## 🎯 Objetivo
Aprender a interpretar los eventos más importantes del registro de Windows para SOC, Threat Hunting y DFIR.  
Los mismos logs aparecen en Splunk, Sentinel, Elastic y CrowdStrike.

---

# 🟥 1. ¿Por qué es tan importante Windows Event Log?

Porque Windows es el objetivo principal de:
- ransomware  
- phishing  
- movimiento lateral  
- escalación de privilegios  
- persistencia  

Los atacantes dejan rastros.  
Tú aprendes a encontrarlos.

---

# 🟧 2. Categorías principales de logs

Windows agrupa eventos en:

1. **Security** → autenticación, permisos, accesos  
2. **System** → servicios, drivers, apagados  
3. **Application** → fallas, apps, comportamiento  
4. **PowerShell** → scripts ejecutados  
5. **Sysmon** (si está instalado) → visibilidad avanzada

Como analista SOC, el 90% del tiempo miras:
- Security  
- PowerShell  
- Sysmon  

---

# 🟨 3. Eventos críticos de autenticación (Security Log)

Estos son los eventos que DEBES conocer:

### 🔸 (4624) Logon exitoso  
Muestra:
- tipo de logon  
- usuario  
- origen  

Los **tipos de logon** son clave:

- **Type 2**: interactivo (teclado)  
- **Type 3**: red  
- **Type 7**: desbloqueo de pantalla  
- **Type 10**: RDP (muy importante)  
- **Type 11**: cached logon  

### Señal SOC:

Si ves **Logon Type 10** → posible RDP.  
Si ocurre a horas raras → investigar.

---

### 🔸 (4625) Logon fallido  
Intentos fallidos de login.

Patrones:
- muchos fallos en poco tiempo → fuerza bruta  
- intentos desde IP interna inesperada → movimiento lateral  

---

### 🔸 (4634) Logoff  
Indica fin de sesión.  
Ayuda a ver quién estuvo activo.

---

### 🔸 (4648) Logon explícito  
Cuando un usuario usa “Run as other user”.

SOC lo investiga si:
- ocurre en horas raras  
- lo hace un usuario que nunca lo hace  

---

# 🟦 4. Eventos de privilegios y cuentas

### 🔸 (4670) Change permissions  
Cambios sospechosos de permisos.

### 🔸 (4672) Special privileges assigned  
Indica que una cuenta con privilegios especiales (como administrador) inició sesión.

Señal SOC:
- si ocurre con una cuenta que NO debería tener privilegios  
- o en horas inusuales  

---

# 🟪 5. Eventos de PowerShell (MUY importantes)

PowerShell es la herramienta favorita de los atacantes.

Eventos a vigilar:

### 🔸 Event ID 4103  
Comandos ejecutados.

### 🔸 Event ID 4104  
Bloques de código ejecutados (ScriptBlock).

Señales de ataque:
- uso de keywords como: download, invoke, base64  
- ejecución desde TEMP o AppData  
- uso de bypass (`ExecutionPolicy Bypass`)  

---

# 🟥 6. Sysmon Essentials (si está instalado)

Sysmon da visibilidad profesional.

Eventos clave:

### 🔸 Event ID 1 — Process Creation  
Muestra:
- proceso  
- línea de comando  
- hash  
- parent process  

Señales:
- cmd.exe o powershell.exe lanzados por Word/Excel  
- ejecución desde TEMP/AppData  
- uso de parámetros sospechosos  

---

### 🔸 Event ID 3 — Network Connection  
Muestra conexiones salientes.

Señales:
- conexión repetitiva a IP desconocida → C2  
- tráfico a otro país  
- puertos raros  

---

### 🔸 Event ID 7 — DLL Loaded  
Ayuda en detección de malware fileless.

---

### 🔸 Event ID 10 — Process Access  
Ejemplo: acceso no autorizado a LSASS → intento de robo de credenciales.

---

### 🔸 Event ID 11 — File Created  
Detecta:
- creación masiva de archivos → ransomware  
- dumps de memoria  
- malware escribiendo payloads  

---

# 🟫 7. Casos reales de detección

### 🔥 Caso 1: Fuerza bruta  
Muchos 4625 seguidos → luego 4624 → ALERTA.

### 🔥 Caso 2: RDP sospechoso  
4624 Type 10 desde IP interna rara.

### 🔥 Caso 3: Movimiento lateral  
- 4624 Type 3  
- seguido de creación de servicios o WMI  

### 🔥 Caso 4: C2  
Sysmon 3 → múltiples conexiones salientes pequeñas y constantes.

### 🔥 Caso 5: PowerShell malicioso  
4104 con comandos codificados en base64.

---

# 🟩 8. Preguntas típicas de entrevista

¿Qué evento indica login exitoso?
→ 4624

¿Qué tipo de logon es RDP?
→ Type 10

¿Qué evento indica login fallido?
→ 4625

¿Qué evento muestra comandos de PowerShell?
→ 4103 / 4104

¿Cómo detectas C2?
→ Sysmon 3 con conexiones repetidas a IP desconocida.

---

# ⭐ Resumen del Día 47

Aprendiste:
- cómo leer los eventos Windows clave  
- cómo detectar logon sospechoso  
- cómo identificar movimiento lateral  
- cómo detectar PowerShell malicioso  
- cómo se ven indicadores de C2  
- qué preguntar en entrevistas  
