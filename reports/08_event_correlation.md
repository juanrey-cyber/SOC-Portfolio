# 🛡️ Reporte 08 — Event Correlation (Correlación de Eventos)

## 🎯 Objetivo
Correlacionar múltiples eventos que, combinados, indican un ataque activo dentro del sistema.

---

## 🧩 1. Eventos observados (caso simulado)

Usuario afectado: **Luis.M**

### Evento 1 — Intentos de login fallidos
09:41 3 failed logins from IP 88.134.221.10

### Evento 2 — Login exitoso desde IP distinta
09:43 Login success from IP 185.22.14.90

### Evento 3 — Comportamiento anómalo de procesos
09:45 WINWORD.exe launched PowerShell

### Evento 4 — Conexión saliente sospechosa
09:47 Outbound connection to 45.112.34.2:4444

### Evento 5 — Descarga de archivo malicioso
09:48 File downloaded: payload.ps1

### Evento 6 — Persistencia creada
09:50 New admin account created: support$ (hidden)

---

## 🧠 2. Análisis (razonamiento humano)

- El login fallido seguido de login exitoso desde otra IP → credenciales comprometidas.  
- Word lanzando PowerShell → indicador de malware o macro maliciosa.  
- Conexión a puerto 4444 → puerto clásico de “command and control” (C2).  
- Descarga de payload → malware activo.  
- Creación de usuario admin → persistencia y escalada.

Ninguno de estos eventos por sí solo es claramente un ataque.  
Pero **juntos confirman un compromiso total del sistema**.

---

## 🚨 3. Conclusión

El sistema ha sido comprometido mediante:

1. Robo de credenciales  
2. Ejecución de malware  
3. Comunicación con servidor de comando y control  
4. Descarga de script malicioso  
5. Creación de persistencia administrativa  

Es un incidente de **severidad crítica**.

---

## 🛡️ 4. Acciones de contención recomendadas

1. Aislar la máquina afectada.  
2. Resetear contraseña del usuario.  
3. Revocar tokens activos.  
4. Analizar archivo payload.ps1.  
5. Eliminar usuario admin creado.  
6. Revisar logs de PowerShell y Sysmon.  
7. Validar si hubo exfiltración.

---

## 🧭 5. MITRE ATT&CK

- **T1078 — Valid Accounts**  
- **T1059 — PowerShell Execution**  
- **T1041 — Exfiltration via C2 Channel**  
- **T1136 — Create Account (Persistence)**  

---

## 📝 6. Resumen ejecutivo

Múltiples eventos aparentemente separados revelan un ataque coordinado que incluye compromiso del usuario, ejecución de malware, comunicación con servidor externo y establecimiento de persistencia.  
Este es un ataque activo y requiere respuesta inmediata.


