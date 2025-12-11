# 🔐 Security+ — Día 42  
# Network Security & Deep Packet Analysis (explicado fácil)

## 🎯 Objetivo
Aprender los fundamentos de análisis de red que usan SOC, Threat Hunting y EDRs para detectar tráfico sospechoso, exfiltración y C2 (command & control).

---

# 🟥 1. ¿Qué es un “paquete de red”?

Cada vez que tu computadora se comunica con internet, envía y recibe **paquetes**.

Un paquete contiene:
- **origen** (IP origen)  
- **destino** (IP destino)  
- **puerto**  
- **protocolo** (TCP, UDP)  
- **datos** (payload)  

Piensa en un paquete como:
👉 un sobre con remitente, destino y contenido.

---

# 🟧 2. Protocolos comunes y para qué sirven

### 🔸 **HTTP (puerto 80)**
Tráfico web no cifrado.  
Los atacantes lo usan para C2 básico.

### 🔸 **HTTPS (puerto 443)**
Tráfico web cifrado.  
Dificulta ver el contenido, pero aún se ven:
- IP  
- dominio  
- volumen  
- frecuencia  

Los ataques modernos usan HTTPS para ocultarse.

### 🔸 **DNS (puerto 53)**
Traduce nombres (google.com) a IPs.  
Los atacantes usan:
- **DNS tunneling** (exfiltración)  
- dominios recién creados  

### 🔸 **SMB (445)**
Compartición de archivos en Windows.  
Usado para movimiento lateral y ransomware.

### 🔸 **RDP (3389)**
Conexión remota a Windows.  
Es una ruta común de ataque.

---

# 🟨 3. Deep Packet Basics (lo esencial para entrevistas)

Aunque no seas analista de red, necesitas entender:

### ✔ Cabeceras (headers)
Muestran:
- IP origen  
- IP destino  
- puertos  
- protocolo  

### ✔ Payload
El contenido del paquete (a veces cifrado).

### ✔ Flags de TCP
Ayudan a entender conexiones:
- SYN  
- SYN/ACK  
- ACK  
- FIN  
- RST  

Ejemplo:
- muchos SYN sin ACK → **SYN flood attack**  
- conexión normal → SYN → SYN/ACK → ACK  

---

# 🟦 4. Indicadores de tráfico malicioso

### 🔥 **1. Conexiones repetidas a la misma IP desconocida**
→ probable Command & Control (C2)

### 🔥 **2. Tráfico saliendo a horas inusuales**
→ posible exfiltración o actividad del atacante

### 🔥 **3. Mucho tráfico en poco tiempo**
→ ransomware, exfiltración o escaneo

### 🔥 **4. Protocolos inusuales**
Un usuario nunca usa:
- SMB  
- RDP  
- WMI  

Si aparecen → investigar.

### 🔥 **5. DNS sospechoso**
- dominios largos o extraños  
- miles de peticiones DNS  
- dominios recién creados  

Esto puede ser:
→ **DNS tunneling**  
→ **malware comunicándose con su C2**

---

# 🟪 5. Patrones de exfiltración (lo que buscan los hunters)

### 🧩 Patrón común:

1. Archivos comprimidos (zip/rar/7z)  
2. Conexiones salientes a IP rara  
3. Gran volumen de tráfico  
4. Tráfico HTTPS persistente  

Correlación:
- Evento 4688 → proceso zip/rar  
- tráfico saliente → dominio sospechoso  

Si coincide → exfiltración.

---

# 🟫 6. Patrones de C2 (Command & Control)

El malware necesita “hablar” con el atacante.

Indicadores:

- conexiones cada 1–5 minutos  
- tráfico pequeño pero constante  
- a una IP / dominio desconocido  
- a países donde no trabajas  
- user agents raros (“curl/7.55” desde un server Windows)  

MITRE ATT&CK lo clasifica como:
**T1071 – Application Layer Protocol**  
**T1095 – Non-Application Layer Protocol**

---

# 🟩 7. Preguntas típicas de entrevista

### ❓ “¿Cómo detectas C2?”
→ conexiones repetidas a una IP desconocida, tráfico persistente, horarios raros.

### ❓ “¿Cómo detectas exfiltración?”
→ compresión inicial + transferencia grande + destinos sospechosos.

### ❓ “¿Qué protocolo usa DNS?”
→ puerto 53.

### ❓ “¿Por qué HTTPS complica detección?”
→ porque cifra el contenido del paquete.

### ❓ “¿Qué indicador clave detecta ransomware en red?”
→ miles de archivos accedidos/modificados en segundos.

---

# ⭐ Resumen del Día 42

Hoy aprendiste:
- cómo funcionan los paquetes de red  
- qué protocolos ven los analistas  
- cómo detectar C2  
- cómo detectar exfiltración  
- cómo interpretar patrones de tráfico  
- preguntas técnicas típicas  
- conceptos que se usan en SOC II y Threat Hunting  

Este módulo te posiciona en un nivel sólido para roles de seguridad que pagan 90–140k+.
