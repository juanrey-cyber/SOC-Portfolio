# 🔐 Security+ — Día 46  
# Web Security Essentials (XSS, CSRF, SQL Injection, SSRF) explicado fácil para SOC/Threat Hunting

## 🎯 Objetivo
Aprender las vulnerabilidades web más importantes, cómo funcionan, cómo se detectan en logs y cómo se responden desde un SOC.  
Esto aparece constantemente en entrevistas y tareas prácticas.

---

# 🟥 1. SQL Injection (SQLi)

SQLi ocurre cuando un atacante inserta comandos SQL en campos de entrada (formularios, URLs, parámetros).

Ejemplo clásico de payload:
' OR '1'='1

Si la app no valida bien, el atacante puede:
- entrar sin contraseña  
- leer datos  
- modificar registros  
- borrar información  

### Señales en logs (para SOC):
- caracteres especiales inesperados en parámetros  
- patrones como OR 1=1  
- errores SQL visibles  
- picos de errores 500 o 403  

### Mitigación:
- sanitización  
- prepared statements  
- firewall de aplicaciones (WAF)  

---

# 🟧 2. Cross-Site Scripting (XSS)

El atacante inyecta JavaScript malicioso en una página.

Tipos:
- Stored XSS (queda guardado en base de datos)  
- Reflected XSS (viaja en la URL)  

Ejemplo de payload:
<script>alert('XSS')</script>

¿Qué logra un atacante?
- robar cookies  
- secuestrar sesiones  
- redirigir a sitios falsos  
- cambiar contenido  

### Señales en logs:
- etiquetas de script  
- strings sospechosas  
- caracteres escapados (%3Cscript%3E)  

### Mitigación:
- escapar caracteres  
- sanitización de input  
- Content Security Policy  

---

# 🟨 3. CSRF (Cross-Site Request Forgery)

CSRF engaña a un usuario autenticado para ejecutar acciones sin darse cuenta.

Ejemplo:
Estás logueado en tu banco → visitas una página maliciosa → esa página envía una petición para transferir dinero “a tu nombre”.

La acción ocurre porque:
- tu cookie está activa  
- el servidor confía en tu sesión  

### Señales en logs:
- solicitudes desde sitios externos sin referer válido  
- acciones sensibles sin token CSRF  
- comportamiento inusual del mismo usuario  

### Mitigación:
- tokens CSRF  
- SameSite cookies  
- verificar origen y referer  

---

# 🟦 4. SSRF (Server-Side Request Forgery)

La vulnerabilidad más peligrosa en cloud.

El atacante hace que el servidor envíe solicitudes hacia:
- recursos internos  
- metadatos cloud  
- endpoints privados  

Ejemplo de abuso en cloud:
Llamar al endpoint de metadatos de AWS:
http://169.254.169.254/latest/meta-data/iam/security-credentials/

Esto permite robar credenciales IAM.

### Señales en logs:
- solicitudes hacia direcciones internas  
- tráfico a IPs reservadas (169.254.x.x)  
- consultas inesperadas desde backend  

### Mitigación:
- bloquear salida (egress filtering)  
- listas blancas estrictas  
- sanitizar URLs  

---

# 🟪 5. Detecciones SOC reales en ataques web

### 🔥 SQLi:
- parámetros largos o con patrones sospechosos  
- errores del tipo “syntax error near…”  
- repetición rápida de payloads  

### 🔥 XSS:
- cadenas que incluyen script o onerror  
- caracteres codificados típicos de XSS  

### 🔥 CSRF:
- falta de token  
- peticiones POST desde dominios externos  

### 🔥 SSRF:
- solicitudes internas inesperadas  
- intentos de acceder a 169.254.169.254  

---

# 🟫 6. Preguntas de entrevista (respuestas cortas)

¿Qué es SQLi?
→ Inyección de comandos SQL para manipular la base de datos.

¿Qué es XSS?
→ Inyección de JavaScript que afecta al usuario.

¿Qué es CSRF?
→ Engañar a un usuario autenticado para ejecutar acciones sin querer.

¿Qué es SSRF?
→ Hacer que el servidor ataque otros recursos internos.

¿Cuál es la más peligrosa en cloud?
→ SSRF, porque puede exponer credenciales IAM.

---

# ⭐ Resumen del Día 46
Aprendiste:
- SQLi, XSS, CSRF y SSRF explicados de forma clara  
- cómo los ven analistas SOC en logs  
- cómo se detectan patrones sospechosos  
- cómo se mitigan  
- respuestas directas de entrevista  
