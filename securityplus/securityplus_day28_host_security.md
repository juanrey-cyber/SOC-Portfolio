# 🔐 Security+ — Día 28  
# Host Security, Endpoint Hardening, EDR, Patch Management, FIM, Baselines

## 🎯 Objetivo
Aprender cómo asegurar computadoras, laptops y servidores a nivel de endpoint. Este módulo aparece en Security+, entrevistas SOC y trabajos reales.

---

# 🟥 1. Endpoint Security Basics

Un **endpoint** es cualquier dispositivo que se conecta a la red:
- laptops  
- desktops  
- servidores  
- móviles

Los endpoints son el blanco más común para ataques.

---

# 🟦 2. Antivirus, NGAV y EDR (diferencias claras)

## 🔸 Antivirus tradicional
- Busca **firmas** de malware conocido  
- No detecta amenazas nuevas  
- NO suficiente para seguridad moderna  

---

## 🔸 NGAV (Next-Gen Antivirus)
Basado en:
- comportamiento  
- machine learning  
- detección sin firmas  
- bloqueo de técnicas comunes  

---

## 🔸 EDR (Endpoint Detection & Response)
El más avanzado.

Incluye:
- monitoreo continuo  
- captura de eventos (procesos, conexiones, archivos)  
- alertas en tiempo real  
- respuesta automatizada  
- hunting en endpoints  

EDR ejemplos:
- CrowdStrike  
- SentinelOne  
- Microsoft Defender for Endpoint

**Preguntas típicas Security+:**  
➡️ “¿Qué solución proporciona visibilidad profunda, respuesta y hunting?” → **EDR**

---

# 🟩 3. Host Firewalls

Filtran tráfico en el endpoint.

Características:
- reglas de entrada/salida  
- perfiles (público, privado, dominio)  
- control granular por aplicación  

Ejemplo real: firewall de Windows.

---

# 🟧 4. Baselines de Configuración (MUY preguntado)

Una **baseline** = configuración estándar segura.

Ejemplo:
- Windows con servicios innecesarios deshabilitados  
- Configuración de contraseñas  
- Políticas de bloqueo  
- Hardening recomendado por CIS

---

## 🔸 CIS Benchmarks
Los estándares más usados para hardening.

CIS = Center for Internet Security.

Ejemplo:
- CIS Benchmark para Windows Server 2019  
- CIS Benchmark para Ubuntu  

Security+:  
➡️ “¿Qué guía se usa para hardening?” → **CIS Benchmarks**

---

# 🟨 5. Patch Management

Actualizar:
- sistema operativo  
- aplicaciones  
- navegadores  
- drivers  

Tipos:
- security patches  
- hotfixes  
- service packs  

Vulnerabilidades sin parchear = una de las causas más comunes de incidentes.

---

# 🟫 6. Application Control  
(Allowlist vs Denylist)

## 🔸 Denylist
Bloqueas programas específicos.

Riesgo: otros programas maliciosos pueden ejecutarse.

---

## 🔸 Allowlist (más seguro)
Solo se permiten aplicaciones aprobadas.

Muy efectivo contra:
- ransomware  
- malware desconocido  

Security+:  
➡️ Allowlist = **control más seguro**.

---

# 🟪 7. FIM — File Integrity Monitoring

Sistema que detecta cambios no autorizados en archivos críticos:
- `/etc/passwd` en Linux  
- `boot.ini`, `system32` en Windows  

Si un archivo crítico cambia → alerta.

Herramientas:
- Tripwire  
- Wazuh FIM  

---

# 🟩 8. Logging del Endpoint

Registros esenciales:
- procesos  
- conexiones  
- cambios de archivo  
- inicios de sesión  
- fallos de autenticación  

Windows Logs clave:
- 4624 (login)  
- 4625 (login fallido)  
- 4688 (nuevo proceso)  

Security+:  
➡️ “¿Qué log detecta un proceso iniciado por malware?” → **Process creation logs (4688)**

---

# 🟦 9. Sandboxing

Ejecutar programas en un entorno aislado.

Usado para:
- analizar malware  
- correr apps sospechosas  
- proteger el sistema real  

---

# 🟩 10. Virtualization Security

Buenas prácticas:
- snapshots  
- no usar VMs para navegar sitios inseguros si contiene datos críticos  
- separar entornos de producción/test  
- no compartir carpetas innecesariamente entre host y VM  

---

# 📝 11. Mini-Práctica tipo Security+

**1. ¿Qué solución permite hunting y respuesta automatizada?**  
→ EDR

**2. ¿Qué es más seguro: allowlist o denylist?**  
→ Allowlist

**3. ¿Qué detecta cambios en archivos críticos?**  
→ FIM

**4. ¿Qué estándar se usa para hardening?**  
→ CIS Benchmarks

**5. ¿Qué log detecta creación de procesos en Windows?**  
→ 4688

---

# ⭐ Resumen final
Hoy aprendiste:
- EDR vs NGAV vs Antivirus  
- Firewalls de host  
- Hardening con CIS Benchmarks  
- Patching  
- Allowlist  
- FIM  
- Logging del endpoint  
- Sandboxing  
- Seguridad de VMs  

Este módulo aparece muchísimo en Security+ y entrevistas SOC.

