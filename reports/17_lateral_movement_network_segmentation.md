# 🛡️ Reporte 17 — Lateral Movement in Segmented Networks (VLAN, DMZ, Zero Trust)

## 🎯 Objetivo
Describir cómo un atacante intenta moverse lateralmente a través de una red segmentada (VLANs, DMZ, Zero Trust) y cómo un SOC Analyst puede detectarlo mediante logs, anomalías de tráfico y correlación.

---

# 🧠 1. ¿Qué es movimiento lateral?

Es cuando un atacante:
- compromete un punto inicial (PC, cuenta)  
- y luego intenta expandirse a otros sistemas  

Como “saltar de una habitación a otra” dentro de la red.

En redes segmentadas, esto es MUCHO más difícil, por eso se usa segmentation.

---

# 🟦 2. Arquitectura de referencia usada en este reporte

### VLANs:

- **VLAN 10 — Usuarios corporativos**  
- **VLAN 20 — Finanzas (acceso restringido)**  
- **VLAN 30 — Servidores internos**  
- **VLAN 40 — Invitados**  
- **DMZ** — Servidores expuestos a internet

### Zero Trust aplica:
- verificación continua  
- no confiar en nada por defecto  
- acceso mínimo necesario  

---

# 🟥 3. Indicadores típicos de movimiento lateral

## 1️⃣ Tráfico inesperado entre VLANs
Ejemplo real:
- Un equipo de usuario (VLAN 10) intenta conectarse a un servidor de Finanzas (VLAN 20)

## 2️⃣ Escaneo interno
Uso de herramientas:
- nmap  
- netstat  
- comandos para descubrir hosts  
- port scanning lateral  

## 3️⃣ Autenticaciones fallidas repetidas entre máquinas internas
Intentos de:
- RDP  
- SMB  
- SSH  
- WinRM  

## 4️⃣ Uso indebido de credenciales robadas
El atacante usa credenciales válidas para moverse.

## 5️⃣ Acceso a sistemas nunca utilizados antes por ese usuario
Gran señal de compromiso.

---

# 🟧 4. Caso Simulado del Ataque

Usuario inicial comprometido: **sofia.m (VLAN 10)**  
Método de entrada: phishing → token OAuth robado

### Secuencia del ataque:

#### 🔹 1. Escaneo interno (descubrimiento de red)
source: sofia.m workstation
dst: 192.168.20.x (Finance VLAN)
event: port scan detected
ports: 445, 139, 3389

#### 🔹 2. Intentos de autenticación en VLAN 20
Uso fallido de credenciales robadas:
failed kerberos logon attempts: 12
failed SMB logins: 8

#### 🔹 3. Intento de pivoting hacia Servidores Internos (VLAN 30)
blocked connection attempt: VLAN10 → VLAN30
protocol: RDP

#### 🔹 4. División de tráfico hacia DMZ (intento de evasión)
El atacante prueba si algún servidor expuesto está mal configurado:
incoming request from internal host to DMZ webserver
path: /admin
response: 403 forbidden

#### 🔹 5. Comportamiento anómalo detectado por UEBA
UEBA eleva riesgo:

risk score: 92/100
reason:

unusual east-west traffic

high failed authentications

cross-VLAN communications

---

# 🧠 5. Análisis (razonamiento humano — AI-proof)

1. Un usuario común jamás debería estar escaneando Finanzas.  
2. El tráfico cross-VLAN sin permisos es una señal clara de intento de movimiento lateral.  
3. Fallos repetidos de Kerberos y SMB indican intentos de forzar autenticación.  
4. Intentar llegar a VLAN 30 (servidores) es escalada de ataque.  
5. El uso de DMZ como punto de pivoting es técnica avanzada.

Conclusión:
> “El atacante está intentando expandir su presencia dentro de la red, realizando reconocimiento, testing de fronteras entre VLANs y buscando escalar privilegios.”

---

# 🛡️ 6. Acciones recomendadas

1. Aislar el equipo de sofia.m inmediatamente.  
2. Revocar sesiones activas (OAuth/MS Entra ID).  
3. Forzar cambio de contraseña (si aplica).  
4. Revisar logs en las VLAN afectadas.  
5. Revisar dispositivos en VLAN20 y VLAN30 por accesos no autorizados.  
6. Ajustar reglas de firewall internas (lateral movement blocking).  
7. Revisar UEBA para más usuarios afectados.  
8. Revisar posture de Zero Trust y permisos de mínimos privilegios.

---

# 🧭 7. MITRE ATT&CK Mapping

- **T1021 — Remote Services** (RDP, SMB, SSH)  
- **T1046 — Network Service Scanning**  
- **T1086 — PowerShell Execution**  
- **T1049 — System Network Connections Discovery**  
- **T1020 — Data Exfiltration Attempt**  
- **T1078 — Valid Accounts**  

---

# 📝 8. Resumen Ejecutivo

El usuario “sofia.m” muestra actividad consistente con movimiento lateral: escaneo interno, intentos de autenticación cruzada entre VLANs, y tráfico hacia segmentos que no debería tocar. Este comportamiento indica compromiso de cuenta y fase de reconocimiento y expansión por parte del atacante. Se requiere acción inmediata.

