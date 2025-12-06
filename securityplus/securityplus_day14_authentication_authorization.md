# 🔐 Security+ — Día 14  
# Authentication & Authorization (AAA, RADIUS, TACACS+, SSO, Federation, Tokens)

---

# 🧠 1. ¿Qué es AAA?

AAA = Authentication, Authorization, Accounting

### 1️⃣ Authentication  
"¿Eres quien dices que eres?"

Métodos:
- Contraseña  
- MFA  
- Biométricos  
- Certificados  
- Tokens  

---

### 2️⃣ Authorization  
"¿Qué puedes hacer?"

Ejemplos:
- Leer archivos  
- Acceder a carpetas  
- Usar sistemas específicos  

---

### 3️⃣ Accounting  
Registro de actividades del usuario.

Ejemplos:
- quién se conectó  
- cuándo  
- a qué accedió  
- qué cambios hizo  

---

# 🟦 2. RADIUS vs TACACS+ (muy preguntado en Security+)

## 🔸 RADIUS
- Autenticación + autorización juntas  
- Menos granular  
- UDP  
- Común en Wi-Fi empresarial  
- Más rápido  

---

## 🔸 TACACS+
- Separación de autenticación, autorización y contabilidad  
- Muy granular  
- TCP  
- Usado en administración de dispositivos de red (switches, routers)  
- Más seguro y flexible  

**Resumen para el examen:**  
👉 **TACACS+ = más seguro + más granular**  
👉 **RADIUS = más común para usuarios, Wi-Fi corporativo**

---

# 🟩 3. SSO — Single Sign-On

Permite que el usuario entre una vez y acceda a múltiples aplicaciones.

Ejemplo:
- Entras a tu cuenta Microsoft  
- Ya puedes acceder a Teams, Outlook, SharePoint, OneDrive, etc.

Ventajas:
- Menos passwords  
- Menos fricción  
- Menos riesgo de password reuse  

---

# 🟧 4. Federation (Federación de Identidad)

Permite que dos organizaciones confíen en la identidad del usuario.

Ejemplo real:
- Entras a Airbnb con tu cuenta Google  
- Google “dice” que tú eres tú  
- Airbnb confía en esa autenticación

Tecnologías:
- SAML  
- OAuth  
- OpenID Connect (OIDC)  

---

# 🟥 5. Tokens (muy importante para SOC)

Después de autenticarse, el sistema genera un **token**.

Ese token:
- permite acceso sin volver a logear  
- guarda permisos del usuario  
- puede ser robado si el atacante compromete el navegador

Tipos:
- Access token  
- Refresh token  
- JWT (JSON Web Token)  

SOC debe detectar:
- tokens desde países distintos  
- tokens usados por dispositivos sospechosos  
- tokens de larga duración  
- robo de sesión  

---

# 🟫 6. SAML, OAuth, OIDC (explicado fácil)

## 🔹 SAML — para aplicaciones corporativas  
Se usa mucho en SSO empresarial  
Formato XML  
Ejemplo: iniciar sesión en Salesforce con tu cuenta corporativa

---

## 🔹 OAuth — permisos delegados  
Ejemplo:
- Instagram pide acceso a tu Google Drive (te pide permiso)

---

## 🔹 OIDC — sobre OAuth, pero para autenticación  
Usa JWT  
Es moderno  
Usado en aplicaciones web y móviles  

---

# 🧠 7. ¿Cómo usa esto un SOC Analyst?

SOC mira eventos como:
- inicio de sesión desde países distintos  
- tokens usados demasiado tiempo  
- MFA bypass  
- SAML authentication anomalies  
- OAuth consent grant a apps maliciosas  
- sesión iniciada sin MFA  

También se correlaciona con:
- exfiltración  
- movimientos laterales  
- compromisos cloud  

Esto te vuelve MUY fuerte en roles de Identity Security / Cloud Security.

---

# 📝 8. Mini-práctica (Security+ Style)

**1. ¿Qué diferencia TACACS+ de RADIUS?**  
➡️ TACACS+ separa autenticación, autorización y contabilidad.

---

**2. ¿Qué permite SSO?**  
➡️ Autenticarse una vez y acceder a múltiples recursos.

---

**3. ¿Qué estándar usa muchas apps corporativas para SSO?**  
➡️ SAML.

---

**4. ¿Qué es un refresh token?**  
➡️ Permite obtener nuevos tokens sin relogin.

---

# ⭐ 9. Resumen Final

- AAA = auth + permisos + registro  
- TACACS+ = granular y seguro  
- RADIUS = popular y rápido  
- SSO = login único  
- Federación = otra entidad verifica identidad  
- Tokens son críticos (pueden ser robados)  
- SOC debe vigilar anomalías en autenticación

