# 🔐 Security+ — Día 29  
# Network Security, Protocol Hardening & Secure Network Design

## 🎯 Objetivo
Aprender cómo proteger redes, protocolos, dispositivos y arquitecturas. Este es uno de los tópicos más grandes del examen y muy usado en entrevistas SOC.

---

# 🟥 1. Network Segmentation

Separar la red en porciones más pequeñas para limitar ataques.

Ejemplos:
- VLANs  
- DMZ  
- Guest network  
- Management network  
- OT/ICS networks separadas  

### Beneficios:
- menos superficie de ataque  
- contención  
- monitoreo más simple  

Security+:  
➡️ “Segmentation limita el movimiento lateral”.

---

# 🟧 2. Firewalls (configuración y tipos)

## 🔸 Packet Filtering Firewall
Filtra por:  
- IP  
- puerto  
- protocolo  

Simple pero limitado.

---

## 🔸 Stateful Firewall
Recuerda conexiones activas.  
Más seguro que un firewall básico.

---

## 🔸 NGFW — Next-Gen Firewall
Funciones avanzadas:
- inspección profunda (DPI)  
- detección de aplicaciones  
- bloqueo de malware  
- reglas basadas en identidad  

Security+:  
➡️ NGFW = capa 7 + inspección avanzada.

---

# 🟨 3. IDS / IPS (detección vs prevención)

## 🔸 IDS — Intrusion Detection System
- detecta ataques  
- alerta  
- NO bloquea  

---

## 🔸 IPS — Intrusion Prevention System
- detecta  
- **bloquea automáticamente**  

Security+:  
➡️ IPS = inline, IDS = out-of-band.

---

# 🟦 4. Protocol Hardening (actualización MUY importante)

## 🔸 Protocolos inseguros → reemplazos seguros

| Inseguro | Seguro | Explicación |
|---------|--------|-------------|
| HTTP | HTTPS | TLS encriptado |
| FTP | SFTP / FTPS | Seguridad en transferencia de archivos |
| Telnet | SSH | Admin seguro |
| SMTP simple | SMTPS | Correo cifrado |
| SNMPv1/v2 | SNMPv3 | Autenticación + cifrado |
| LDAP simple | LDAPS | Cifrado TLS |

Security+:  
➡️ “SNMPv3 es la versión segura”  
➡️ “SSH reemplaza Telnet”

---

# 🟪 5. Wireless Security (resumen reforzado)

## 🔸 WPA3 (más seguro)
- SAE handshake  
- resistente a ataques offline  

---

## 🔸 WPA2 (aún común)
- PSK o Enterprise  
- AES es seguro  
- TKIP NO es seguro → vulnerable

---

## 🔸 Open Wi-Fi
SIN cifrado. Nunca usar.

---

## 🔸 Captive Portals
No proveen cifrado → solo control de acceso.

---

# 🟩 6. Network Access Control (NAC)

Verifica:
- identidad  
- estado del dispositivo (posture check)  
- cumplimiento de políticas  

Permite:
- bloquear  
- poner en cuarentena  
- dar acceso limitado  

Security+:  
➡️ NAC = control antes de entrar a la red.

---

# 🟫 7. VPN Security

## 🔸 Site-to-site VPN
Conecta dos redes completas.

## 🔸 Remote Access VPN
Para empleados externos.

Protocolos seguros:
- IPsec  
- SSL/TLS VPN (más flexible)  

---

## 🔸 Split Tunnel vs Full Tunnel

### Split Tunnel:
- Solo tráfico corporativo va por VPN  
- Resto del tráfico va directo a internet  
- Más rápido, pero menos seguro  

### Full Tunnel:
- TODO el tráfico pasa por VPN  
- Más seguro  
- Más consumo de ancho de banda  

Security+:  
➡️ Full tunnel = seguridad máxima.

---

# 🟥 8. Network Devices Security

## 🔸 Switches
- Port security  
- Disable unused ports  
- 802.1X (autenticación)  
- Storm control  

---

## 🔸 Routers
- ACL (Access Control Lists)  
- Filtrar tráfico  
- Hardening (no servicios innecesarios)

---

## 🔸 Load Balancers
Tipos:
- Round robin  
- Least connections  
- Layer 4/7  

Beneficios:
- distribución de carga  
- disponibilidad  
- resistencia a ataques  

---

# 🟦 9. DNS Security (muy preguntado)

Problemas:
- DNS poisoning  
- DNS spoofing  
- Secuestro DNS  

Mitigación:
- DNSSEC  
- Validación de firmas  
- DoH (DNS over HTTPS)  
- DoT (DNS over TLS)

---

# 🟩 10. Secure Network Architecture

Incluye:
- Air gaps  
- Jump servers  
- Bastion hosts  
- Reverse proxies  
- DMZ  
- Zero Trust Network Access (ZTNA)  

Security+:  
➡️ Jump servers limitan acceso a redes internas críticas.  
➡️ DMZ = área expuesta pero controlada.

---

# 📝 11. Mini-Práctica tipo Security+

**1. ¿Qué reemplaza Telnet?**  
→ SSH

**2. ¿Qué versión de SNMP es segura?**  
→ SNMPv3

**3. ¿Cuál opción limita movimiento lateral?**  
→ Network segmentation

**4. ¿IDS o IPS bloquea ataques?**  
→ IPS

**5. ¿Qué túnel VPN es más seguro?**  
→ Full Tunnel

---

# ⭐ Resumen Final

Hoy aprendiste:
- Segmentación  
- Firewalls clásicos vs NGFW  
- IDS vs IPS  
- Protocol hardening (FTP→SFTP, HTTP→HTTPS, etc.)  
- Wireless security actualizado  
- NAC  
- VPNs (full/split)  
- Switch/Router security  
- DNS security  
- Zero Trust & DMZ

Este módulo es crítico para Security+ y SOC.

