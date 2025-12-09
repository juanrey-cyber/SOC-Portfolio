# 🔐 Security+ — Día 31  
# Authentication, Authorization & Federation (IAM Deep)

## 🎯 Objetivo
Comprender cómo funciona la autenticación moderna, SSO, federación, MFA, biometría, OAuth, OIDC y SAML de forma simple, clara y útil para entrevistas y Security+.

---

# 🟥 1. Conceptos base: AAA

## 🔸 Authentication  
Verifica **quién eres**.  
Ejemplo: contraseña, biometría, MFA.

## 🔸 Authorization  
Define **qué puedes hacer**.  
Ejemplo: permisos, roles, access control.

## 🔸 Accounting  
Registra **qué hiciste**.  
Ejemplo: logs, auditoría.

---

# 🟧 2. FAR — Methods of Authentication  
(Security+ lo pregunta MUCHO)

Authentication = “probar identidad”.

### ✔ Algo que sabes  
- contraseña  
- PIN  

### ✔ Algo que tienes  
- token  
- smartphone  
- tarjeta inteligente  

### ✔ Algo que eres  
- biometría (huella, rostro, iris)

### ✔ Algo que haces  
- patrón de tecleo  
- comportamiento  

### ✔ Lugar donde estás  
- geolocalización  
- IP  

**MFA = 2 factores de categorías diferentes.**  
Contraseña + huella = MFA  
Contraseña + PIN = NO MFA (mismo tipo)

---

# 🟨 3. Passwordless Authentication (moderno)

Ejemplos:
- biometría  
- llaves FIDO2  
- tokens hardware (YubiKey)  
- certificados  

Ventajas:
- No hay contraseñas que robar  
- Previene phishing  
- Más seguro que MFA tradicional

---

# 🟪 4. Federation (clave para entrevistas)

**Federation = confianza entre sistemas/empresas para que el usuario no tenga que autenticarse varias veces.**

Ejemplo real:
- Te logeas en Google  
- Entras a YouTube, Gmail, Drive sin login adicional  

Federación se logra con:
- SAML  
- OAuth 2.0  
- OIDC  

---

# 🟦 5. SSO — Single Sign-On

**Una sesión = acceso a múltiples aplicaciones.**

Ejemplos:
- Microsoft 365  
- Google Workspace  
- Okta  

SSO no significa que no haya autenticación, sino que se **reutiliza**.

---

# 🟩 6. SAML (explicado fácil y didáctico)

SAML = Security Assertion Markup Language  
Usado en empresas.

Flujo simplificado:

1. Usuario intenta entrar al servicio (SP - Service Provider).  
2. SP lo manda al IdP (Identity Provider).  
3. IdP autentica (contraseña, MFA).  
4. IdP envía una **assertion SAML** firmada digitalmente al SP.  
5. SP confía y deja pasar.

Claves:
- XML  
- Enterprise  
- SSO clásico  

Security+:  
➡️ IdP autentica y envía la assertion.

---

# 🟫 7. OAuth 2.0 (autorización moderna)

**OAuth = autorización, NO autenticación.**

Ejemplo super común:
“Este sitio quiere acceder a tu correo de Google.”

Flujo:

1. El usuario permite acceso.  
2. El sitio recibe un **access token**.  
3. Puede acceder a datos según permisos.

Grant types (simplificado para Security+):
- Authorization Code (más seguro)  
- Device Code  
- Client Credentials  

---

# 🟧 8. OIDC — OpenID Connect (añade autenticación a OAuth)

OAuth = autorización  
OIDC = autenticación + OAuth

OIDC usa:
- **ID token** (quién eres)  
- **Access token** (qué puedes hacer)

Preguntas típicas:
- “¿Cuál protocolo provee autenticación moderna sobre OAuth 2.0?” → **OIDC**
- “¿Cuál usa ID tokens?” → OIDC

---

# 🟩 9. Certificate-Based Authentication

El usuario se identifica con un **certificado digital**.

Ventajas:
- no hay contraseñas  
- muy seguro  
- común en empresas y VPNs  

---

# 🟦 10. Biometrics (muy preguntado)

Tipos:
- huella  
- iris  
- rostro  
- patrón de venas  

Fallos importantes (Security+):
- FMR = False Match Rate  
- FNMR = False Non-Match Rate  
- CER = Crossover Error Rate (punto donde FMR = FNMR) → calidad del sistema

---

# 🟨 11. Risk-Based Authentication (moderno)

Ejemplo:
- Si entras desde Miami, te deja pasar.  
- Si entras desde Rusia, te pide MFA.  
- Si entras desde una máquina nueva, alerta.

Factores:
- ubicación  
- dispositivo  
- comportamiento  

---

# 🟫 12. Mini-práctica tipo Security+

**1. ¿Cuál protocolo corporativo usa assertions XML para SSO?**  
→ SAML

**2. ¿Cuál protocolo añade autenticación a OAuth?**  
→ OIDC

**3. ¿Qué método elimina contraseñas por completo?**  
→ Passwordless / FIDO2 / Certificados

**4. ¿Qué mide CER?**  
→ Punto donde falso positivo = falso negativo en biometría

**5. ¿Qué componente autentica en SAML?**  
→ IdP (Identity Provider)

---

# ⭐ Resumen Final
Aprendiste:
- Autenticación moderna  
- MFA correcto  
- Passwordless  
- SSO  
- Federation  
- SAML  
- OAuth  
- OIDC  
- Certificates  
- Biometrics  
- Autenticación basada en riesgo  

Este módulo es CRÍTICO para Security+ y para entrevistas bien pagadas.

