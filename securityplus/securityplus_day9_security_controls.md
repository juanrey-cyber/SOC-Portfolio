# 🔐 Security+ — Día 9  
# Honeypots, NAC, WAF, DLP — Controles de Seguridad (Nivel A)

---

# 🧠 1. Honeypots (Trampa para atacantes)

Un **honeypot** es un sistema falso diseñado para:

- atraer atacantes,  
- registrar su comportamiento,  
- detectarlos temprano.

No contiene datos reales.  
Si alguien entra → automáticamente es sospechoso.

Tipos:
- Honeypot simple (servidor falso)  
- Honeynet (varios sistemas falsos)  

Beneficios:
- detectar actividad maliciosa  
- estudiar patrones de ataque  
- alertar sobre intrusiones reales

---

# 🟦 2. NAC — Network Access Control

NAC = sistema que **decide si un dispositivo puede entrar a la red**.

Funciona como un “portero inteligente”.

Ejemplos de reglas NAC:
- ¿El PC tiene antivirus actualizado?  
- ¿El usuario pasó MFA?  
- ¿El dispositivo es corporativo o personal?  

Si falla → NO entra a la red.

Modos:
- **Pre-admission**: antes de entrar.  
- **Post-admission**: monitoreo continuo.

Muy usado en empresas modernas.

---

# 🟥 3. WAF — Web Application Firewall

WAF = firewall diseñado específicamente para **proteger aplicaciones web**.

Bloquea ataques como:
- SQL Injection  
- XSS  
- CSRF  
- LFI / RFI  
- ataques a APIs  

Ejemplo real:
AWS WAF, Cloudflare WAF, Azure WAF.

Mientras un firewall normal protege “puertos”,  
un WAF protege **las solicitudes web y parámetros**.

---

# 🟩 4. DLP — Data Loss Prevention

DLP = sistemas que evitan que los datos salgan donde no deben.

Protegen:
- datos sensibles  
- archivos confidenciales  
- PII / PHI / tarjetas

Detectan y bloquean:
- enviar datos por email  
- copiar a USB  
- subir archivos a la nube  
- imprimir documentos sensibles  

Tipos:
- **Endpoint DLP**  
- **Network DLP**  
- **Cloud DLP**

Ejemplos:
- Microsoft Purview  
- Symantec DLP  

---

# 🟫 5. CASB — Cloud Access Security Broker (importante para roles bien pagados)

CASB controla y monitorea:
- uso de aplicaciones cloud  
- políticas de acceso  
- riesgos de cuentas  
- tráfico hacia servicios SaaS  

Ejemplo:
Microsoft Defender for Cloud Apps.

---

# 🧠 6. Cómo usa esto un SOC Analyst

- Honeypots alertan actividad temprana.  
- NAC bloquea dispositivos no confiables.  
- WAF genera alertas de ataques web.  
- DLP detecta exfiltración de datos.  
- CASB muestra riesgos en aplicaciones cloud (muy usado hoy).  

Muchos roles SOC modernos combinan SIEM con DLP, CASB y WAF.

---

# 📝 7. Mini-Práctica Security+ Style

**1. Un sistema falso que atrae atacantes es:**  
A) WAF  
B) Honeypot  
C) CASB  
➡️ **B**

---

**2. Un sistema que controla quién entra a la red es:**  
A) NAC  
B) DLP  
C) SIEM  
➡️ **A**

---

**3. ¿Cuál protege aplicaciones web contra SQL injection?**  
A) WAF  
B) Firewall tradicional  
C) VPN  
➡️ **A**

---

**4. ¿Cuál evita que datos sensibles salgan de la empresa?**  
A) NAC  
B) IDS  
C) DLP  
➡️ **C**

---

# ⭐ 8. Resumen en una línea

- **Honeypot** → trampa para atacantes  
- **NAC** → controla acceso a la red  
- **WAF** → protege aplicaciones web  
- **DLP** → evita fuga de datos  
- **CASB** → controla seguridad en la nube

