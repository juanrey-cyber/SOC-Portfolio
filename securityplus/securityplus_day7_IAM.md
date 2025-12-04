# 🔐 Security+ — Día 7  
# Identity & Access Management (IAM) — Nivel A, Explicación Simple

---

## 🧠 1. ¿Qué es IAM?
IAM = Identity & Access Management  
Es el sistema que controla:

1. **Quién eres** (identidad)  
2. **Cómo entras** (autenticación)  
3. **Qué puedes hacer** (autorización)  
4. **Qué permisos tienes** (privilegios)  

IAM es la base de toda ciberseguridad empresarial.

---

# 🟦 2. Conceptos ESENCIALES (Security+ y trabajo real)

## 1️⃣ Identidad
Tu “ser digital”: usuario, cuenta o entidad.

Ejemplos:
- juan.rey  
- máquina WIN-102  
- aplicación que usa API keys  

---

## 2️⃣ Autenticación
Proceso de probar quién eres.

Ejemplos:
- contraseña  
- MFA  
- huella digital  
- token físico  

---

## 3️⃣ Autorización
Lo que puedes hacer después de autenticarte.

Ejemplos:
- ver carpetas  
- modificar archivos  
- acceder a bases de datos  
- administrar sistemas  

---

## 4️⃣ Accounting / Auditing (AAA)
Registrar lo que haces.

Sirve para:
- investigar incidentes  
- revisar abuso de permisos  
- detectar movimientos sospechosos  

AAA = Authentication / Authorization / Accounting.

---

# 🟦 3. PRINCIPIOS CRÍTICOS DE SEGURIDAD: “LOS MÁS IMPORTANTES DEL EXAMEN”

## 🔹 Least Privilege (Principio de mínimo privilegio)
Los usuarios solo deben tener **lo mínimo necesario** para hacer su trabajo.

Evita:
- escalada de privilegios  
- abuso de permisos  
- daños accidentales  

Ejemplos:
- Un empleado de marketing NO debería poder ver la nómina.  
- Un usuario normal no debe poder instalar software.

---

## 🔹 Separation of Duties (Separación de funciones)
Una misma persona NO debe tener control total sobre un proceso.

Ejemplos reales:
- Quien crea pagos NO debe ser quien los aprueba.  
- Quien administra usuarios NO debe auditar logs.  

Evita fraude y abuso interno.

---

## 🔹 Rotation of Duties
Rotar tareas entre empleados.

Beneficios:
- reduce riesgos de fraude  
- detecta actividad irregular  
- mejora auditoría  

---

## 🔹 Job Rotation & Mandatory Vacations
Medidas que detectan actividad sospechosa cuando el empleado no está.

Ejemplo:
- Un empleado malicioso no puede seguir cubriendo sus huellas si se va de vacaciones obligatorias.

---

# 🟦 4. TIPOS DE CUENTAS EN IAM

## 🔸 User Accounts (Cuentas normales)
Para empleados regulares.

## 🔸 Privileged Accounts (Administradores)
Acceso elevado → más riesgo → más control.

## 🔸 Service Accounts
Cuentas usadas por aplicaciones o servicios, NO por humanos.

Ejemplo:
- Cuenta usada por un servidor para conectarse a una base de datos.

## 🔸 Shared Accounts (No recomendadas)
Malas para auditoría.

---

# 🟦 5. AUTENTICACIÓN MODERNA: SSO, Federation y Directory Services

## 🔹 SSO — Single Sign-On
Un solo login → acceso a múltiples aplicaciones.

Ejemplo:
- Entrar a Gmail y acceder a Drive, Docs, etc.

Ventajas:
- cómodo  
- reduce contraseñas  
- mejora seguridad  

---

## 🔹 Federation (Federación)
Permite que identidades de un sistema se usen en otro distinto.

Ejemplo:
- Iniciar sesión en un sitio usando la cuenta de Google.  

Protocolo: **SAML** (muy preguntado en Security+).

---

## 🔹 Active Directory / LDAP
Los directorios empresariales donde viven los usuarios y permisos.

AD = dominante en empresas Windows.

LDAP = protocolo para leer y autenticar información de directorios.

---

# 🧠 6. Seguridad IAM en SOC (cómo lo usas de verdad)

Un analista SOC revisa:

- inicios de sesión fallidos  
- accesos fuera de horario  
- creación de cuentas admin  
- cambios en permisos  
- abuso de privilegios  
- autenticación desde países inusuales  
- tokens sospechosos  
- actividad MFA extraña  

Esto ya lo has aplicado en:
- impossible travel  
- privilege escalation  
- persistence  
- brute force  

Tu portafolio YA demuestra dominio IAM.

---

# 📝 7. MINI-PRÁCTICA (Estilo Security+)

**1. “Solo dar permisos mínimos necesarios” es:**  
A) Separation of Duties  
B) Least Privilege  
➡️ **B**

---

**2. SSO significa:**  
A) Un usuario → múltiples aplicaciones  
B) Un usuario → un servidor  
➡️ **A**

---

**3. SAML se usa para:**  
A) Hashing  
B) Federation / SSO  
➡️ **B**

---

**4. Las cuentas de servicio son usadas por:**  
A) Personas  
B) Aplicaciones  
➡️ **B**

---

# ⭐ 8. RESUMEN FINAL (para memorizar)
- IAM = identidad, autenticación, autorización, auditoría  
- Least Privilege = mínimo permiso necesario  
- SSO = un login para muchas apps  
- SAML = federación/SSO en empresas  
- AD/LDAP = sistemas de gestión de identidades  
- Separation of Duties = evitar abuso  
- Service Accounts = usadas por sistemas, no personas  

