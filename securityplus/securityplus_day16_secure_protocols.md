# 🔐 Security+ — Día 16  
# Secure Protocols (TLS, HTTPS, SFTP, SSH, DNSSEC, IPSec)

---

# 🧠 1. ¿Qué son “secure protocols”?

Son protocolos que protegen:
- confidencialidad (cifrado)  
- integridad (sin modificación)  
- autenticidad (saber quién es el otro extremo)  

Security+ pregunta mucho cuál usar en cada escenario.

---

# 🟦 2. TLS vs SSL (muy preguntado)

## ❌ SSL → está muerto, inseguro  
- NO se usa  
- No aparece en sistemas modernos

## ✔️ TLS → estándar actual  
- TLS 1.2 ok  
- TLS 1.3 preferido  

Usado en:
- HTTPS  
- FTPS  
- SMTP seguro  
- VPN SSL  

---

# 🟩 3. HTTPS (http + TLS)

Es simplemente HTTP dentro de un túnel TLS.

Protege:
- contraseñas  
- tarjetas  
- comunicación web  

Usa certificados digitales (PKI).

---

# 🟧 4. SSH (Secure Shell)

Usado para:
- administrar servidores  
- conexiones remotas seguras  
- túneles cifrados  

NO es lo mismo que SFTP (pero están relacionados).

---

# 🟫 5. SFTP vs FTPS (muy confundido por estudiantes)

## ✔️ SFTP  
- usa SSH  
- puerto 22  
- seguro por defecto  

## ✔️ FTPS  
- usa TLS  
- puerto 990 o 21  
- parecido a FTP pero seguro  

Security+ casi siempre pregunta la diferencia.

---

# 🟥 6. DNSSEC (DNS Security Extensions)

Protege contra:
- spoofing  
- ataques de manipulación DNS  

Añade **firmas digitales** (integridad).  
No cifra el tráfico → solo verifica autenticidad.

---

# 🟪 7. SMTP, POP3, IMAP seguros

Protocolos de email necesitan cifrado:

- SMTPS = TLS en puerto 465  
- POP3S = TLS en puerto 995  
- IMAPS = TLS en puerto 993  

Muy común en preguntas del examen.

---

# 🔵 8. IPSec (altamente examinable)

Protocolo para VPNs.

Tiene dos modos:

### ⭐ Transport Mode  
- Solo cifra la carga útil  
- Más usado entre hosts internos  

### ⭐ Tunnel Mode  
- Cifra TODO el paquete  
- Usado en VPN site-to-site  

Componentes:

- **AH (Authentication Header)**  
  - integridad + autenticación  
  - NO cifra  

- **ESP (Encapsulating Security Payload)**  
  - integridad + autenticación + cifrado  
  - el más usado  

---

# 🟣 9. LDAPS (LDAP secure)

LDAP = directorio (Active Directory)  
LDAPS = LDAP + TLS (seguro)

---

# 🧠 10. ¿Qué mira SOC en protocolos?

- downgrade attacks (e.g., TLS → SSL)  
- tráfico a puertos inseguros  
- uso de protocolos raros no autorizados  
- conexiones SSH sospechosas  
- uso incorrecto de tunneling  
- certificados inválidos  
- dominio manipulados por falta de DNSSEC  

---

# 📝 11. Mini-práctica (Security+ Style)

**1. ¿Qué reemplaza SSL?**  
➡️ TLS

---

**2. ¿Qué protocolo usa SSH para transferir archivos?**  
➡️ SFTP

---

**3. ¿Qué modo IPSec cifra TODO el paquete?**  
➡️ Tunnel Mode

---

**4. ¿Qué agrega DNSSEC?**  
➡️ Firmas digitales (integridad)

---

# ⭐ 12. Resumen Final

- TLS = estándar moderno  
- HTTPS = HTTP + TLS  
- SSH = administración segura  
- SFTP = archivos por SSH  
- FTPS = archivos por TLS  
- IPSec → transport vs tunnel  
- DNSSEC → autenticidad e integridad del DNS  

