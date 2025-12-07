# 🔐 Security+ — Día 24  
# AAA, Identity, Authentication, SSO, Federation, OAuth, Kerberos, SAML

## 🎯 Objetivo
Dominar los sistemas modernos de identidad: autenticación, autorización, tokens, SSO, Kerberos, OAuth, federación y protocolos usados en empresas y nubes. Este contenido es ultra importante en Security+ y en SOC real.

---

# 🟥 1. AAA — Authentication, Authorization, Accounting

## ✔ Authentication — ¿Quién eres?
Ejemplos:
- contraseña  
- MFA  
- biometría  
- tokens  

## ✔ Authorization — ¿Qué puedes hacer?
Ej:
- permisos  
- roles (RBAC)  
- políticas IAM  

## ✔ Accounting — Auditoría
Registra:
- accesos  
- cambios  
- acciones de usuario  

SIEM usa mucho esta parte.

---

# 🟦 2. Factor Types (Tipos de autenticación)

## 🔸 Something you KNOW  
Contraseña, PIN

## 🔸 Something you HAVE  
Token, teléfono, llave FIDO

## 🔸 Something you ARE  
Biometría

## 🔸 Somewhere you ARE  
Ubicación geográfica

**MFA = 2 o más factores.**

---

# 🟧 3. SSO — Single Sign-On

Un usuario inicia sesión **una sola vez** y accede a múltiples aplicaciones.

Ejemplos:
- Google  
- Microsoft Entra ID (Azure AD)  
- Okta  

SSO depende de **tokens**, no de contraseñas repetidas.

---

# 🟫 4. Kerberos — Autenticación interna en Active Directory

Usado en:
- entornos Windows  
- servidores corporativos  
- autenticación interna de empresas  

Conceptos clave:

### ✔ KDC — Key Distribution Center  
Servidor que maneja autenticaciones.

### ✔ TGT — Ticket Granting Ticket  
Lo que obtienes al autenticarte.

### ✔ Service Ticket  
Permite acceder a servicios (archivos, impresoras, apps).

### ✔ Característica clave  
**Autenticación mutua**: cliente y servidor se verifican.

---

# 🟩 5. Federation (identidad federada)

Permite que una organización confíe en otra para autenticar usuarios.

Ejemplo:
- Iniciar sesión en Slack usando tu cuenta de Google.  
- Empresa A inicia sesión en Empresa B sin crear cuentas nuevas.

Federación = confianza entre dominios.

---

# 🟪 6. SAML — Security Assertion Markup Language (XML)

Usado para:
- SSO basado en navegador  
- Integración con aplicaciones empresariales  

Componentes:
- **IdP** — Identity Provider (Okta, Google, Azure)  
- **SP** — Service Provider (Salesforce, AWS, etc.)  

SAML Assertions = los mensajes que contienen credenciales.

---

# 🟦 7. OAuth 2.0 — Autorización moderna

MUY usado en apps móviles y web.

Ejemplos:
- “Iniciar sesión con Google”  
- “Conectar con Spotify”  

Importante:
- OAuth = autorización, **NO autenticación**  
- Otorga permisos a apps sin compartir contraseña  

Roles clave:
- Resource Owner (usuario)  
- Client (aplicación)  
- Authorization Server  
- Resource Server  

---

# 🟨 8. OpenID Connect (OIDC)

Extensión de OAuth 2.0 que **sí provee autenticación**.

Se usa en:
- Google Login  
- Apple Sign-In  
- Microsoft / Azure AD  

Tokens importantes:
- **ID Token** (quién eres)  
- **Access Token** (qué puedes hacer)  
- **Refresh Token** (para renovar acceso)

---

# 🟫 9. Directory Services

## 🔸 LDAP
Protocolo para consultar directorios de usuarios.  
Versión segura: **LDAPS**.

## 🔸 RADIUS
Autenticación remota.  
Usado en:
- Wi-Fi Empresarial  
- VPNs  
- NAC  

## 🔸 TACACS+
Más granular que RADIUS.  
Usado para admins de red.

---

# 🟥 10. Common Attacks Against Identity

## 🔸 Password Spraying
Pocas contraseñas → muchas cuentas.

## 🔸 Credential Stuffing
Usar credenciales filtradas.

## 🔸 MFA Fatigue
Bombardeo de notificaciones hasta que el usuario aprueba.

## 🔸 Token Theft (moderno)
Robar sesiones de:
- OAuth  
- cookies  
- tokens JWT  

Muchos incidentes reales comienzan así.

---

# 🧭 11. Qué mira SOC en Identity

SOC analiza:
- inicios de sesión anómalos  
- MFA bypass  
- accesos desde países inusuales  
- sesión sin autenticación (token replay)  
- fallos masivos de login  
- creación sospechosa de tokens OAuth  
- aplicaciones no autorizadas  

El 80% de ataques modernos → identidad.

---

# 📝 12. Mini-Práctica

**1. ¿Qué protocolo provee SSO en aplicaciones web empresariales?**  
➡️ SAML

**2. ¿Qué protocolo se usa para autorización moderna en apps móviles?**  
➡️ OAuth 2.0

**3. ¿Qué añade autenticación encima de OAuth?**  
➡️ OIDC (OpenID Connect)

**4. ¿Qué servicio maneja tickets en Kerberos?**  
➡️ KDC

**5. ¿Qué modelo define “quién eres”?**  
➡️ Autenticación

---

# ⭐ Resumen Final
- AAA: quién eres, qué puedes hacer, qué hiciste  
- Kerberos = tickets, AD, autenticación mutua  
- SAML = SSO empresarial basado en navegador  
- OAuth = autorización (sin contraseña)  
- OIDC = autenticación moderna  
- Federation = confianza entre entidades  
- Identidad es el corazón de seguridad moderna  
