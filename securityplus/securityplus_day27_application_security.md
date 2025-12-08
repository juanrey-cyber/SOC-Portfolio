# 🔐 Security+ — Día 27  
# Application Security, OWASP Top 10, Secure Coding & Code Analysis

## 🎯 Objetivo
Entender las vulnerabilidades más comunes en aplicaciones web, cómo explotarlas y cómo defenderlas.  
Este módulo aparece MUCHO en Security+ y también en entrevistas de SOC.

---

# 🟥 1. OWASP Top 10 (versión simplificada para Security+)

OWASP = Open Web Application Security Project  
Organización que publica las vulnerabilidades web más críticas.

Security+ usa la **versión simplificada**, no la más técnica.

---

## 🔸 A1 — Injection (SQL Injection)
Ejemplo:  
`' OR '1'='1` → acceso sin contraseña

**Qué permite:**  
- saltarse login  
- robar datos  
- borrar tablas  

**Mitigación:**  
- Prepared statements  
- Parameterized queries  
- Input validation  
- Escapar caracteres

---

## 🔸 A2 — Broken Authentication
Problemas en login:
- tokens inseguros  
- sesiones que no expiran  
- MFA débil  

Mitigación:
- MFA  
- Timeouts de sesión  
- Cookies seguras

---

## 🔸 A3 — Sensitive Data Exposure
Datos mal protegidos:
- sin encriptar  
- TLS ausente  
- hashing débil (MD5, SHA1)

Mitigación:
- TLS 1.2+  
- Hash fuerte (bcrypt, PBKDF2, Argon2)  

---

## 🔸 A4 — XML External Entities (XXE)
Ataques a parsers XML mal configurados.

Mitigación:
- Deshabilitar ENTIDADES externas  
- Bibliotecas modernas

---

## 🔸 A5 — Broken Access Control
Ejemplo:  
Un usuario normal accede a panel de admin.

Mitigación:
- Revisiones de acceso  
- Zero Trust  
- Validación en servidor, no en cliente

---

## 🔸 A6 — Security Misconfiguration
Los más comunes:
- S3 buckets públicos  
- Firewalls mal configurados  
- Directorios con listado público  

Mitigación:
- Hardening  
- Revisiones periódicas  

---

## 🔸 A7 — Cross-Site Scripting (XSS)
Inyección de JavaScript en sitios web.

Tipos:
- Stored  
- Reflected  
- DOM-based  

Mitigación:
- Encoding  
- Input validation  

---

## 🔸 A8 — Insecure Deserialization
Permite:
- RCE (remote code execution)  
- Escalada de privilegios  

Mitigación:
- No deserializar datos no confiables  
- Firmar objetos

---

## 🔸 A9 — Using Components with Known Vulnerabilities
Ejemplo:
- Log4j  
- Versiones antiguas de frameworks  

Mitigación:
- Patching  
- SBOM (Software Bill of Materials)

---

## 🔸 A10 — Insufficient Logging & Monitoring
Problemas:
- Incidentes no detectados  
- Falta de alertas  
- No correlación  

Mitigación:
- SIEM  
- Logging estructurado  
- Alertas críticas

---

# 🟧 2. Secure Coding Practices

## 🔸 Validation (Input / Output)
NUNCA confiar en entrada del usuario.

### Validación correcta:
- lista blanca (*whitelisting*)  
- sanitización de entrada  
- longitud permitida  
- tipos permitidos  

---

## 🔸 Least Privilege App Design
La aplicación debe usar permisos mínimos.

Ejemplo:
- No usar una cuenta root en una app web  
- No dar permisos excesivos en bases de datos

---

## 🔸 Code Signing
Usar certificados para asegurar:
- integridad  
- autenticidad  

Evita ejecutar código alterado.

---

## 🔸 Memory Safety
Errores típicos:
- Buffer overflow  
- Use-after-free  

Mitigaciones:
- Lenguajes seguros (Rust, Go)  
- ASLR  
- DEP  

---

# 🟦 3. Application Testing Methods

## 🔸 Static Analysis (SAST)
Analiza el código SIN ejecutarlo.  
Busca:
- SQLi  
- XSS  
- funciones inseguras  
- hardcoded passwords  

Herramientas:
- SonarQube  

---

## 🔸 Dynamic Analysis (DAST)
Analiza la aplicación MIENTRAS se ejecuta.  
Detecta:
- inyecciones  
- accesos indebidos  
- fallos de sesión  

---

## 🔸 Fuzzing
Envía datos aleatorios buscando crashes o errores.  
Muy útil para descubrir vulnerabilidades desconocidas.

---

## 🟩 4. Hardening de aplicaciones

- Deshabilitar funciones inseguras  
- Parchar frameworks  
- Configurar TLS correctamente  
- No exponer APIs innecesarias  
- Revisar dependencias (SBOM)  
- Revisar permisos de servicio  

---

# 🟨 5. Mini-Práctica tipo Security+

**1. ¿Qué ataque permite inyectar JavaScript en un sitio web?**  
→ XSS

**2. ¿Qué ataque permite manipular consultas a la base de datos?**  
→ SQL Injection

**3. ¿Qué método analiza el código sin ejecutarlo?**  
→ Static Analysis

**4. ¿Qué técnica envía datos aleatorios buscando fallos?**  
→ Fuzzing

**5. ¿Qué vulnerabilidad de OWASP aparece cuando un usuario normal accede a funciones de administrador?**  
→ Broken Access Control

---

# ⭐ Resumen final
Hoy aprendiste:
- OWASP Top 10  
- SQLi, XSS, CSRF  
- Static vs Dynamic analysis  
- Fuzzing  
- Hardening  
- Memory safety  
- Secure coding fundamentals  

Este módulo aparece MUCHO en el examen.

