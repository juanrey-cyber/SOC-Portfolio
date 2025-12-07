# 🔐 Security+ — Día 23  
# Governance, Compliance & Security Frameworks (NIST, ISO, CIS, PCI, HIPAA)

## 🎯 Objetivo
Aprender los marcos, regulaciones y estándares más importantes en ciberseguridad. Esto aparece MUCHO en Security+, entrevistas SOC y roles donde se requiere entender cumplimiento y auditorías.

---

# 🟥 1. ¿Qué es Governance?
Son las **políticas, estándares y procesos** que guían cómo una organización maneja la seguridad.

Incluye:
- políticas de seguridad  
- roles y responsabilidades  
- controles  
- auditorías internas  
- cumplimiento legal  

---

# 🟦 2. Frameworks — Qué son y para qué sirven
Los frameworks son guías estructuradas para implementar controles de seguridad.

Se dividen en:

### ✔ Frameworks de control  
Dicen *qué controles* implementar  
Ej: NIST 800-53, CIS Controls

### ✔ Frameworks de gestión de riesgo  
Dicen *cómo gestionar riesgos*  
Ej: NIST RMF, ISO 27005

### ✔ Frameworks de ciberseguridad  
Dicen *cómo proteger y responder a amenazas*  
Ej: NIST CSF

### ✔ Frameworks regulatorios  
Obligatorios por ley  
Ej: HIPAA, PCI-DSS

---

# 🟩 3. NIST (National Institute of Standards and Technology)

## 🔸 NIST 800-53
Framework de **controles** de seguridad.  
Usado por el gobierno y muchas empresas privadas.

Incluye controles como:
- acceso  
- auditoría  
- autenticación  
- continuidad  
- configuraciones  

---

## 🔸 NIST CSF (Cybersecurity Framework)
MUY popular y muy importante.

Consta de 5 funciones:

1. **Identify**  
2. **Protect**  
3. **Detect**  
4. **Respond**  
5. **Recover**

Este modelo es ORO para entrevistas SOC.

---

## 🔸 NIST RMF (Risk Management Framework)
Procesos para gestionar riesgos:
- categorización  
- selección de controles  
- implementación  
- monitoreo continuo  

---

# 🟧 4. ISO 27001 (estándar internacional de seguridad)

ISO 27001 = norma para crear un **ISMS (Information Security Management System)**.

Incluye:
- políticas  
- controles  
- monitoreo  
- auditorías  
- gestión de riesgos  

Muchas empresas fuera de EE.UU. se basan en este estándar.

---

# 🟫 5. CIS Controls (Center for Internet Security)

Lista priorizada de **20 controles críticos**.

Ejemplos:
- inventario de hardware/software  
- gestión de vulnerabilidades  
- configuración segura  
- monitoreo  
- control de accesos  

SOC usa CIS Controls en detecciones y recomendaciones.

---

# 🟪 6. PCI-DSS (Payment Card Industry Data Security Standard)

Regulación obligatoria para empresas que manejan tarjetas de crédito.

Incluye:
- cifrado  
- segmentación  
- monitoreo  
- políticas estrictas  
- pruebas de penetración  

Multas altas si no cumplen.

---

# 🟨 7. HIPAA (salud — EE.UU.)

Protege datos médicos (PHI).  
Requiere:

- controles de acceso  
- auditoría  
- protección de datos  
- entrenamiento de personal  
- notificación de brechas  

Preguntas típicas:
**“¿Qué regulación aplica para información médica?” → HIPAA.**

---

# 🟦 8. GDPR (Europa)

Regulación europea de privacidad.

Principios clave:
- consentimiento  
- derecho al olvido  
- protección de datos personales  
- notificación de brechas  
- fines legítimos  

Multas de hasta 4% del revenue anual.

---

# 🟥 9. SOX (Sarbanes-Oxley)

Regula empresas públicas en EE.UU.  
Asegura integridad financiera y controles TI.

---

# 🟩 10. SOC 2 (Service Organization Controls)

Define controles para empresas de tecnología (SaaS).

5 pilares:
1. Seguridad  
2. Disponibilidad  
3. Integridad de procesamiento  
4. Confidencialidad  
5. Privacidad  

MUY usado en empresas cloud.

---

# 🧭 11. ¿Qué le importa al SOC sobre Governance & Compliance?

SOC debe:
- monitorear controles  
- detectar incumplimientos  
- revisar logs de auditoría  
- apoyar incidentes regulatorios  
- asegurar retención de logs  
- cumplir tiempos de respuesta (SLAs)  

Ejemplo real:
- una brecha que involucra tarjetas → PCI  
- una brecha médica → HIPAA  
- datos UE → GDPR  

---

# 📝 12. Mini-Práctica (Security+ Style)

**1. ¿Qué framework usa Identify–Protect–Detect–Respond–Recover?**  
➡️ NIST CSF

**2. ¿Qué regula PCI-DSS?**  
➡️ Pagos con tarjeta

**3. ¿Cuál regula datos médicos en EE.UU.?**  
➡️ HIPAA

**4. ¿Qué estándar define un ISMS?**  
➡️ ISO 27001

**5. ¿Qué controles son priorizados para reducir riesgo rápidamente?**  
➡️ CIS Controls

---

# ⭐ Resumen Final
- NIST = frameworks más usados en EE.UU.  
- ISO 27001 = estándar internacional de gestión de seguridad  
- CIS = controles priorizados  
- PCI-DSS / HIPAA / GDPR = regulaciones obligatorias  
- Conocer esto es crítico para entrevistas y Security+  
