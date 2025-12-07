# 🔐 Security+ — Día 25  
# Access Control Models: RBAC, ABAC, MAC, DAC + Permissions & Policies

## 🎯 Objetivo
Dominar los modelos de control de acceso utilizados en empresas modernas y cómo se asignan permisos de manera segura. Este tema aparece MUCHO en Security+ y es muy común en entrevistas SOC y de seguridad.

---

# 🟥 1. Principios Fundamentales de Control de Acceso

## 🔸 Least Privilege (Principio del mínimo privilegio)
Los usuarios deben tener solo los permisos estrictamente necesarios.

## 🔸 Separation of Duties
No se permite que una misma persona complete un proceso crítico sin supervisión.  
Ejemplo:
- una persona genera pagos  
- otra los aprueba  

## 🔸 Job Rotation
Mejora seguridad y reduce fraude.

## 🔸 Mandatory Vacations
Obliga a ausentarse para detectar fraude o actividades ocultas.

---

# 🟦 2. DAC — Discretionary Access Control

- El **dueño del recurso** controla quién tiene acceso.  
- Modelo más flexible pero menos seguro.  
- Usado en:
  - sistemas Windows tradicionales  
  - sistemas UNIX/ Linux  

DAC = control basado en propiedad.

---

# 🟧 3. MAC — Mandatory Access Control

- El acceso NO depende del dueño.  
- El sistema asigna etiquetas de seguridad.  
- Usado en:
  - gobiernos  
  - militares  
  - entornos extremadamente controlados  

Ejemplo:
- Top Secret  
- Secret  
- Confidential  

MAC = modelo más estricto.

---

# 🟫 4. RBAC — Role-Based Access Control (El más usado)

Permisos basados en **roles**, no en usuarios individuales.

Ejemplos:
- Rol “Analyst” → leer logs  
- Rol “Admin” → configurar sistemas  
- Rol “HR” → ver datos de empleados  

Ventajas:
- muy fácil de administrar  
- escalable  
- se integra con IAM moderno  

RBAC es el modelo favorito de Security+ y el más usado en empresas.

---

# 🟩 5. ABAC — Attribute-Based Access Control (Modelo moderno)

Acceso basado en **atributos** del usuario, dispositivo o entorno.

Ejemplos de atributos:
- usuario: cargo, departamento, certificaciones  
- dispositivo: compliant, parcheado  
- contexto: ubicación, hora del día  
- recurso: tipo, sensibilidad  

Ejemplo típico:
> *Permitir acceso si el usuario es del departamento de Finanzas, usando un dispositivo corporativo, desde EE.UU., entre 7 am – 7 pm.*

ABAC = parte fundamental de Zero Trust.

---

# 🟪 6. Rule-Based Access Control

Acceso basado en reglas dinámicas.

Ejemplo:
- bloquear tráfico fuera del horario laboral  
- permitir acceso a ciertos sistemas solo desde VPN  

Muy usado en firewalls.

---

# 🟨 7. Permission Types

## 🔸 ACL — Access Control List
Lista que especifica qué usuarios o grupos pueden:
- leer  
- escribir  
- ejecutar  
- borrar  

## 🔸 File System Permissions
Ej. Linux:
- r (read)  
- w (write)  
- x (execute)  

Ej. Windows:
- Full Control  
- Modify  
- Read  
- Execute  

---

# 🟦 8. Policies (políticas de seguridad)

### ✔ Privilege Access Management (PAM)
Control estricto de privilegios administrativos.

### ✔ Acceptable Use Policy (AUP)
Reglas para uso de la tecnología corporativa.

### ✔ Mandatory Access Policy
Define reglas obligatorias del sistema.

### ✔ Account Policies
Incluye:
- contraseñas  
- expiración  
- bloqueo por intentos  

---

# 🟥 9. Qué mira SOC sobre Access Control

SOC analiza alertas relacionadas con:
- escalamiento de privilegios  
- acceso fuera de horario  
- permisos que cambian de forma sospechosa  
- usuarios que acceden a recursos no autorizados  
- exceso de permisos (toxic privileges)  
- cuentas huérfanas (sin dueño)  

IAM mal configurado = una de las mayores causas de breaches.

---

# 📝 10. Mini-Práctica Security+

**1. ¿Qué modelo es el más usado en empresas?**  
➡️ RBAC

**2. ¿Qué modelo usa etiquetas como “Secret” o “Top Secret”?**  
➡️ MAC

**3. ¿Qué modelo usa atributos como hora del día o ubicación?**  
➡️ ABAC

**4. ¿Qué principio dice “solo lo mínimo necesario”?**  
➡️ Least Privilege

**5. ¿Qué política previene fraude interno?**  
➡️ Separation of Duties

---

# ⭐ Resumen Final
- DAC = dueño controla  
- MAC = sistema controla  
- RBAC = roles (más usado)  
- ABAC = atributos (moderno, Zero Trust)  
- Control de acceso correcto es clave para seguridad  
